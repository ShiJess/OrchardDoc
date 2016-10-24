<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Adding-Pages-to-Your-Site/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/create_page.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots/Permalink.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots/ShowOnMainMenu.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots/AddComment.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots/EditorControls.png
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots/save_publish_buttons.png

> 原文链接：[Adding Pages to Your Site][001]

*注：内容为官方文档翻译，本人遇到的page中间是布局，而非官网的body——但此内容可以在内容定义里自行修改（本文不做介绍）*

在创建Orchard网站后，你可以添加页面来承载你的内容。
本文将介绍怎么创建一个新的网页，以及如何使用Orchard中的富文本编辑器添加内容并发布到你的网站。

# 创建新页面

在控制面板中，点击 **Content** 菜单下的 **Create Page**。
 **Create Page** 设置页面将如下显示：

![][101]

点击 **New Page** 菜单后，可以做如下操作：

* 为新页面设置一个标题
* 设置搜索引擎友好的链接地址（永久链接）
* 将新页面设置为网站首页
* 利用富文本编辑器添加内容
* 添加内容标签 
* 控制页面链接是否显示在主菜单上
* 是否允许用户评论页面
* 设置页面的拥有者
* 保存和发布页面至网站

## 固定链接

固定链接是指向页面的永久性链接，并且几乎不受“死链”的影响。
当你输入页面标题后，页面会依据页面标题自动生成一个建议的链接。你可以接受它或者自行修改。——*点击保存后才能看到自动生成的链接地址*

![][102]

## 内容标签

一个内容标签为页面添加一个内容分类。例如：一个关于著名小说作者的页面可能会有如下标签：作者、小说和书籍。
在页面发布后，页面内容下面将会显示页面所属的标签列表。点击一个标签，网站会展示所有具有这个标签的页面列表。

## 显示在主菜单上

如果你想让页面的链接出现在主菜单上，勾选 **Show on main menu** 。
一旦勾选，**Menu text** 录入框会显示出来，然后输入要显示在主菜单上的文本内容即可。

![][103]

## 用户评论

> 页面中评论功能是默认不可用的。启用评论功能步骤：点击`Content Types`菜单，编辑 `Page` 内容类型，添加 `Comments` 部分。

要是用户可以评论页面，勾选 **Allow new comments** 。这样在页面底部会自动添加一个输入框以供用户评论。下图展示已发布的页面的评论输入框：

![][104]

# 使用富文本编辑器

Orchard文本编辑器提供强大的富文本编辑功能，以便更好的为你的页面添加内容。下图展示了编辑器的工具栏，同时提供每一个按钮的提示——与悬停提示一致。

![][105]

下面列举一些不常用的编辑功能：

* **Add Media** ——上传媒体文件，如图片、音频文件、视频文件。
* **Insert/Edit Image**——将图片添加到页面或修改选中图片的尺寸大小
* **Insert/Edit Link**——添加链接到页面
* **Edit HTML Source**——显示HTML源码内容，并提供直接更改。
* **Toggle Fullscreen Mode**——控制编辑器全屏显示或恢复正常大小

# 保存及发布页面

在页面底部，**save** 将页面保存为草稿，**publish now** 立即发布页面到网站，**publish later** 指定时间发布页面

![][106]


译：[奇葩史][000]