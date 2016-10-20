<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Getting-Started/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Installing-Orchard/
[003]: http://www.shisujie.com/blog/Installing-Orchard
[004]: http://tryorchard.net/
[005]: http://dotnest.com/
[006]: http://dotnest.com/knowledge-base/topics/theming/
[007]: http://azure.microsoft.com/en-us/services/websites/
[008]: http://docs.orchardproject.net/en/latest/Documentation/Managing-Widgets/


<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/getting-started/1.png
[102]: http://docs.orchardproject.net/en/latest/Upload/getting-started/2.png
[103]: http://docs.orchardproject.net/en/latest/Upload/getting-started/3.png
[104]: http://docs.orchardproject.net/en/latest/Upload/getting-started/4.png
[105]: http://docs.orchardproject.net/en/latest/Upload/getting-started/5.png
[106]: http://docs.orchardproject.net/en/latest/Upload/getting-started/6.png
[107]: http://docs.orchardproject.net/en/latest/Upload/getting-started/7.png
[108]: http://docs.orchardproject.net/en/latest/Upload/getting-started/8.png
[109]: http://docs.orchardproject.net/en/latest/Upload/getting-started/15.png
[110]: http://docs.orchardproject.net/en/latest/Upload/getting-started/14.png
[111]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/ThemeZonePreview_homepage_675.png
[112]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_before_contextual_edits_675.png
[113]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/widgets_default_layer_675.png
[114]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_layer_selection_675.png
[115]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_layer_675.png
[116]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_tripelthird_675.png
[117]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_remove_tripelthird_675.png
[118]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_add_tripelthird_675.png
[119]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_choose_widget_675.png
[120]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_new_thirdleaderaside_675.png
[121]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/homepage_modified_thirdleaderaside_675.png
[122]: http://docs.orchardproject.net/en/latest/Upload/getting-started/9.png
[123]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/home_page_675.png


> 原文链接：[Building Your First Orchard Site][001]

*文章内容基于Orchard 1.8版本*

本文将逐步简要介绍Orchard提供的功能。如果你是第一次使用Orchard，本文将非常适合你。

### Orchard入门

对于初次接触Orchard的人，我们提供以下一些关于Orchard资源和最新信息的链接：

1. [Orchard Beginner][6]
2. [Orchard in GitHub - Orchard Code Repository][1]
3. [Orchard Discussion Forum - Discussion area for Orchard][3]
4. [Orchard Documentation - Documentation area for Orchard][2]
5. [Orchard Community Websites - Community sites on Orchard from all over the world][4]
6. [Orchard CMS Weekly Meeting][5]


  [1]: https://github.com/OrchardCMS/Orchard
  [2]: http://docs.orchardproject.net/
  [3]: http://orchard.codeplex.com/discussions
  [4]: http://orchardproject.net/
  [5]: http://orchardproject.net/discussions
  [6]: http://orchardbeginner.com


本文假设你已经安装了Orchard并且已经配置号了网站。如果没有，参见：[原文：Installing Orchard][002]、[译文：Orchard 安装][003]。

另外，如果你没有在本地机器或本地IIS服务器安装Orchard，你也可以通过其他几种方法尝试使用Orchard。

### Orchard试用

[Try Orchard!][004] 是Orchard的一个运行示例：你可以通过已经运行的Demo示例来尝试感受Orchard。

关于[Try Orchard!][004]：
* 不需要注册安装
* 它是一个demo网站，会不断的重新安装
* 这是初步了解Orchard最简单的方式

请注意 Try Orchard! 仅仅是用来测试：demo网站每小时重置一次，所以不要再上面发布你的博客。

![Try Orchard][101]

![Try Orchard][102]

### DotNest : Orchard SaaS 提供商

[DotNest][005] 是Orchard SaaS 提供商: 那意味着你可以很方便的注册并创建Orchard网站——运行在云服务上。你只需要使用它，而不必关注部署和升级的问题。

借助 DotNest，你可以非常方便快速的使用Orchard网站，并且你可以将你在这上面创建的网站公布给所有人访问。除了使用Orchard的用户界面和功能，你也可以进行一些Orchard主题的基础开发，修改网站风格，自定义Orchard网站等。
* [basics of Orchard theme development][006] *官网此链接有误，本文已修改*

方便也就意味有缺陷：由于DotNest的架构，你无法安装自定义的模块，所以你只能使用已有的模块——不过应该足以应付网站运行的大部分情况。

**1)** 什么是 **DotNest** 
![][103]

**2)** 点击 **New Tenant** 来创建托管网站

![][104]

**3)** 填写创建托管网站所必需的信息

![][105]

**3)** **New Tenant** 创建成功

![][106]

### 在Azure上运行Orchard网站

[免费注册][007]微软Azure后，可以在Azure的应用商店里选择Orchard一键部署来创建网站。*没有信用卡的绕行，免费注册需要信用卡——Visa、万事达、美国的Express*

托管在Azure的Orchard网站完全由你自己控制：你可以安装任何你想要的模块和主题。当然，这也就意味着所有的事都得自己干：网站维护、更新升级、问题修复等。

![][107]

![][108]
  
![][109]

![][110]

### 修改主页布局

Orchard网站默认使用一个名为 "Theme Machine" 的主题。此主题包括 CSS 样式和一个基本的布局。Orchard允许你控制网站上的每一个页面包含或不包含哪些部分（区域）。 

![][111]

在 **Navigation** 区域默认包含一个 *Home* 选项卡菜单。页面底部区域的 **TripelFirst, TripleSecond** 和 **TripleThird** 内容是虚构的第一，二，三负责人信息。 

除了上述区域，每一页还包含一个中心区域（样例中为文字 *"Welcome to Orchard"* 到 *"Thank you for using Orchard"*），在本教程中，它被称为页面的**主体-Body** 。 

![][112]

尽管Theme Machine 定义了许多可用区域，但只有有部件的区域才会显示出来，更多部件内容见：[原文：Managing-Widgets][008]。首页显示Navigation, TripelFirst, TripelSecond 和 TripelThird 区域是由于它们含有部件。下面对此进行演示：

**1)** 在控制面板中选中 **部件 Widgets** 。  

部件管理页面打开后默认选中 *Default* 层。在默认层上显示的区域将在所有页面显示。因此 *Navigation* 区以及内部的 **Main Menu** 部件是在所有页面显示。主菜单部件显示为绿色是因为它被添加到**当前层**的一个区域内。  

![][113]

**2)** 选择 **HomePage** 层可以查看在首页有哪些区域是显示的。  

在选中层中已添加部件的区域显示为绿色 (FirstLeaderAside, SecondLeaderAside and ThirdLeaderAside)。 在其他层中已添加部件的区域将显示为灰色 (Main Menu)。

![][114]

![][115]

在首页中，TripelFirst, TripelSecond, 和 TripelThird 区域都有部件，故会显示在首页上。移除部件将会隐藏区域。  

**3)** 点击 **Third Leader Aside** 部件后的 **Remove** 。

![][116]

区域TripelThird将不在首页显示。

![][117]

**4)** 点击TripelThird区域后的 **Add** 添加部件。

![][118]

**5)** 选择 **HTML Widget** 添加一个部件到 TripelThird 区域。

![][119]

**6)** 输入部件名称及内容

![][120]

**7)** 点击 **Save** 完成添加部件.

**8)** 点击控制面板左上角**网站名称**跳转到网站首页，查看TripelThird区域的变化。

![][121]

### 编辑主页内容

Orchard提供了一个简化页面区域或页面主体编辑的功能。要打开功能，需启用 **Content Control Wrapper** 和 **Widget Control Wrapper** 模块 

**1)** 点击控制面板中的 **模块 Modules** 

**2)** 启用 **Content Control Wrapper**

**3)** 启用 **Widget Control Wrapper**

![][122]

一旦启用这两个模块，你可以通过点击区域右上角的 **Edit** 链接来编辑区域内容。

![][123]

**4)** 点击首页上*TripelFirst*区域的 **Edit** 链接。 

**5)** 修改标题、主体内容等。 

<!--原文为三级标题，实则是接着上面的扩展，故需改四级-->
#### Inserting a Media Item 

**6)** Select **Insert Media Item**. 

![](../Upload/screenshots_675/edit_widget_media_1_675.png)

**7)** Click **Create Folder**. 

![](../Attachments/Getting-Started/MedLibCreateFolder.png)

**8)** Name the folder *myImages* and click **Save**. 

![](../Attachments/Getting-Started/MedLibSaveFolderName.png)

**9)** Click the folder *myImages*, and then click **Import** 

![](../Attachments/Getting-Started/MedLibImport.png)

**10)** Click *My Computer* and then click in the central zone to browse for an image. If you prefer you can drop your image into the central zone.

![](../Attachments/Getting-Started/MedLibUpload.png)


**11)** Close the dialog.

![](../Attachments/Getting-Started/MedLibClose.png)


**12)** Click the image and click **Select**.

![](../Attachments/Getting-Started/MedLibSelectImage.png)

**13)** If needed, resize the image using the handlers so that later it fits nicely into the zone. Then click **Save** to save the changes to the widget. 

![](../Attachments/Getting-Started/MedLibSaveContent.png)

The home page is automatically displayed with the updated zone.

![](../Attachments/Getting-Started/FirstLeaderAside.png)

**14)** Select the **Edit** link for the **Body** of the page.

![](../Upload/screenshots_675/edit_body_675.png)

 Orchard will display the **Edit Page** screen.
 > **Note:** The Edit Page screen can also be reached from the Dashboard by selecting **Content** on the Dashboard and then selecting **Edit** for the page you are interested in.

 **15)** Enter some text for the content. 

![](../Upload/screenshots_675/edit_homepage_675.png)

**16)** Select **Publish Now** at the bottom of the page to make the updates to the page visible immediately.

![](../Attachments/Getting-Started/PagePublishNow.png)


### Adding a New Page to Your Site

**1)** In the Orchard Dashboard, under **New**, select **Page**.

**2)** Enter a title for the page.  When you enter a title for the page and save it (for example, "Download"), the permalink (URL) for the page will be filled in automatically ("download").  You can edit this link if you prefer a different URL.

**3)** Enter some text for the content page body.

![](../Upload/screenshots_675/create_new_page_0_1_675.png)


**4)**  In the **Tags** field, add comma-separated tags such as "download" and "Orchard" so that you can search and filter using those tags later. 

**5)** Check **Show on main menu** and enter the menu text ("Downloads") to use in the site's main menu.

**6)** Select **Publish Now** to make the updates to the page visible immediately. You can also save the page as a draft (to edit later before publishing), or you can choose to publish the page at a specific date and time.

![](../Attachments/Getting-Started/CreateNewPage.png)

**7)** Select **Your Site** in the upper-left side of the Dashboard to view the modified home page with the new menu. Clik **Downloads** and you will see your new page.
 
### Adding New Layer for a Page

To change the layout of your new page without affecting the rest of the site you can create a new layer, that will be applied only to the *Downloads* page. Then you can place some widgets on that layer and they will be visible only in the *Downloads* page.
 

**1)** Go to the Dashboard and select **Widgets**. Then click **add a new layer** to add a new layer for this page which will allow you to customize the layout for the new page at a later point in time.

![](../Attachments/Getting-Started/AddNewLayer.png)

**2)** Write a name for the layer, a description, and a layer rule: url"~/download". This will instruct the Orchard System to show the widgets in this layer only when the url of the browser is pointing to "download". Select **Save**.

![](../Upload/screenshots_675/create_new_page_2_2_675.png)


### Adding a New HTML Widget

**3)** To check that your layer rule is working you can add a widget to it. Ensure that **Current Layer** is **Download**. Click **Add** in *AsideFirst*.

![](../Attachments/Getting-Started/AddNewWidget.png)

**4)** Add a new **Html Widget**.

![](../Attachments/Getting-Started/AddHtmlWidget.png)

**5)** Write a title and a body for it. Save it.

![](../Attachments/Getting-Started/EditHtmlWidget.png)

**6)** Select **Your Site** in the upper-left side of the Dashboard. Navigate to *Downloads*. You should see the custom layout.

![](../Attachments/Getting-Started/CustomLayoutResult.png)



### Selecting A Theme

To customize the look and feel of the Orchard website you change the theme. 

**1)** On the Orchard Dashboard, select **Themes**.  The currently installed themes are listed. 

**2)** To download new themes, select the **Gallery** tab.

**3)** Search for **PJS.Bootstrap** to find the PJS.Bootstrap Theme. Install the **PJS.Bootstrap** theme.

**4)** Select the **Installed** tab. 

After a theme has been installed it appears as an option in the **Available** section on the **Installed** tab. In the following illustration, the **PJS.Bootstrap** theme has been installed so it appears in the **Available** section. (The current theme for the site is **PJS.Bootstrap**.) 

**5)** To see how your site will look with an available them,  select **Preview** for the theme.  To apply an available theme to your site select **Set Current** for the theme. For more details, see [Previewing and Applying a Theme](Previewing-and-applying-a-theme) and [Installing Themes](Installing-themes).

![](../Upload/getting-started/10.png)

![](../Upload/getting-started/11.png)


### Extending Orchard With Modules And Features

A key feature of Orchard is the ability to add new features in order to extend the functionality of your site. The primary way to do this is by installing modules. You can think of a module as a package of files (in a .zip folder) that can be installed on your site. To view the modules that are included with Orchard, in the Orchard Dashboard, click **Modules** and then click the **Installed** tab in the **Modules** screen.

![](../Upload/getting-started/12.png)

Orchard provides some built-in modules, and you can install new modules. For details, see [Installing and Upgrading Modules](Installing-and-upgrading-modules) and [Registering additional gallery feeds](Module-gallery-feeds).

Individual modules can expose features that can be independently enabled or disabled. To view the features exposed by the built-in modules in Orchard, click the **Features** tab in the **Modules** screen.  

![](../Upload/getting-started/13.png)

Each feature has an **Enable** or **Disable** link (depending on its current state), as well as an optional list of dependencies that must also be enabled for a specific feature. The documentation throughout this site describes the variety of features in Orchard and how you can use them to customize your site's user interface and behavior.


译：[奇葩史][000]