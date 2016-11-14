<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Navigation-and-menus/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Attachments/Navigation-and-menus/AddNewContentItemLink.png
[102]: http://docs.orchardproject.net/en/latest/Attachments/Navigation-and-menus/CreateMenuItem.png
[103]: http://docs.orchardproject.net/en/latest/Attachments/Navigation-and-menus/SelectAContentItem.png
[104]: http://docs.orchardproject.net/en/latest/Attachments/Navigation-and-menus/CreatePageAndNavigation.png
[105]: http://docs.orchardproject.net/en/latest/Attachments/Navigation-and-menus/NotIndentedMenu.png
[106]: http://docs.orchardproject.net/en/latest/Attachments/Navigation-and-menus/IndentedMenu.png
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/manage_menu_675.png

[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Navigation and Menus][001]

*文章内容基于Orchard1.8版本。同时包含Orchard 1.5之前版本的导航参考*

Orchard有许多不同的方法来创建菜单。本文将介绍两种较为常用的方法：

* 先添加菜单项，然后添加内容关联
* 先创建内容，然后选择导航菜单

当然，这些方法不是只能选一种，你可以在同一个网站上组合使用它们。

# 先添加菜单项，然后添加内容关联
这种方式是你查看管理所有菜单项的首选。

在控制面板中点击 **Navigation** 菜单项，你将看到一个默认可用的菜单——'Main Menu'。页面右侧包含所有可以添加到菜单中的类型：

* 内容项类型菜单*Content Menu Item*
* 自定义链接*Custom Link*
* 自定义Html菜单项*Html Menu Item*
* 查询链接*Query Link*
* 形状链接*Shape Link*
* 分类链接*Taxonomy Link*

点击**Content Menu Item**后的 **Add** 添加一个新菜单项。

![][101]

在 '创建菜单项*Create Menu Item*' 页面填写菜单文本。
点击 **Browse** ,然后选择要链接的任何内容(如：你的首页)。 当你真正准备好你的内容后，你也可以修改你的菜单链接项。 

![][102]

![][103]

# 先创建内容，然后选择导航菜单

下面我们首先创建一个新页面（或修改一个页面）。 点击控制面板左侧菜单中的 **New Page** 。创建一个 *About Us* 页面，输入标题及内容。
勾选页面底部的 **Show on a menu** 并为页面选择菜单, **Menu text** 是菜单的显示名称。默认情况下，页面链接将会被添加到**Main Menu**。

![][104]

点击**现在发布Publish Now**页面后，点击控制面板左侧 **Navigation** 菜单项。新的菜单将已被添加到主菜单。

# 创建子菜单

创建子菜单非常容易:
点击 **Navigation** 部分。将鼠标悬停在已添加的菜单项上，你就可以拖动菜单项。
将菜单稍微向右拖动一点，出现子容器后即可。注意：这里所做的修改，在点击页面右下方的 **Save All** 之前都不会生效。

![][105]

![][106]


# 旧版本Orchard操作(1.5之前的版本)
旧版本的Orchard菜单管理差别很大。
1.5之前的Orchard版本的菜单管理很简单，只有菜单文本和链接列表——同样通过控制面板 **Navigation** 打开。当你在页面编辑界面或博文编辑页面添加一个菜单后，菜单列表中就创建一个新项。你可以通过此界面重命名、排序和移除菜单项。（不会删除页面或博文内容，仅仅删除菜单项）。

![][107]

你也可以给菜单添加任意的Url链接，包括站外链接或你Orchard网站的链接。注意：只有在此界面添加菜单才可以修改Url链接。
内容项的菜单链接必须在内容编辑页面修改。

通过在 "Position" 文本框中输入数字索引来修改菜单顺序。其中支持的数字索引格式如下:

* **整数 Integer**: 1, 2, 3, etc.
* **浮点数 Decimal**: 1.1, 1.2, 1.3, etc
* **多部分数字组合 Multi-part number**: 1.1.1, 1.2.1, 1.2.2, etc

当你确认修改好后，点击 **Update All** 来更新网站主菜单（即时生效）。


译：[奇葩史][000]