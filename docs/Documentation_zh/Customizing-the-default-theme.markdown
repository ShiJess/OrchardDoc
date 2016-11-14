<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Customizing-the-default-theme/
[002]: http://tryorchard.net/
[003]: http://docs.orchardproject.net/en/latest/Documentation/Using-the-command-line-interface/
[004]: http://www.shisujie.com/blog/Using-the-command-line-interface

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots/ThemeMachine_structure.PNG
[102]: http://docs.orchardproject.net/en/latest/Attachments/Anatomy-of-a-theme/TheThemeMachineZoneScreenshot.PNG
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots/NewTheme_structure.PNG
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots/NewTheme_thumbnail.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots/themes_available.PNG

[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Customizing Themes][001]

Orchard中的默认主题叫 *The Theme Machine* 。它被设计为多功能的，可以从它来进行定制和开发主题。 

本文将介绍主题 *The Theme Machine* 以及示范如何通过自定义The Theme Machine的样式表（Site.css）来创建自己的主题。

# The Theme Machine主题介绍

The Theme Machine为主题设计提供了灵活且强大的基础。下图是它的文件结构：

![][101]

The Theme Machine中的核心文件是布局页面(Layout.cshtml)和样式表(Site.css)。

# 布局页面概览

布局页面定义多个区域。每个区域都有一个条件语句，所以只有当它含有内容时，他才会呈现出来。如果区域内没有提供内容，显示的页面将不会包含这个区域。下图为布局中的区域：

![All the zones in The Theme Machine][102]

> 注：官方文档此处本有一个示例来展示各个区域部分，但给出的示例链接已经失效，故此处给出官方的Demo网站：[Try Orchard][002]。

关于区域的内容则在控制面板中进行添加。 

# CSS样式概览

The Theme Machine的样式表(Site.css)提供了大量的样式用于更详细的控制网站的外观。样式表中对样式进行了分组，以便于你自定义时更容易地定位样式。下表显示了分组情况以及相应类型样式的描述：

分组-*Grouping*  | 描述-*Description*
--------- | -----------------------------------------------------------------
General   | 包含 body, headings, lists, 和 text elements部分的默认样式。
Forms     | 包含与HTML表单有关的样式，如**form**, **legend**, **fieldset**, **label**, 和 **input**。
Structure | 包含The Theme Machine中页面布局的每个区域的样式定义
Main      | 包含blog posts, comments, tagged search, 和 search results的样式定义
Secondary | 包含aside zones, tripel zones, 和 footer quad zones 部分内的额外布局样式。
Widgets   | 包含选定部件的样式，如 search widget, edit-mode widgets, 和 content mode.
Pager     | 包含与页面形状有关的样式。
Misc      | 包含其他杂项样式，如：small, large, quiet, 和 highlight.

# 创建自主题

你可以通过自定义The Theme Machine来创建自己的样式。但是，你最好不要直接编辑The Theme Machine的文件。取而代之，你应该创建一个子主题，然后将你想要修改的文件拷贝到子主题中。你不必将不准备修改的内容拷贝过来 —— 子主题继承父主题，并且只会覆盖你自定义的内容。当你将子主题作为当前主题时，Orchard首先查找当前主题文件，如果没有找到，然后去查找父级主题（BaseTheme）——甚至你的每一个父主题还可以有自己的父主题，系统会一层一层查。

创建子主题步骤如下：

1. 用command-line CodeGen工具生成子主题代码结构
2. 从The Theme Machine主题中拷贝需要修改的内容到子主题
3. 编辑子主题的文件
4. 应用新主题到网站


## 生成主题结构

要为新主题生成代码结构，我们会用到 **Code Generation** 功能 —— 在控制面板中点击**模块**就可以看到此功能包含在**功能**标签下。一旦启用code generation功能后，就可以在Orchard中用命令行生成新主题了。关于更多命令行的内容见：[原文：Using the command-line interface][003]、[译文：使用命令行界面][004]。

打开Orchard命令行工具，然后输入以下命令 ：
    
    codegen theme MyTheme /BasedOn:TheThemeMachine

如果你要使用Visual Studio来编辑（或你想让你的主题最终含有代码文件），你或许需要指定`CreateProject`和`IncludeInSolution`选项，命令如下：
   
    codegen theme MyTheme /BasedOn:TheThemeMachine /CreateProject:true /IncludeInSolution:true

上述命令告诉Orchard创建新主题的代码结构，并将主题名称设为 _MyTheme_, 并指明其父主题为 _TheThemeMachine_。最终CodeGen命令将生成如下文件结构：

![][103]

其中只创建了Theme.txt和Views\Web.config文件。控制面板通过Theme.txt文件（主题清单）来查询信息，如主题名称。这里面同样制定了父主题。 Web.config是ASP.NET MVC渲染Views文件夹中页面所需的配置文件。你几乎不需要修改Web.config文件。


## 从The Theme Machine中拷贝文件

为了让示例较为简单，你只需要自定义 Site.css 文件。从TheThemeMachine\Styles文件夹中将Site.css文件拷贝到MyTheme\Styles文件夹中。

你还需要拷贝TheThemeMachine\Views\Layout.cshtml文件到MyTheme\Views文件夹中。——*新版本中，此步骤非必需。*


## 自定义主题文件

在你将要修改的文件拷贝到新主题文件夹后，你就可以进行修改了。你也可以按需创建一些新文件。在本示例中，我们仅仅修改页面的背景颜色。 

在拷贝过来的 Site.css 文件中，查找**General**部分的**body**样式。然后，将背景颜色从**#fff**修改为**#fff8dc**，代码如下：

    body { 
      font-size: 81.3%;
      color: #434343;
      background: #fff8dc; 
      font-family: Tahoma, "Helvetica Neue", Arial, Helvetica, sans-serif;
    }

至此，背景颜色将修改为*玉米丝色-cornsilk*——淡黄色。

你也可以在主题的根文件夹下为新主题添加一个缩略图。其名称必须为Theme.png。此图片会在控制面板中显示，以便于用户选择主题。

下图为从TheThemeMachine拷贝的图片，然后将 背景色调为淡黄色：

![][104]

## 应用新主题

在控制面板中，点击**主题**，切换到**已安装**标签。在**已安装**标签下，将会在**可用**下面显示新主题。：

![][105]

点击**设为当前**。**已安装**标签会刷新显示——**MyTheme**显示为当前主题。

至此，新主题已经在网站中使用。 

    
***
译：[奇葩史][000]