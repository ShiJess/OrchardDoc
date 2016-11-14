<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Search-and-indexing/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Managing-widgets/
[003]: http://www.shisujie.com/blog/Managing-widgets


<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/enable_lucene.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/search2.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/indexnsearch.PNG
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/indexcreated.PNG
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/indexupdated.PNG
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/indexcontenttype.PNG
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/searchfield.PNG
[108]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/searchformwidget.PNG
[109]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/searchwidgetfrontend.PNG


[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Search and Indexing][001]

Orchard支持在网站中索引和搜索内容项。索引功能需要启用**Indexing**功能，同时还要一个具体的索引实现功能（例如：Lucene-based是默认内置在Orchard中的）。除了**Indexing**之外，**Search**功能支持通过索引（关键字或Lucene查询语法）来查询内容项，并将匹配的内容列表项返回到前台显示。

你必须启用以下所有模块： **Search**, **Indexing**, 和 **Lucene**.

> 新版中**Indexing**模块还依赖**Jobs Queue**——一个异步处理的模块。

![][101]

由于搜索功能依赖于索引功能，所以启用搜索功能时，会自动启用索引功能。注意：在使用搜索和索引之前，你还必须启用Lucene模块。

![][102]

在索引功能启用之后，在控制面板中，可以看到**设置-Settings**菜单下面会有 **搜索-Search** 和 **索引-Indexes** 两个新菜单。索引器是作为一个后台任务在运行，在默认情况下，一分钟执行一次，你可以在索引界面中更新和重建索引。**Indexes** 界面中还显示文档（内容项）的索引数量， **Search** 界面中显示索引字段。

![][103]

![][104]

![][105]

在启用**Search**功能后，点击 **内容定义——Content Definition** 菜单，然后点击你想要索引的内容类型，并勾选上可索引勾选框。如，内容类型——Page：

![][106]

当搜索功能启用后，在 **设置-Settings** 下的**搜索** 界面中会显示哪些字段可以通过索引查询。 

![][107]

现在在网站前台界面还没有搜索交互界面。要添加搜索交互，你需要添加一个部件。在控制面板中，点击**部件**。在默认的层上，在项添加搜索框的区域后点击**添加-Add**，然后选择可用部件列表中的 **SearchForm** 。

选择 "Header" 区域和"Default" 层可以保证搜索部件始终显示在所有界面的最上面（default层在网站的每一个界面都会显示）。

输入标题，如 "Search" 并点击**保存-Save** 按钮。

> 关于更多部件内容，见：[原文：Managing widgets][002]、[译文：Orchard入门——部件管理][003]。

现在打开前台界面就可以看到搜索框了。

> 注：个人之前使用TheBootstrapTheme时，由于其已经存在搜索框，添加到Header位置不生效（其他位置可以），故建议测试时，切换为默认主题查看。

![][108]

当在输入框中输入关键字或查询条件后，符合条件的内容列表将会显示在界面上：

![][109]


***
译：[奇葩史][000]