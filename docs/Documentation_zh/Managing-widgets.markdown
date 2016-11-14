<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Managing-widgets/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Customizing-the-default-theme/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/widgets_manage_1_675.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/widgets_choosewidget_675.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/widgets_AddLayer_1_675.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/widgets_AddZone_1_675.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/widgets_Delete_1_675.png

[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Managing Widgets][001] 

在Orchard中，部件是可以加入到当前当前主题任何位置或区域（如侧栏*sidebar*或底部区域*footer*）的UI块（如：HTML）或代码部分（如：内容部分）。常见部件示例包括：导航菜单*navigation menus*, 图片库*image galleries*, 广告*ads*, 视频*videos*, 以及标记云图*tag clouds*

本文介绍部件的基础知识，以及如何管理部件。

# 层*Layers*, 区域*Zones*, 和部件*Widgets*

在Orchard控制面板中，点击 **部件*Widgets*** 菜单进入部件管理界面。**Widgets** 界面列出了可用的部件列表，以及可以添加部件的层_layer_和区域_zone_。 

你可以将层 _layer_ 理解为展示一个部件（或一组部件）的一系列规则。例如：一个层可以控制页面上某一部件只对登录用户可见。区域_zone_控制部件显示在页面的哪一个位置。 

下图为**部件*Widgets*** 页面：

![][101]

## 可用的部件

一旦部件设置可用 (通常是在**控制面板-模块-功能**下面启用了一个功能后引起), Orchard会自动将部件添加到当前主题区域可用部件列表当中。要查看区域可用部件列表，点击**部件**界面中区域列表中某一区域后面的**添加**按钮。 

例如：在**部件**界面中点击 **Header** 区域后的**添加**按钮。网站将展示可以添加到区域的可用部件列表。

![][102]

下面表格描述了Orchard中默认可用的部件： 

部件*Widget*                | 描述*Description*
--------------------- | ------------------------------------------------------------------
**Blog Archives**     | 显示指定博客的博文条目列表
**Container Widget**  | 显示内容项容器，例如一个列表
**Html Widget**       | 显示HTML内容——需要通过部件编辑器添加内容
**Recent Blog Posts** | 显示指定博客的最近更新博文

## 层的列表

Orchard内置提供了一些层。你也可以按照自己的需要定义层，稍后将详述**[添加层](#AddingaLayer)**。在**部件**页面，你可以通过**当前层**下拉菜单改变当前编辑的层，也可以点击**添加一个新层来**来添加新层。

下面列表列举了默认层的显示规则，以及层的作用。

层*Layer*          | 规则*Rule*              | 描述*Description*
-------------- | ----------------- | ---------------------------------------
Default        | true              | 在所有页面都显示
Authenticated  | authenticated     | 用户已认证——即对登录用户可见
Anonymous      | not authenticated | 匿名用户可见
Disabled       | false             | 不显示。可用于保存当前不需要显示的部件配置
TheHomepage    | url("~/")         | 首页显示

## 区域列表

Orchard中，网页被分成许多个区域。可用区域被定义在网站主题之中。在**部件**界面，你可以看到当前选中层所有可用区域的列表。界面上也包含当前选中层的每个区域包含的部件。

关于更多默认主题(TheThemeMachine)的可用区域信息，参见：[原文：Customizing the Default Theme][002]。

<!--此处需要内部锚点，故使用html格式写-->
<h2 id='AddingaLayer'>添加层</h2>

点击**控制面板-部件-添加一个新层**来添加一个层，下图为 **Add Layer** 界面：

![][103]

添加新层信息：层名称、描述，以及层规则，完成后点击**保存**。

**层规则**的值是一个可以解析为**true** 或 **false**的表达式。如果解析为 **true**, 则部件显示，否则部件不显示。

下表简述了建立层的语法规则：

语法规则*Rule Syntax*                  | 描述*Description*
---------------------------- | ------------------------------
url("&lt;url&nbsp;path&gt;") | 当当前url地址符合指定的路径，则为true。如果在路径最后加了星号（\*），所有此路径下的子链都被认为是true（如：`url("~/home*")`）。
authenticated                | 用户已登录则为true。
ContentType("&lt;Type&gt;")  | 浏览内容类型与特定的类型匹配，则为true。如：内容类型（“Page”）
not                          | 逻辑非
and                          | 逻辑与
or                           | 逻辑或

表达式可以使用括号。

例如，下面表达式定义的规则表示对于未登录用户可以在**About**页面查看到部件，登录用户在任何页面都可以看到部件。
    

    (not authenticated and url("~/about")) or authenticated


如 允许多个url值，可以使用如下语法：

    
    url("~/foo") or url("~/bar")


# 为区域添加部件

点击要添加部件的区域后的**添加**按钮，然后选择要添加的部件，以此给一个区域添加部件。  

例如：点击**Header**区域后的**添加**按钮，然后在 **Choose A Widget** 页面点击 **Html Widget**。然后网站将展示 **Add A Widget** 页面

![][104]

要配置哪些字段取决于你配置的部件类型。所有部件都包含**区域*Zone***, **层*Layer***, **标题*Title***, 和 **位置*Position*** 字段。**位置**字段确认区域内部所有部件的相对位置（事实上就是z-order）。需要注意的是区域内的部件可以来自多个层。例如：两个完全不同的层中可能在统一区域都含有部件。

**位置**字段可以是整数，也可以是由点分隔的整数序列。例如：以下值都是有效的：5, 10.1, 7.5.3.1。位置值小的部件将显示在位置值大的部件之前。

设置完所有字段后，点击**保存**。

# 编辑或删除部件

要编辑或删除部件，在**部件**页面的**当前层**下拉框中选择部件所在的层。然后在层所含的区域列表中，点击要更改的部件。之后会自动进入**编辑部件**界面：

![][105]

编辑你想修改的字段，然后点击**保存**。要从区域中移除部件，点击后面的**移除**按钮。
  
***
译：[奇葩史][000]