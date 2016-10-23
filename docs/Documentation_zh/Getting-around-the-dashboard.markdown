<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Getting-around-the-dashboard/
[002]: http://orchardproject.net
[003]: http://docs.orchardproject.net/en/latest/Documentation/Creating-custom-content-types/
[004]: http://docs.orchardproject.net/en/latest/Documentation/Adding-pages-to-your-site/
[005]: http://docs.orchardproject.net/en/latest/Documentation/content-types/
[006]: http://docs.orchardproject.net/en/latest/Documentation/Adding-a-Blog-to-Your-Site/
[007]: http://docs.orchardproject.net/en/latest/Documentation/Moderating-comments/
[008]: http://docs.orchardproject.net/en/latest/Documentation/Managing-widgets/
[009]: http://docs.orchardproject.net/en/latest/Documentation/Adding-and-Managing-Media-Content/
[010]: http://docs.orchardproject.net/en/latest/Documentation/Navigation-and-Menus/
[011]: http://docs.orchardproject.net/en/latest/Documentation/Organizing-content-with-tags/
[012]: http://docs.orchardproject.net/en/latest/Documentation/Installing-modules-and-themes-from-the-gallery/
[013]: http://docs.orchardproject.net/en/latest/Documentation/Enabling-and-Disabling-Features/
[014]: http://docs.orchardproject.net/en/latest/Documentation/Installing-and-Upgrading-Modules/
[015]: http://docs.orchardproject.net/en/latest/Documentation/Installing-Themes/
[016]: http://docs.orchardproject.net/en/latest/Documentation/Previewing-and-Applying-a-Theme/
[017]: http://docs.orchardproject.net/en/latest/Documentation/Managing-Users-and-Roles/
[018]: http://docs.orchardproject.net/en/latest/Documentation/Modifying-Site-Settings/
[019]: http://www.shisujie.com/blog/Navigation-and-menus
[020]: http://www.shisujie.com/blog/Adding-a-Blog-to-Your-Site


<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Attachments/Getting-around-the-dashboard/Dashboard.png

> 原文链接：[Getting Around the Dashboard][001]

*文章内容基于Orchard 1.8版本*

Orchard控制面板用于管理网站、改变外观、添加内容以及控制Orchard功能可用性。成功登陆网站后，一般情况下，在页面的底端有 **Dashboard** 链接，可以直接打开控制面板。

在控制面板左侧为功能列表，相关的功能会合并在一起，你可以展开查看内部功能，点击具体功能项打开功能内容。同时，列表内容可以通过启用或禁用Orchard功能来控制显示。如：
在 **Blog** 部分，创建博客后它就是一个可折叠项。在 **New** 部分，可以选择创建默认的内容类型或者自定义的内容类型。
在控制面板右侧展示所选功能的设置。下图展示了控制面板的内容。

![][101]

# 控制面板包含的功能设置

下面表格列举了控制面板里的功能以及相关简要介绍。

功能名称       | 描述
-------------       | -----------
控制面板 *Dashboard*       | 包含控制面板以及显示 ("Welcome to Orchard") 页面。此页面内容主要有：<br /> 1. 关于Orchard的帮助链接；<br /> 2. 网站所运行的Orchard版本。<br /> 3. [Orchard][002]提供的相关公告，如Orchard有新版本、相关应用有更新等。
新建 *New*                 | 用于创建在 **Content Definition** 中定义的默认内容类型或自定义的内容类型的新实例。更多内容，详见：[原文：Creating Custom Content Types][003]。
内容 *Content*             | 用于管理已创建的内容实例。如：你可以这里管理你的页面——创建、修改或者删除，以及发布。更多详细内容见：[原文：Adding Pages to Your Site][004]。
内容定义 *Content Definition*  | 用于管理已有的内容类型或者添加自定义的内容类型。详情见：[原文：Content Types][005]。
博客 *Blog*                | 用于添加新的博客到网站，或者添加一篇博文到博客，以及管理你的博客。*注：Orchard支持多博客，此处可以添加多个博客*。更多内容见：[原文：Adding a Blog to Your Site][006]、[译文：Orchard入门——给网站添加新博客][020]。
筛选 *Queries*             | 用于管理筛选器——新增修改删除。筛选器用于后期网站内容列表显示。*注：默认可能不显示，在**Modules**中启用Forms下的Query Element功能即可显示*。
评论 *Comments*            | 在网站允许用户评论的情况下，用于管理用户评论。更多信息见：[原文：Moderating Comments][007]。
分类方法 *Taxonomies*      | 用于管理分类信息。添加后，可以给网站内容进行分类，以此进行分类显示。
部件 *Widgets*             | 用于管理网站界面显示部件。详见：[原文：Managing widgets][008]。
媒体 *Media*               | 用于管理媒体文件夹。详见：[原文：Adding and Managing Media Content][009]。
导航 *Navigation*          | 用于管理主菜单以及自定义添加的菜单。详见：[原文：Navigation and Menus][010]、[译文：Orchard入门——导航与菜单][019]。
标签 *Tags*                | 用于管理网站内容标签。详见：[原文：Organizing Content with Tags][011]。
模块 *Modules*             | 用于管理网站功能模块——下载、安装、管理。详见：<br />[原文：Installing Modules and Themes from the Gallery][012]; <br />[原文：Enabling and Disabling Features][013]; <br />[原文：Installing and Upgrading Modules][014]。
主题 *Themes*              | 用于管理网站主题——下载、应用。详见：<br />[原文：Installing Themes][015]; <br />[原文：Previewing and Applying a Theme][016].
工作流　*Workflows*        | 用于管理工作流。网站可以利用工作流配置系统事件或用户交互来触发一些简单或复杂的任务。
用户 *Users*               | 用于管理用户与角色。详见：[原文：Managing Users and Roles][017]。
报告 *Reports*             | 用于管理及查看Orchard生成的网站报告。*注：默认可能会不显示，在**Modules**中启用Core下的Report功能即可显示*
设置 *Settings*            | 用于配置各种站点设置，包括：网站名称、时区、每页项目数、Gallery地址、用户评论是否必须批准、允许上传的媒体类型以及用户注册设置等等。更多信息见：[原文：Modifying Site Settings][018]。


译：[奇葩史][000]