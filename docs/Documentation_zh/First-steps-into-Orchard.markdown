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
[018]: http://docs.orchardproject.net/en/latest/Documentation/Search-and-indexing/
[019]: http://www.shisujie.com/blog/Search-and-indexing
[020]: http://docs.orchardproject.net/en/latest/Documentation/Blogging-with-LiveWriter/
[021]: http://www.shisujie.com/blog/Blogging-with-LiveWriter
[022]: http://docs.orchardproject.net/en/latest/Documentation/Getting-Started-with-Modules/
[023]: http://docs.orchardproject.net/en/latest/Documentation/Packaging-and-sharing-a-module/
[024]: http://docs.orchardproject.net/en/latest/Documentation/Installing-and-upgrading-modules/
[025]: http://docs.orchardproject.net/en/latest/Documentation/Gallery-overview
[026]: http://docs.orchardproject.net/en/latest/Documentation/Creating-custom-content-types/
[027]: http://www.shisujie.com/blog/Creating-custom-content-types
[028]: http://docs.orchardproject.net/en/latest/Documentation/Writing-a-content-part/
[029]: http://docs.orchardproject.net/en/latest/Documentation/Creating-a-custom-field-type/
[030]: http://docs.orchardproject.net/en/latest/Documentation/Contributing-patches/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-Installation.png
[102]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-SiteSettings.png
[103]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-BlogPost.png
[104]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-CommandLine.png
[105]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/ThemeZonePreview.png
[106]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-ShapesOutlined.png
[107]: http://docs.orchardproject.net/en/latest/Attachments/First-Steps-Into-Orchard/Orchard-WidgetLayers.png


[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
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

* 扩展模块：为网站添加有用的功能（底层的）。如：添加搜索功能，详见：[原文：Search and Indexing][018]、[译文：Orchard网站内容管理——搜索与索引][019]，或者添加外部编辑器（如Liver Writer）支持，详见：[原文：Blogging with LiveWriter][020]、[译文：Orchard网站内容管理——使用Live Writer写博客][021]。

* 内容模块：为查看/编辑内容的类型（如博文）添加所需要的一切（代码和可视化）

* 部件模块：在内容模块旁边添加小的可视化内容，如在博客边上添加标签云

* 元素模块：在Orchard.Layouts模块中添加小的要包含的元素，这是让你的设计页面显示在浏览器中的核心模块。

* 主题模块：改变已有的内容模块的外观。—— 这是设计师通常需要创建的模块。

* 上面所有的集合：一个模块可以在一个包中含有多个扩展、内容类型、部件和主题。 

Orchard采用了高度可扩展设计 —— 这意味着几乎所有你要交互的事都可以扩展，取代或禁用。
Orchard默认提供一系列的模块，为此可以提供给用户/管理员良好的体验，但是设计者/开发者可以修改他们，或者创建更多，关于如何创建模块见：[原文：Getting Started with Modules][022]。它还允许你共享你的模块到Orchard社区，或者安装有其他人开发的模块。更多内容见：[原文：Packaging and Sharing a Module][023]、[原文：Installing and Upgrading Modules][024]。

Orchard默认只附带一个主题 —— [The Theme Machine]。但是，它含有足够的区域供不同的安排，这非常重要，因为一个网站在一个时间上只能使用一个主题。这就意味着主题必须足够灵活以允许所有的页面使用不同的布局。如果它无法满足你，你可以拷贝它并添加更多区域。

在[Orchard Gallery][025]中，含有大量的主题和模块以供安装。你可以通过浏览它并从中找到额外的可用功能。

## 内容

为了填充你的网站，Orchard允许你编辑和展示内容。在默认安装中，它含有创建页面和博文的功能。但是他也允许你定义自己的内容，这很重要，因为你可能需要创建事件或简介，或任何其他的内容，但在Orchard中是没有默认提供的。本节介绍了提供该功能的各种元素：

* **内容——Content:** 通常是网站前台页面显示的数据。可将它作为调用用户产生的任何东西的通用方式。

* **[内容类型和项目][027] —— [Content Type &amp; Item][026]**: **内容类型**类似于动态类，它用于定义特殊类型内容的数据结构。结构可以被修改，管理员也可以修改结构。**内容项**是内容类型的一个实例。因此，BlogPost是一个内容类型，当你写了一篇博文，那篇博文就是一个内容项。

* **内容块——[Content Part][028]**: 因为内容类型共享许多方面，那些方面可以单独创建，也可以在每种内容类型中重复使用。如：一篇博文可能含有评论，一张照片也可以含有评论，因此，我们可以创建一个评论部分，并在两个内容类型中重用，这避免了在实现两次评论功能。

* **内容字段——[Content Field][029]**: 与内容块一样，为了可以重复使用，我们可能需要创建更小型的类型来处理必须要以某些方式表现的内容。例如：大部分内容类型包含日期、电话号码、电子邮件地址等。他们不是简单的属性，因为我们可以附加一些行为（如验证规则）；他们也不是内容块，因为他们太“小”。

* **记录——Record**: 为了可以保存一个内容类型/部分（保存到SQL数据库）,它需要关联到一条记录。它是一个类，且它的所有属性都需要保存。例如：Map部分必须保存它的坐标（纬度和经度），因此他会关联到一条含有两个属性的记录，然后Orchard会完成加载和保存的操作。你不许要自己处理记录，除非你开发自己的模块，但是在你遇到它时，理解本概念是有帮助的。关于更多开发模块见：[原文：Getting Started with Modules][022]。

注意，在每个内容类型中，每个内容块最多只能有一个。但是在同一类型中含有多个字段。原因在于这些概念的语义含义。例如：一篇博文中只能有一个评论部分，但它可以有很多日期（创建日期、最后更新日期等）。

由于Orchard是开源项目，你可以自由贡献你想要的功能或模块。更多内容见：[原文：Frequently Asked Questions][003]、[原文：Contributing Patches][030]。

## 结语

至此，你应该对Orchard有一个比较好的理解。下一步将会更多的讨论模块、主题以及Orchard的底层架构。这在进行扩展开发之前是比较有用的。

***
译：[奇葩史][000]