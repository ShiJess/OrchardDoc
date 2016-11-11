<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/First-steps-into-Orchard/
[002]: http://www.shisujie.com/blog/First-steps-into-Orchard
[003]: http://docs.orchardproject.net/en/latest/Documentation/Frequently-asked-questions/
[004]: http://docs.orchardproject.net/en/latest/Documentation/How-Orchard-works/
[005]: http://docs.orchardproject.net/en/latest/Documentation/Installing-Orchard/
[006]: http://www.shisujie.com/blog/Installing-Orchard
[007]: http://docs.orchardproject.net/en/latest/Documentation/Getting-around-the-dashboard/
[008]: http://www.shisujie.com/blog/Getting-around-the-dashboard
[009]: http://docs.orchardproject.net/en/latest/Documentation/Getting-Started/
[010]: http://www.shisujie.com/blog/Getting-Started
[011]: http://docs.orchardproject.net/en/latest/Documentation/Using-the-command-line-interface/
[012]: http://www.shisujie.com/blog/Using-the-command-line-interface
[013]: http://docs.orchardproject.net/en/latest/Documentation/Previewing-and-applying-a-theme/
[014]: http://docs.orchardproject.net/en/latest/Documentation/Customizing-the-default-theme/
[015]: http://www.shisujie.com/blog/Customizing-the-default-theme
[016]: http://docs.orchardproject.net/en/latest/Documentation/Managing-widgets/
[017]: http://www.shisujie.com/blog/Managing-widgets

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-Installation.png
[102]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-SiteSettings.png
[103]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-BlogPost.png
[104]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-CommandLine.png
[105]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/ThemeZonePreview.png
[106]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-ShapesOutlined.png
[107]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-WidgetLayers.png


> 原文链接：[First Steps into Orchard][001]  
> 译文链接：[Orchard扩展——初步理解Orchard][002]

本文的目标是帮助我们快速了解Orchard。由于Orchard中有太多的概念要理解，所以在深入理解之前，我们有必要对它有个整体的了解。因此，本文开始是以任何web用户都能理解为共同基础，然后在逐步深入的同时，引入相关的专业术语。

当你完成本文的阅读后，你就对Orchard有了足够的理解，以此你可以在处理Orchard（以一个设计者或开发者的身份）时，不会被它的高级架构和术语等搞晕。在本文介绍中，每一个新的术语都是以粗体表示，因此你需要在往下学习前确保你已经理解了遇到的术语。

本文中还包含了许多其他页面的链接 —— 含有相关内容更具体的解释，因此你可以将本文作为出发点。关于一些Orchard一般性的问题，如什么是Orchard，Orchard从何而来，请阅读：[原文：Frequently Asked Questions][003]。而关于更多技术上的内容，请阅读：[原文：How Orchard works][004]。


## Looking at Orchard as...

介绍Orchard基础最好的办法是看用户在访问网站时，能够有什么样的角色。其中包括：普通用户（亦叫读者/访问者/访客——*reader/visitor/guest*），管理员，设计者和开发者。

### 用户

Orchard网站和其他任何**网站**一样 —— 以一个前台页面开始，**用户-user**可以通过首页内的链接访问其他页面。而由于网站涉及不同领域，它的内容也会不一样（可以是静态页面，博客，wiki，电子商务等等）。

### 管理员

**管理员**可以访问网站的以下几个方面：

1. 在安装Orchard时，可以看到安装页面。此步骤将会创建用于存储网站内容和设置的数据库。关于如何安装Orchard，见：[原文：Install-Orchard][005]、[译文：Orchard入门——安装Orchard][006]。

    ![][101]

2. 当前，作为用户，它也可以访问前台页面。
3. 他们可以打开控制面板，可以进行如下两个操作：关于控制面板的内容夹：[原文：Getting Around the Dashboard][007]、[译文：Orchard入门——Orchard控制面板概览][008]。

    1. 配置网站：编辑网站的行为和外观设置（或安装/禁用/升级它们）。关于更多网站配置见：[原文：Building Your First Orchard Site][009]、[译文：Orchard入门——构建你的第一个Orchard网站][010]
    
    ![][102]
    
    2. 编辑网站内容。关于更多网站内容编辑见：[原文：Building Your First Orchard Site][009]、[译文：Orchard入门——构建你的第一个Orchard网站][010]
    
    ![][103]
    
4. 使用命令行：可以通过命令行来管理脚本执行，这样就可以比较容易的处理自动化操作。关于更多命令行内容见：[原文：Using the Command-Line Interface][011]、[译文：Orchard网站管理——使用命令行界面][012]。

    ![][104]

### 设计人员

设计者可以修改网站的外观，如[原文：Previewing and Applying a Theme][013]。他还可以编辑现有主题（如果提供）的设置，或创建一个新的主题。
在网站中，主题是用于控制网站整体的视觉呈现。它有时还叫做皮肤或模板。它将**内容**（用户产生的数据）转化为可以在浏览器中显示的html内容。例如：当你写了一篇博文，主题会定义菜单、标题、主体、评论等显示在什么位置以及如何显示。

设计者会依据需要定制到什么程度来修改主题的部分或所有元素，关于如何自定义主题内容见：[原文：Customizing Themes][014]、[译文：Orchard网站定制——定制主题][015]。而主题中主要有以下类型：

* 定义**布局**和区域的文档：这是网站页面的整体展示（不含有任何具体内容）。例如：它可以定义网站有1、2、3列。而**区域**则是布局内的一个部分，它是准备接收任何内容的一个容器。注意，一个灵活的主题（如Orchard提供的）可以自动隐藏空区域。因此，尽管下图显示了许多区域，但大部分区域不会显示在页面上 —— 由于他们没有被使用。

    ![][105]
    
* **视图——Views**: 具体内容的可视化显示。一个视图界面通常是一个后缀为.CSHTML 或 .ASPX的文件。它为显示特定类型内容提供html代码。因此，一个含有很多内容的页面（菜单、博文、评论等）是由各个相关的单个视图组合后创建出来的。

    ![][106]

* **样式表——Stylesheets**, **Javascript** 和媒体文件：它们用于修改视图显示的视觉定义。它们是一系列文件，如"Site.css", jQuery 或者背景图片，边框和图标。

* **部件-Widget**：一个网页通常含有一个主要内容（如博文），但常常还会在两边有小块的信息，如标签云、最近博文列表，twitter订阅等。更多部件内容见：[原文：Managing Widgets][016]、[译文：Orchard入门——部件管理][017]

* 层和特定区域之间的绑定：**层**就像一组页面的描述。一旦定义，你可以控制每一个内容（或部件）显示在哪里。例如：我们可以为博文定义一个层组，然后在其一边添加一个标签云。

    ![][107]

更高级的主题还可以通过编写代码来进一步定制外观显示。

### 开发人员

**开发人员**对Orchard架构有一个比较完整的了解，并可以扩展它。

Orchard是以模块组织的。每一个模块通过一个高级别的目标实现来为网站提供构建块（又叫附加或外挂）。例如，你可以有以下模块：

* Extension module: Adds some (low-level) features that will benefit the website. Eg: Ability to [search your content](Search-and-indexing) or to [use an external editor to write blog posts (like Live Writer)](Blogging-with-LiveWriter)

* Content module: Adds everything (code and visual) required to view/edit some type of content (like blog posts)

* Widget module: Adds a small visual content that can be displayed on the side of existing content modules (like a Tag cloud next to a blog)

* Element module: Adds a small contained element for use in the Orchard.Layouts module, a core module that lets you design page layouts in the browser.

* Theme module: Changes the look of existing content modules (This is what the designer would typically create)

* All the above: A module can have many extensions, content types, widgets and themes all in one package 

Orchard is designed to be highly extensible; this means that almost anything that you interact with can be extended, replaced or disabled.
Out of the box, Orchard comes with a number of modules to provide a good user/administrator experience; but a designer/developer can change them or [create more](Getting-Started-with-Modules). It is also possible to [share your modules](Packaging-and-sharing-a-module) with the Orchard community and to [install modules](Installing-and-upgrading-modules) developed by others.

Orchard comes with only one theme (called "[The Theme Machine](Anatomy-of-a-theme)"). However, it has enough zones to allow various arrangements. This is important because a site can only have one theme active at a time. This means the theme must be flexible enough to allow pages to have different layouts. If you are not satisfied, you can copy it and add more zones.

[The Orchard Gallery](Gallery-overview) contains a lot more themes and modules ready to install. Make sure to browse it to find out what extra features are available.

## Content
In order to fill your website, Orchard allows you to edit and display content. It comes with the ability to create pages and blog posts out of the box. But it also allows you to define your own content. This is important because you may want to have events or profiles or anything else that isn't supported out of the box. This section explains the various elements that plays into providing that capability.

* **Content:** Data that is typically displayed on the front-end website. I use this term as a generic way of calling anything that is user-generated.


* **[Content Type &amp; Item](Creating-custom-content-types)**: A **content type** is like a dynamic class; it defines a structure of data for a specific type of content. That structure can be changed, even by the administrator. A **content item** is an instance of content type. So, BlogPost can be a content type, and when you write one, that one is a content item.

* **[Content Part](Writing-a-content-part)**: Because many content types share many aspects; these aspects can be created independently and reused in each content type. That's what a content part is. Eg: A blog post can have comments; a photo can also have comments; so, instead of implementing the "comments" feature twice, we can create it as a content part and reuse it for both content types.

* **[Content Field](Creating-a-custom-field-type)**: In the same spirit of reusability, we can have smaller types that must behave in a certain way. Eg: Most content types will need Date, phone number, email address, etc. They aren't simple properties since we can attach some behavior (like validation rules) but they aren't content parts either (too "small").
* **Record**: In order to be able to save a content type/part (in a SQL database), it needs to be "linked" to a record. It is a class with all the properties that should be saved. Eg: A Map part must save its coordinates (Latitude &amp; Longitude), so it will be linked to a record with these two properties; and Orchard will do the rest to load/save it. You will not have to deal with records unless you [develop your own module](Getting-Started-with-Modules). But it is useful to understand this concept in case you encounter it.
* **Record**: In order to be able to save a content type/part (in a database), it needs to be "linked" to a record. It is a class with all the properties that should be saved. Eg: A Map part must save its coordinates (Latitude &amp; Longitude), so it will be linked to a record with these two properties; and Orchard will do the rest to load/save it. You will not have to deal with records unless you [develop your own module](Building-a-hello-world-module). But it is useful to understand this concept in case you encounter it.

Note that a content type can only have one of each kind of content parts. But it can have many fields of the same kind. The reason is in the semantic meaning of these concepts. For example, a blog post can only have one commenting aspect and it can have many dates (creation date, last update date, etc.).

Since Orchard is an [open source project](frequently-asked-questions), feel free to [contribute](Contributing-patches) any feature/module you would like.

## Conclusion
We are going to stop here. At this point, you should have a good understanding of what is Orchard. The next step is to get into a bit more details about modules, themes and the [low-level architecture of Orchard](How-Orchard-works). This would be useful when you start learning [how to extend Orchard](Getting-Started-with-Modules).

***
译：[奇葩史][000]