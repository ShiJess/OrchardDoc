<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Creating-custom-content-types/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Basic-Orchard-Concepts/
[003]: http://docs.orchardproject.net/en/latest/Documentation/Creating-a-custom-field-type/
[004]: http://docs.orchardproject.net/en/latest/Documentation/Template-file-syntax-guide/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/ContentTypes_enable.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots/ContentTypes_startcustom.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/ContentTypes_Manage2.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/manage_page_content2.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/edit_content_type_page.png
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots/ContentTypes_createname.png
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/ContentTypes_addfield.png
[108]: http://docs.orchardproject.net/en/latest/Upload/screenshots/ContentTypes_addfieldname.png
[109]: http://docs.orchardproject.net/en/latest/Upload/screenshots/locationfieldsetting.png
[110]: http://docs.orchardproject.net/en/latest/Upload/screenshots/add_field3.png
[111]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/add_part.png
[112]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/content_type_field_settings.png
[113]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/includefieldinsearch.png
[114]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/create_new_event.png
[115]: http://docs.orchardproject.net/en/latest/Upload/screenshots/ContentTypes_newevent.png
[116]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/ContentTypes_adddinner.png
[117]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/manage_content_event.png
[118]: http://docs.orchardproject.net/en/latest/Upload/screenshots/ContentTypes_displayevent.png
[119]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/search_index_event.png
[120]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/ContentTypes_addeventlocation.png
[121]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/ContentTypes_searchresults.png

> 原文链接：[Creating Custom Content Types][001]


尽管Orchard默认提供了Page和Blog Post内容类型，但是，在控制面板中，我们仍然可以很容易的创建自定义的内容类型（或者扩展已有内容类型的定义）。默认情况下，**内容定义**功能模块是启用的——创建自定义内容类型，此功能必须启用。如果没有启用，可以在**模板-功能**界面手动启用它。

![][101]

要创建内容类型，在控制面板中，点击**内容定义**，选择**内容类型**标签。

![][102]

在此界面中，你可以看到系统中可用的内容类型。注意：此处有些类型可以直接在此处创建内容项或查看内容项列表（如Page类型），而其他的则只能在此编辑内容类型定义（如Comments和Widgets，由于它们有专门的/定制的管理界面来创建和列举内容项）。

![由于官网图片名称大小写有误，无法显示，此处修改][103]

点击Page类型里的**项目列表**可以查看网站的Page类型内容项列表——界面类似**管理内容**界面。

![][104]

你也可以点击Page类型的编辑链接来修改Page类型的定义。

![][105]

Orchard中的内容类型由字段和元件组成，关于那些基本概念的概述见：[原文：Basic Orchard Concepts][002]。字段是类型中的一些定制内容，如：Product类型可能会需要SKU和Price字段。元件则用于可以在一个或多个类型中重复使用的部分。例如：Autoroute元件为类型提供使用链接地址访问内容的功能。 从某种意义上讲，你可以将类型理解为 **含有**字段的，并由一个或多个部件组成的一个东西。事实上，反应到代码层面也是一样。 如果你需要处理博文为Autoroute部件并访问其Slug属性，你可能需要写如下代码：`post.As<AutoroutePart>.Slug` 。幸运的是，你现在不必编写代码来查看处理类型和部件。我们将在下一节通过更详细的例子来介绍这一点。

### 定义一个新的内容类型

下面准备定义一个自定义内容类型。假设你定义一个**Event**类型，用于列举活动（包括地点和日期字段）。首先，点击**内容定义**进入**内容类型**界面，点击**创建新类型**。

输入类型名称 *Event* 。**内容类型Id**字段可以保持使用自动填写的 *Event* 。

![][106]

点击 **添加字段-Add** 添加字段

![][107]

现在Orchard只有一个字段类型（TextField），但在Orchard中还有许多扩展类型（如CheckBoxField, EmailField, TextAreaField, DateTimeField 等），详细内容见：[原文：Creating-a-custom-field-type][003]。同时在模块里的库中还提供了大量的额外字段类型可供下载。

下面在字段名称中输入 *Location* ，并点击**保存**  

![][108]

![][109]

现在可以看到字段显示在Event类型字段列表中了。

![][110]

重复以上步骤添加字段 *Date* 。

现在给类型添加元件，在Event类型中点击**添加元件**。

然后你可以看到当前版本的Orchard中可用的元件。对于我们的Event类型，我们添加 *Comments* 元件（允许评论event），*Tags* 元件（可以为event打标签），*Autoroute* 元件（可以通过前台url地址访问），*Menu* 元件（可以将event添加到主菜单）以及*PublishLater* 元件（允许event立即发布，稍后发布或保存为草稿）。

另外还要添加 "Common" 元件，那样你的内容项可以显示在内容项列表中。

![][111]

类型、字段和元件都可以有自己的设置。字段和元件的特有的设置由Orchard中的功能来决定。如果我们启用**Indexing**功能，类型设置上会出现**Index this content type for search**的设置，并且在每个字段上会有设置项**Include in the index**。勾选**Event**类型中**Location**字段上的选项，这样讲会允许用户在前台通过location来搜索内容（**Search**功能需要启用）。最后记得点击保存。 

![][112]

![][113]

现在我们已经完成了自定义内容类型的定义。下面我们为其创建内容项。可以在**内容定义-内容类型**界面看到**新建Event**链接。

![][114]

同样，在控制面板的**新建**菜单下也有**Event**类型。点击效果与上面一样（二选一）。

![][115]

我们可以在**Event**类型的编辑页面，看到所有我们定义的字段和元件。其中有**Title**（**AutoroutePart**元件，包含**TitlePart** 和 **Permalink**），有**Location**字段，还有 **Tags** 输入框（**Tags**元件），**显示到主菜单-Show on main menu** 勾选框（**Menu**元件），是否允许评论勾选框（**Comments**元件），以及**现在发布-Publish Now**, **稍后发布-Publish Later** 和 **保存草稿-Save As Draft**（**Publish Later** 元件）。填写完成后下一步发布活动。

![][116]

点击Orchard控制面板中的**内容**，我们可以看到添加的event内容项出现在列表项中。

![][117]

在网站的前台页面中，event正如预期的一样，被添加到了主菜单中，同时所有的字段和元件都得以正确显示。

我们可以自定义event的显示方式，并将其模板化。关于此的更多内容见：[原文：Template File Syntax Guide][004]。

![][118]

下面我们可以测试下新类型的搜索功能。首先保证你在**模块-功能**界面启用了**Indexing**, **Search** 和 **Lucene** 功能。然后访问**搜索索引-Search Index** 页面查看有哪些可用字段有索引。你应该可以在索引字段列表中看到**event-location**字段（如果没有，重建索引即可）。

![][119]

我们可以在**设置**管理界面将字段添加到搜索设置中，以此让搜索功能可以通过查询此字段查找内容。

![][120]

在前台界面输入可以匹配活动地址的关键字。

系统会通过搜索地址字段的索引，然后展示搜索结果。

![][121]

至此本教程结束。

***
译：[奇葩史][000]