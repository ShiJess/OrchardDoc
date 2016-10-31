<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Installing-Orchard/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Working-with-Orchard-in-WebMatrix/
[003]: https://github.com/OrchardCMS/Orchard/releases
[004]: http://docs.orchardproject.net/en/latest/Documentation/Manually-installing-Orchard-zip-file
[005]: http://docs.orchardproject.net/en/latest/Documentation/Setting-up-a-source-enlistment "TODO"
[006]: http://www.microsoft.com/web/downloads/platform.aspx
[007]: http://docs.orchardproject.net/en/latest/Documentation/Making-a-Web-Site-Recipe/ "TODO"
[008]: http://www.shisujie.com/blog/Manually-installing-Orchard-zip-file
[009]: http://www.shisujie.com/blog/Working-with-Orchard-in-WebMatrix

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Attachments/Installing-Orchard/webpi_install.png
[102]: http://docs.orchardproject.net/en/latest/Attachments/Installing-Orchard/Install_acceptterms.png
[103]: http://docs.orchardproject.net/en/latest/Attachments/Installing-Orchard/Install_success.png
[104]: http://docs.orchardproject.net/en/latest/Attachments/Installing-Orchard/launch_Orchard_WebMatrix.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots/get_started_dialog_1.png
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots_85/setup_sqlserver.png
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots/get_started_recipe.png
[108]: http://docs.orchardproject.net/en/latest/Attachments/Installing-Orchard/first_frontend.png

> 原文链接：[Installing Orchard][001]

*文章内容基于Orchard 1.8版本*

# 安装Orchard的方式
主要有以下四种方式安装Orchard：

* 利用Microsoft Web Platform Installer（微软Web平台安装程序）进行安装。
* 利用Microsoft WebMatrix安装。参考：[原文：使用WebMatrix管理Orchard][002]、[译文：Orchard入门 ——使用WebMatrix管理Orchard][009]。
* 下载Orchard[.zip file][003]安装包手动安装。参考：[原文：利用zip包手动安装][004]、[译文：Orchard入门——手动安装Orchard][008]。
* 使用Visual Studio直接源码编译安装。参考：[原文：Enlist][005]。

本文将介绍利用Microsoft Web Platform Installer安装Orchard

# 系统环境要求
运行Orchard的最小环境配置要求:

* ASP.NET 4.5
* 运行IIS Express 8, 7.5 或 IIS 7.x的服务端

确保您的服务器Asp.net IIS模块可用，并保证对应的应用程序池使用的是托管管道模式为“集成”。

> **注意**:  为确保Orchard的正确运行，您最好卸载以前安装过的WebMatrix, ASP.NET Web Pages以及ASP.NET MVC 4的旧版本。 
以下内容以全新安装的Windows 8.1为基础进行测试。其中涉及内容有：Web Platform Installer、Orchard、IIS 8.0 Express，以及WebMatrix（可选-可用Visual Studio替代）、SQL Server Compact 4.0（可选-可用SQL Server替代）。 

# 安装Orchard

前提：下载安装-[Web Platform Installer][006]。

参考下图找到**Orchard CMS**并点击**Add**——以此将Orchard添加到安装列表.

![][101]

点击**Install**进行安装。点击接受许可条款并继续安装

![][102]

安装完成后显示如下信息——Orchard以及其相关的一些工具。点击 **Finish** 完成安装。

![][103]

# 在WebMatrix中运行Orchard

在WebMatrix启动后, Orchard将自动在默认浏览器中打开。如果没有，点击 **Run** 下拉按钮，选择浏览器来手动启动Orchard。
在WebMatrix中，可以点击**Files**工作去查看Orchard网站的目录内容。

![][104]

第一次启动Orchard时，浏览器将显示安装配置界面： 

![][105]

默认情况下，Orchard选择使用内置数据库——在你没有单独数据库服务的情况下使用。如果你有在使用中的SQL Server或SQL Server Express，你可以为其手动配置器连接字符串。另外，你可以输入表前缀，这样你可以多个Orchard网站使用同一个数据库，并且保证数据分开。

![][106]

安装界面中还包含了recipe（网站的功能模板？）设置。你可以选择如下几种recipe:

* **Default**. 配置使用Orchard的常用功能——倾向于CMS
* **Blog**. 配置为个人博客
* **Core**. 只配置Orchard核心框架-自己另外手动开发额外功能

![][107]

关于recipe的信息以及如何定制开发recipe，参考：[原文：Making a Web Site Recipe][007] 

填完安装必需信息后，点击 **Finish Setup**。安装程序执行完后，就会跳转到新网站的首页。

![][108]

后面就是在控制面板里面自己各种设置了。

***
译：[奇葩史][000]