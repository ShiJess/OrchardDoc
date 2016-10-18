<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Working-with-Orchard-in-WebMatrix/
[002]: http://www.microsoft.com/web/webmatrix/
[003]: http://www.microsoft.com/web/downloads/platform.aspx
[004]: http://docs.orchardproject.net/en/latest/Documentation/Installing-Orchard/
[005]: http://www.shisujie.com/blog/Installing-Orchard
[006]: http://docs.orchardproject.net/en/latest/Documentation/Orchard-module-loader-and-dynamic-compilation
[007]: http://sybak.com/blog/2011/02/changing-the-file-types-that-open-with-webmatrix/
[008]: http://www.microsoft.com/web/post/how-to-publish-a-web-application-using-webmatrix

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots/install_selectorWebMatrix.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_start_675.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_select_orchard_675.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_orchard_eula_675.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_orchard_project_675.png
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots/webmatrix_run.png
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_files_675.png
[108]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_opendatabase_675.png
[109]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_databasetable_675.png
[110]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_database_refresh_675.png
[111]: http://docs.orchardproject.net/en/latest/Upload/screenshots/webmatrix_publish.png
[112]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_publish_firsttime_675.png
[113]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_AzurePortal_675.png
[114]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_import_settings_675.png
[115]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_publish_preview_675.png
[116]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/webmatrix_remote_view_675.png

> 原文链接：[Working with Orchard in WebMatrix][001]

[WebMatrix][002]——微软一站式Web开发工具，包括网站的创建、编辑以及发布——*不过现在微软更推荐VS code* 。WebMatrix中自带了内置Web服务器(IIS Express), 同时还内置了一个简化的编辑器——可以直接编辑及自定义应用，如Orchard。如果你使用Web Platform Installer安装Orchard，你需要选择将其安装到WebMatrix而非IIS——*在你决定使用WebMatrix管理网站的情况下*。

## WebMatrix的安装与启动

下载并安装[Web Platform Installer][003]。然后在Web Platform Install中找到 **Microsoft WebMatrix** 后点击 **Add** 按钮，然后点击 **Install**.

![][101]

安装时接受许可条款，并在安装完成后启动 WebMatrix 。

## 使用WebMatrix创建Orchard网站

点击开始界面中的 **App Gallery** 来添加Orchard网站  

![][102]

滚到找到 **Orchard CMS**。输入你想要的网站存储目录名称——如图所示，以 "Orchard CMS" 为例，稍后程序会自动创建"Documents/My Websites/Orchard CMS"目录，点击 **Next**。

![][103]

点击 **I Accept** 接受 EULA 协议.

![][104]

完成后，你的网站目录"My Websites"下会自动创建一个子目录"Orchard CMS"。点击 **OK** ，你将可以在Web Matrix中看到你的Orchard网站，同时浏览器将会打开 "Orchard 设置" 页面。

![][105]

接下来，就进入网站设置，具体介绍可以见如下文档：
* [原文链接：Installing Orchard][004]
* [译文链接：Orchard安装][005]


## 在Web Matrix中运行网站

在任何时候，你都可以选中要打开的网站，然后点击 **Run** 打开它。

![][106]

## 文件处理

你可以用WebMatrix来编辑你的Orchard网站文件。WebMatrix内置了一个简化的编辑器——提供了HTML, CSS, JavaScript, 和代码文件着色. 

尽管WebMatrix不提供编译环境，但Orchard自身对于修改的代码文件提供动态编译。详见：[原文：Orchard Dynamic Compilation][006]。

![][107]

你可以为你的WebMatrix内置编辑器自定义一些功能。参考文档： [地址][007]. 
 
例：
假设你的.info后缀文件，内容其实是xml类型，你可以让这一类文件使用XML editor,这样你就可以使用代码高亮来查看.info代码文件。以下为如何修改配置来让WebMatrix支持*.info*文件：首先，找到文件 **filetypes.xml** ——路径如下：

    32-bit machines: C:\Program Files\Microsoft WebMatrix\config\filetypes.xml
    64-bit machines: C:\Program Files (x86)\Microsoft WebMatrix\config\filetypes.xml

1) 将 .info 文件扩展名添加到 XML 文件的支持类型列表中:

    <FileType extension=".info;.config;.csproj;.vbproj;.resx;.settings;.sitemap;.user;.wsdl;.browser;.xaml;.xml;.xoml;.xsd;.xsl;.xslt;.mxml;.dbml;.wstemplate">
        <OpenAs>XML</OpenAs>
        <TabColor>Yellow</TabColor>
        <Icon>XMLFileIcon</Icon>
        <EmitUtf8BomByDefault>True</EmitUtf8BomByDefault>
        <Description>An XML File</Description>
    </FileType>

2) 将 .info 文件扩展名从 Text 文件支持类型列表中移除:

    <FileType extension=".ashx;.export;.po;.blogtemplate;.yml;.yaml;.manifest;.pl;.json;.csv">
        <OpenAs>Text</OpenAs>
        <TabColor>Gray</TabColor>
        <Icon>DefaultFileIcon</Icon>
        <EmitUtf8BomByDefault>False</EmitUtf8BomByDefault>
        <Description>Unknown file type</Description>
    </FileType>
    
3) 重启WebMatrix软件以应用更改。

## 数据库操作

如果你在Orchard安装时，选择了 **SQL Server Compact** 数据库，你可以在WebMatrix中选择**Databases**来打开 **Orchard.sdf** 数据库文件。
 
![][108]

打开数据库后，你可以选择打开对应的表查看内容了。

![][109]

(如果已经在 **Databases** 工作去，你可以右击 Orchard 节点选择 **Refresh** 来刷新数据库和表的显示内容。)

![][110]

## 网站发布

当你准备把你的网站发布到网上时，可以直接点击WebMatrix工具栏里的 **Publish** 按钮。

![][111]

如果是第一次发布，将显示 **Publish Your Site** 提示框。 

![][112]

 要发布网站，你得有Web托管服务提供商账号。如果还没有的话，可以选择 **Get Started with Windows Azure** 或 **Find Windows Web Hosting**。
 假如你选择了，你将需要选择网站的创建方式： Azure Website 或 Azure Web Role。

 ![][113]

当你注册了一个托管服务提供商后，提供商会发送相关信息（用户名、服务器名以及一些其他信息）的邮件给你。某些情况下，服务提供商会直接给出扩展名为_.publishsettings_的“Profile XML”文件——包含你所需要的基本信息。你可以直接使用 **Import publish profile** 将配置信息直接导入。 如果没有现成的配置文件，就需要手动录入配置了。 

 ![][114]  
 
当你网站已经发布后，你可能会需要修改部分内容并重新发布。当你选择发布时，WebMatrix会列出已修改的文件——最后一次更新到现在。与此同时，你可以在界面中选择哪些文件需要远程更新，然后点击 **Continue** 或取消发布。

 ![][115]

一旦发布网站后，你可以通过打开 **Remote View** 查看远程文件信息.

![][116]

更多关于 WebMatrix 发布网站的信息见如下地址： [链接][008]。


译：[奇葩史][000]