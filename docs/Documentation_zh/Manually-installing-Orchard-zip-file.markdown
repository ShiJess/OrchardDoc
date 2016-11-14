<!--链接集合-->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Manually-installing-Orchard-zip-file/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Installing-Orchard/
[003]: http://www.shisujie.com/blog/Installing-Orchard
[004]: https://github.com/OrchardCMS/Orchard/releases

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISSearchForAddRemovePrograms.png
[102]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISTurnOnWindowsFeatures.png
[103]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISEnableIISAndASP45.png
[104]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISSetFolderPermissions.png
[105]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISOpenIISManager.png
[106]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISStopDefaultWebSite.png
[107]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISAddANewWebsite.png
[108]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISAddWebsiteScreen.png
[109]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISPort80Conflict.png
[110]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISBrowseToSite.png
[111]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISWMOpenFolder.png
[112]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISWMSelectFolder.png
[113]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/IISWMRun.png
[114]: http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/contents_of_source_zip_file.png
<!--官网此文件路径有误，故直接取github上的-->
<!--本应为：http://docs.orchardproject.net/en/latest/Attachments/Manually-installing-Orchard-zip-file/VSOpenSolution.PNG-->
[115]: https://github.com/OrchardCMS/OrchardDoc/blob/master/docs/Attachments/Manually-installing-Orchard-zip-file/VSOpenSolution.png?raw=true


[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Manually Installing Orchard][001]

*文章内容基于Orchard 1.8版本*

本文将演示通过zip安装包安装Orchard所需要的步骤。

本文包括如下三种不同的Orchard使用方式：

  * IIS.
  * WebMatrix and IIS Express
  * Visual Studio and the Visual Studio Development Server.

> **注意**: 如果你倾向于使用Web Platform Installer，或者准备使用WebMatrix来开发网站,可以参考如下文档：[原文：Installing Orchard][002]、[译文：Orchard入门——安装Orchard][003]——文档内容包括了使用Web Platform Installer安装Orchard，也包括了部分WebMatrix内容。


# 下载Orchard的zip安装包

下载地址：[Releases Section of Orchard in GitHub][004]. 

其中有如下两个zip文件：

* _Orchard.Web.1.x.xx.zip_ : 此文件为编译好的网站程序，可以直接拿来用。里面不包含源码。
* _Orchard.Source.1.x.xx.zip_ : 此文件为源码程序。适用于自己开发模块使用。如果想研究源码，了解Orchard运行机制的话，可以下下来看。


# 将Orchard网站托管在IIS上
*以下测试环境为全新安装的Windows 8.1企业版*

首先安装IIS服务器，打开“控制面板-程序和功能”（或者如原文一样搜索）。

![][101]

点开 **启用或关闭Windows功能**.

![][102]

展开 **Internet Information Services** 并找到 **ASP.NET 4.5** 选中后确定。

![][103]

安装完成后建议重启系统，以此保证所有必要的服务都启动。

重启完成，下载 _Orchard.Web.1.x.xx.zip_ 安装包——[地址][004]。解压至单独的文件夹——内容包括一个*Orchard*文件夹以及几个文件。

拷贝*Orchard*文件夹到你的网站目录（或者如原文所示拷贝到iis默认网站目录*C:\inetpub\wwwroot\\*）

打开*Orchard*文件夹。以下先从*App\_Data*文件夹开始设置。

此文件夹为Orchard站点设置文件夹。鼠标右击*App\_Data*文件夹，点击 **属性** 并切换到**安全**标签；点击界面中的编辑打开权限文件夹设置窗口，给*IIS\_IUSRS*用户添加修改权限-即此用户对此文件夹拥有读写权限。

之后为如下文件夹进行相似步骤：

* _Modules_. 如果你需要从gallery（插件库）安装功能模块，修改权限是必需的。 (生产环境下，建议移除读写权限)
* _Themes_. 如果你需要从gallery（主题库）安装其他的主题，就需要修改权限。 (生产环境下，建议移除读写权限)
* _Media_. 此文件夹是Orchard媒体文件存储的位置(images, etc.)。（如果有单独的静态云存储的话，如阿里的oss，等，可以移除读写权限）

![][104]

> **提示-谨慎操作**: 如果需要完全重置网站，可以删除App\_Data文件夹里的所有内容——此操作将移除网站所有的自定义设置、用户和配置以及所有自定义的数据。
删除App\_Data文件夹内容之后，如果不需要你的媒体文件，也可以清空Media文件夹内容。网站所需的文件都会在下次启动时自动创建。

下面就可以打开IIS建立网站了。打开“控制面板-管理工具（记得查看方式改“大图标”才能看到管理工具）-IIS管理器”（或如原文所示搜索**Internet Information Services (IIS) Manager**, 并打开）.

![][105]

选择**Default Web Site** 将其 **停止**。——释放80端口

![][106]

右击 **网站** 并 **添加网站**.

![][107]

填写网站名称并选择 **物理路径** —— *Orchard* 文件夹。 点击 **确定**.

![][108]

如果弹出如下警告窗口-多个网站使用同一个80端口，点击 **是**

![][109]

至此，你的网站就可以运行了，可以点击 **浏览** 在浏览器中打开它，进入Orchard设置界面。

![][110]

# 使用WebMatrix 和 IIS Express运行网站

下载_Orchard.Web.1.x.xx.zip_安装包：[地址][004]。解压zip至单独的文件夹。启动WebMatrix，在**Quick Start** 界面, 点击 **Open** ，在弹出菜单中选择 **Folder**.

![][111]

 选择你的zip解压目录，并选中 **Orchard**文件夹,然后点击 **Select Folder** 打开网站

![][112]

在WebMatrix的 **Files** 区域，选择 **Orchard** 根目录，展开 **Run** 下拉菜单选择使用的浏览器，以此启动网站。——浏览器中将展示Orchard设置界面。

![][113]

# 使用Visual Studio 和 Visual Studio Development Server运行网站
*以下内容测试环境为Visual Studio 2013 Update 1.*

虽然Visual Studio可以运行预编译版本的Orchard，但使用完整代码版本的Orchard会更容易。——都用Visual Studio了，难道还有谁会用编译好的版本？

下载完整代码版：[地址][004]。解压zip包至单独目录。

![][114]

 运行 Visual Studio 打开项目（**File** > **Open** > **Project/Solution**）——**Orchard.sln** 解决方案文件在zip解压目录中的**src**文件夹下。

![][115]

按 Ctrl+F5运行网站，浏览器中将跳转至Orchard设置界面。

# 配置网站

原文内容基本与Installing Orchard重复；故此处直接给出Orchard安装入门链接：

* [原文链接：Installing Orchard][002]
* [译文链接：Orchard安装][003]
 

译：[奇葩史][000]