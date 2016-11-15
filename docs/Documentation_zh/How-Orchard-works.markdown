<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/How-Orchard-works/
[002]: http://www.shisujie.com/blog/How-Orchard-works
[003]: http://www.asp.net/mvc
[004]: http://www.nhforge.org/
[005]: https://autofac.org/
[006]: https://en.wikipedia.org/wiki/Inversion_of_control
[007]: http://www.castleproject.org/projects/dynamicproxy/
[008]: https://zh.wikipedia.org/wiki/多租户技术


[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[How Orchard Works][001]  
> 译文链接：[Orchard扩展——Orchard的工作原理][002]  
> 本文为纯文字内容，稍显枯燥，不过若能全篇理一遍，对Orchard的整体架构技术可以有个比较好的了解。  
> 另，本文有些内容个人看的时候还是一头雾水，有些地方翻译会比较晦涩。


构建一个web cms与常规的web应用有所不同，它更像是构建一个应用容器。当设计一个这类系统，我们需要把可扩展性作为首要功能特性。这是一个的挑战，因为开放式的架构会需要有很好的扩展性，但这可能需要降低应用的可用性来满足：系统中所有内容都需要能够和未来未知的模块进行组合，包括在UI层。将所有不互通的小部件组织为一个连贯的整体就是所谓的Orchard。

本文讲述了组成Orchard所做的架构选择，以及它是如何解决在提供灵活性的同时，又保证了良好的用户体验这一问题。

# 网站架构

<table cellspacing="2" cellpadding="2" border="1" style="width:100%">
<tr>
<td colspan="4" align="center">Modules
</tr><tr>
<td colspan="4" align="center">Core
</tr><tr>
<td colspan="4" align="center">Orchard Framework
</tr><tr>
<td align="center" style="width:25%">ASP.NET MVC
<td align="center" style="width:25%">NHibernate
<td align="center" style="width:25%">Autofac
<td align="center" style="width:25%">Castle
</tr><tr>
<td colspan="2" align="center">.NET
<td colspan="2" align="center">ASP.NET
</tr><tr>
<td colspan="4" align="center">IIS or Windows Azure
</tr>
</table>

# Orchard基础

Orchard CMS是建立在现有框架和库之上的。以下是其中最基本的几个：

- [ASP.NET MVC][003]: ASP.NET MVC是一个现代的Web开发框架 —— 它提倡业务分离。
- [NHibernate][004]: NHibernate是一个对象关系映射工具。它用于处理Orchard内容项的持久化数据库存储，并在进行模块开发时，极大简化数据模型，以便于我们无需关注数据的持久化。你可以通过查看任何一个核心内容类型的源代码来查看示例，例如Pages。
- [Autofac][005]: Autofac是一个[IoC][006]容器。Orchard大量使用了依赖注入。通过实现IDependency接口（或继承自IDependency的特定接口——如标记接口）来创建一个可注入的Orchard依赖就项写一个类一样简单；而使用依赖就像使用正确类型的构造参数一样简单。注入的依赖项的使用范围和生命周期则由Orchard框架进行管理。你可以通过查看IAuthorizationService, RolesBasedAuthorizationService 和 XmlRpcHandler的代码来查看示例。
- [Castle Dynamic Proxy][007]: 我们使用Castle来进行动态代理生成。

Orchard应用及框架是在这些基础框架之上建立额外的抽象层。Orchard中有许多方法来实现具体功能内容，且不一定需要知道NHibernate, Castle, 或 Autofac。

# Orchard框架

Orchard框架是Orchard中最低层的东西。它包含了应用程序的引擎以及不能继续拆分为模块的部分。那些东西通常是最基本的模块都要依赖的。你可以把它当作Orchard的基础类库。

## Orchard启动

> 关于本节中“租户（tenant）”一词，网络未找到比较好的解释，仅在维基百科中的多租户技术中提到此词的解释：  
> 租户（tenant）是指使用系统或电脑运算资源的客户。  
> [多租户概念维基百科链接][008] —— **墙外链接**

当Orchard web应用启动时，一个Orchard主机服务将会被创建。其主机服务为一个应用程序域级别的单例。

然后，主机服务会使用ShellContextFactory来为当前租户获取一个Shell。租户是应用程序的实例，它被拆分到了用户操作级别，但是它们还运行在同一个应用程序域 —— 提高网站的密度。Shell在租户级别是一个单例，或者可以说它实际上代表租户。它在租户级别有效的隔离了对象，并且保证了模块的编程模型与多租户无关。

shell一旦创建，将会从ExtensionManager中获取可用扩展列表（即模块和主题）。其默认实现是通过扫描模块和主题目录来获取扩展内容。

与此同时，shell还会从ShellSettingManager中获取有关租户的设置列表。其默认实现是在`App_Data`中对应的子文件夹中获取设置，但是我们可以另外实现来从其它不同的位置获取。例如，我们有一个Azure实现，它用来存储blob数据，因为在那种情况下，`App_Data`可写是不安全的。

之后，shell会获取组策略对象，并使用它依据当前主机服务的可用扩展列表和当前租户的设置来准备IoC容器。在此获得的结果并不是一个shell的IoC容器，它是一个ShellBlueprint —— 依赖、控制器和记录蓝图的一个列表。

至此，ShellSetting（每个租户）的列表和ShellBluePrint将会放入ShellContainerFactory。利用CreateContainer来获取一个ILifetimeScope —— 基本上可以在租户级别范围使用IoC容器，这样模块可以在不需要处理具体事宜的情况下，获取当前租户的作用域中注入的依赖。

## 依赖注入

在Orchard中，标准的创建注入依赖的方式是：先创建一个派生自IDependency（或者是它的派生接口）的接口，然后再实现这个接口。而在使用时，可以在你的构造函数中使用接口类型的参数。Orchard应用框架会发现所有依赖项，然后依据需要进行实例化和注入实例。

Orchard中为注入提供了三个可行的范围，从中选择正确的接口派生即可：

- 请求——Request: 为每个新的http请求创建的依赖实例，且一旦请求完成，实例就会销毁。通过继承接口IDependency来使用。此对象应当相对低代价的创建。
- 对象——Object: 每次对象通过接口获取依赖时，都会创建一个新的实例。且实例从不共享。通过继承接口ITransientDependency来使用。此对象必须很低代价的创建。
- Shell: 每个shell/租户只创建一个实例。它利用ISingletonDependency接口派生。只有需要在shell生存期中必须保持一个共同状态的对象使用此创建。

### 替换现有依赖

可以通过使用OrchardSuppressDependency特性装饰类来实现替换现有依赖。它会将完全限定类型名称替换为一个参数。

### 依赖关系排序

一些依赖项并不唯一，而是列表的一部分。例如，handlers是同时处于活动状态。在某些情况下，你将会需要修改这些依赖的使用顺序。这可以通过修改模块清单来实现 —— 使用功能中优先级（Priority）属性。下面为示例代码：
    
    Features:
        Orchard.Widgets.PageLayerHinting:
            Name: Page Layer Hinting
            Description: ...
            Dependencies: Orchard.Widgets
            Category: Widget
            Priority: -1



## ASP.NET MVC

Orchard是基于ASP.NET MVC建立的，但是为了添加事物，如主题与租户分离，它需要引入一个额外的层，这样，在设想中ASP.NET MVC端将按预期进行控制显示呈现，而在Orchard概念层中的Orchard端拆分事物。

例如，当请求一个特定视图时，我们的LayoutAwareViewEngine将会启动。严格来讲，它并不是一个新的视图引擎，因为它不关心实际的渲染，但是，它包含依据当前主题查找到正确视图的逻辑处理，然后他会将渲染的工作交给实际的视图引擎。

同样，我们还有路由提供程序、模型绑定器和控制器工厂，它们的工作是作为ASP.NET MVC的单一入口点，并将调用分配到下面合理范围的对象。

就以路由为例，我们会有n个路由提供程序（通常来自模块）和一个与ASP.NET MVC交互的路由发布程序。模型绑定器和控制器工厂也是一样的。

## Content Type System

Contents in Orchard are managed under an actual type system that is in some ways richer and more dynamic than the underlying .NET type system, in order to provide the flexibility that is necessary in a Web CMS: types must be composed on the fly at runtime and reflect the concerns of content management.

### Types, Parts, and Fields

Orchard can handle arbitrary content types, including some that are dynamically created by the site administrator in a code-free manner. Those content types are aggregations of content parts that each deal with a particular concern. The reason for that is that many concerns span more than one content type.

For example, a blog post, a product and a video clip might all have a routable address, comments and tags. For that reason, the routable address, comments and tags are each treated in Orchard as a separate content part. This way, the comment management module can be developed only once and apply to arbitrary content types, including those that the author of the commenting module did not know about.

Parts themselves can have properties and content fields. Content fields are also reusable in the same way that parts are: a specific field type will be typically used by several part and content types. The difference between parts and fields resides in the scale at which they operate and in their semantics.

Fields are a finer grain than parts. For example, a field type might describe a phone number or a coordinate, whereas a part would typically describe a whole concern such as commenting or tagging.

But the important difference here is semantics: you want to write a part if it implements an "is a" relationship, and you would write a field if it implements a "has a" relationship.

For example, a shirt **is a** product and it **has a** SKU and a price. You wouldn't say that a shirt has a product or that a shirt is a price or a SKU.

From that you know that the Shirt content type will be made of a Product part, and that the Product part will be made from a Money field named "price" and a String field named SKU.

Another difference is that you have only one part of a given type per content type, which makes sense in light of the "is a" relationship, whereas a part can have any number of fields of a given type. Another way of saying that is that fields on a part are a dictionary of strings to values of the field's type, whereas the content type is a list of part types (without names).

This gives another way of choosing between part and field: if you think people would want more than one instance of your object per content type, it needs to be a field.

### Anatomy of a Content Type

A content type, as we've seen, is built from content parts. Content parts, code-wise, are typically associated with:

- a Record, which is a POCO representation of the part's data
- a model class that is the actual part and that derives from `ContentPart<T>` where T is the record type
- a repository. The repository does not need to be implemented by the module author as Orchard will be able to just use a generic one.
- handlers. Handlers implement IContentHandler and are a set of event handlers such as OnCreated or OnSaved. Basically, they hook onto the content item's lifecycle to perform a number of tasks. They can also participate in the actual composition of the content items from their constructors. There is a Filters collection on the base ContentHandler that enable the handler to add common behavior to the content type.  
For example, Orchard provides a StorageFilter that makes it very easy to declare how persistence of a content part should be handled: just do `Filters.Add(StorageFilter.For(myPartRepository));` and Orchard will take care of persisting to the database the data from myPartRepository.  
Another example of a filter is the ActivatingFilter that is in charge of doing the actual welding of parts onto a type: calling `Filters.Add(new ActivatingFilter<BodyAspect>(BlogPostDriver.ContentType.Name));` adds the body content part to blog posts.
- drivers. Drivers are friendlier, more specialized handlers (and as a consequence less flexible) and are associated with a specific content part type (they derive from `ContentPartDriver<T>` where T is a content part type). Handlers on the other hand do not have to be specific to a content part type. Drivers can be seen as controllers for a specific part. They typically build shapes to be rendered by the theme engine.

## Content Manager
All contents are accessed in Orchard through the ContentManager object, which is how it becomes possible to use contents of a type you don't know in advance.

ContentManager has methods to query the content store, to version contents and to manage their publication status.

## Transactions

Orchard is automatically creating a transaction for each HTTP request. That means that all operations that happen during a request are part of an "ambient" transaction. If code during that request aborts that transaction, all data operations will be rolled back. If the transaction is never explicitly cancelled on the other hand, all operations get committed at the end of the request without an explicit commit.


## Request Lifecycle

In this section, we'll take the example of a request for a specific blog post.

When a request comes in for a specific blog post, the application first looks at the available routes that have been contributed by the various modules and finds the blog module's matching route. The route can then resolve the request to the blog post controller's item action, which will look up the post from the content manager. The action then gets a Page Object Model (POM) from the content manager (by calling BuildDisplay) based on the main object for that request, the post that was retrieved from the content manager.

A blog post has its own controller, but that is not the case for all content types. For example, dynamic content types will be served by the more generic ItemController from the Core Routable part. The Display action of the ItemController does almost the same thing that the blog post controller was doing: it gets the content item from the content manager by slug and then builds the POM from the results.

The layout view engine will then resolve the right view depending on the current theme and using the model's type together with Orchard conventions on view naming.

Within the view, more dynamic shape creation can happen, such as zone definitions.

The actual rendering is done by the theme engine that is going to find the right template or shape method to render each of the shapes it encounters in the POM, in order of appearance and recursively.

## Widgets

Widgets are content types that have the Widget content part and the widget stereotype. Like any other content types, they are composed of parts and fields. That means that they can be edited using the same edition and rendering logic as other content types. They also share the same building blocks, which means that any existing content part can potentially be reused as part of a widget almost for free.

Widgets are added to pages through widget layers. Layers are sets of widgets. They have a name, a rule that determines what pages of the site they should appear on, and a list of widgets and associated zone placement and ordering, and settings.

The rules attached to each of the layers are expressed with IronRuby expressions. Those expressions can use any of the IRuleProvider implementations in the application. Orchard ships with two out of the box implementations: url and authenticated.

## Site Settings

A site in Orchard is a content item, which makes it possible for modules to weld additional parts. This is how modules can contribute site settings.

Site settings are per tenant.

## Event Bus

Orchard and its modules expose extensibility points by creating interfaces for dependencies, implementations of which can then get injected.

Plugging into an extensibility point is done either by implementing its interface, or by implementing an interface that has the same name and the same methods. In other words, Orchard does not require strictly strongly typed interface correspondence, which enables plug-ins to extend an extensibility point without taking a dependency on the assembly where it's defined.

This is just one implementation of the Orchard event bus. When an extensibility point calls into injected implementations, a message gets published on the event bus. One of the objects listening to the event bus dispatches the messages to the methods in classes that derive from an interface appropriately named.

## Commands

Many actions on an Orchard site can be performed from the command line as well as from the admin UI. These commands are exposed by the methods of classes implementing ICommandHandler that are decorated with a CommandName attribute.

The Orchard command line tool discovers available commands at runtime by simulating the web site environment and inspecting the assemblies using reflection. The environment in which the commands run is as close as possible to the actual running site.

## Search and Indexing

Search and indexing are implemented using Lucene by default, although that default implementation could be replaced with another indexing engine.

## Caching

The cache in Orchard relies on the ASP.NET cache, but we expose a helper API that can be used through a dependency of type ICache, by calling the Get method. Get takes a key and a function that can be used to generate the cache entry's value if the cache doesn't already contains the requested entry.

The main advantage of using the Orchard API for caching is that it works per tenant transparently.

## File Systems

The file system in Orchard is abstracted so that storage can be directed to the physical file system or to an alternate storage such as Azure blob storage, depending on the environment. The Media module is an example of a module that uses that abstracted file system.

## Users and Roles

Users in Orchard are content items (albeit not routable ones) which makes it easy for a profile module for example to extend them with additional fields.
Roles are a content part that gets welded onto users.

## Permissions

Every module can expose a set of permissions as well as how those permissions should be granted by default to Orchard's default roles.

## Tasks

Modules can schedule tasks by calling CreateTask on a dependency of type IScheduledTaskManager. The task can then be executed by implementing IScheduledTaskHandler. The Process method can examine the task type name and decide whether to handle it.

Tasks are being run on a separate thread that comes from the ASP.NET thread pool.

## Notifications

Modules can surface messages to the admin UI by getting a dependency on INotifier and calling one of its methods. Multiple notifications can be created as part of any request.

## Localization

Localization of the application and its modules is done by wrapping string resources in a call to the T method: `@T("This string can be localized")`. See [Using the localization helpers](Using-the-localization-helpers) for more details and guidelines. Orchard's resource manager can load localized resource strings from PO files located in specific places in the application.

Content item localization is done through a different mechanism: localized versions of a content item are physically separate content items that are linked together by a special part.

The current culture to use is determined by the culture manager. The default implementation returns the culture that has been configured in site settings, but an alternate implementation could get it from the user profile or from the browser's settings.

## Logging

Logging is done through a dependency of type ILogger. Different implementations can send the log entries to various storage types. Orchard comes with an implementation that uses [Castle.Core.Logging](https://github.com/castleproject/Windsor/blob/master/docs/logging-facility.md) for logging.

# Orchard Core

The Orchard.Core assembly contains a set of modules that are necessary for Orchard to run. Other modules can safely take dependencies on these modules that will always be available.

Examples of core modules are feeds, navigation or routable.

# Modules
The default distribution of Orchard comes with a number of built-in modules such as blogging or pages, but third party modules are being built as well.

A module is just an ASP.NET MVC area with a manifest.txt file that is extending Orchard.

A module typically contains event handlers, content types and their default rendering templates as well as some admin UI.

Modules can be dynamically compiled from source code every time a change is made to their csproj file or to one of the files that the csproj file references. This enables a "notepad" style of development that does no require explicit compilation by the developer or even the use of an IDE such as Visual Studio.

Modules must be placed in the Modules folder (Orchard.Web/Modules/MyModule) and the folder name *must* match the name of the compiled DLL produced by the project.  So, if you have a custom module project called My.Custom.Module.csproj and it compiles to My.Custom.Module.dll, then the module root folder must be named My.Custom.Module. [~/Modules/My.Custom.Module/]

# Themes

It is a basic design principle in Orchard that all the HTML that it produces can be replaced from themes, including markup produced by modules. Conventions define what files must go where in the theme's file hierarchy.

The whole rendering mechanism in Orchard is based on shapes. The theme engine's job is to find the current theme and given that theme determine what the best way to render each shape is. Each shape can have a default rendering that may be defined by a module as a template in the views folder or as a shape method in code. That default rendering may be overridden by the current theme. The theme does that by having its own version of a template for that shape or its own shape method for that shape.

Themes can have a parent, which enables child themes to be specializations or adaptations of a parent theme. Orchard comes with a base theme called the Theme Machine that has been designed to make it easy to use as a parent theme.

Themes can contain code in much the same way modules do: they can have their own csproj file and benefit from dynamic compilation. This enables themes to define shape methods, but also to expose admin UI for any settings they may have.

The selection of the current theme is done by classes implementing IThemeSelector, which return a theme name and a priority for any request. This allows many selectors to contribute to the choice of the theme. Orchard comes with four implementations of IThemeSelector:

- SiteThemeSelector selects the theme that is currently configured for the tenant or site with a low priority.
- AdminThemeSelector takes over and returns the admin theme with a high priority whenever the current URL is an admin URL.
- PreviewThemeSelector overrides the site's current theme with the theme being previewed if the current user is the one that initiated the theme preview.
- SafeModeThemeSelector is the only selector available when the application is in "safe mode", which happens typically during setup. It has a very low priority.

An example of a theme selector might be one that promotes a mobile theme when the user agent is recognized to belong to a mobile device.


***
译：[奇葩史][000]