<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Blogging-with-LiveWriter/
[002]: http://openlivewriter.org/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/feature_enable_675.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots/live_writer.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots/livewriter2.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter3.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter4.png
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter5.png
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter6.png
[108]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter7.png
[109]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter8.png
[110]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter9.png
[111]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter10.png
[112]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter11.png
[113]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/livewriter12.png
[114]: http://docs.orchardproject.net/en/latest/Upload/screenshots/livewriter13.png


> 原文链接：[Blogging with LiveWriter][001]

尽管Orchard在控制面板中内置了博文编辑功能，但很多人更喜欢使用客户端来写作文章，例如使用[Open Live Writer][002]。客户端使用XML-RPC接口远程发布文章，同时提供额外的功能，如保存离线草稿（例如：在飞机上写作你的博文，稍后再同步到你的网站）。

要允许远程发布博客，在控制面板中点击**模块——*Features*** 

要让Orchard支持Open Live Writer，你需要启用 **Remote Blog Publishing** 功能——点击**Remote Blog Publishing**功能块中的**启用——Enable** 链接。

![][101]

> 注：文中图片是Windows Live Write，但Open Live Write是从其衍生过来的，操作基本相同。

现在，在**开始** 菜单中找到 Live Writer 并启动

![][102]

点击**Blogs**菜单里的**Add blog account...**

![][103]

选择 **Other blog service** 并点击 **Next**.

![][104]

输入你的Orchard博客的地址，以及安装Orchard时定义的用户名和密码。

> 注意: 你也可以用其他支持XML-RPC的客户端软件，不过你可能需要提供xmlrpc接口的地址，而不仅仅是博客地址。例如：http://myimaginaryorchardsite.com/xmlrpc 。

![][105]

Live Writer会去连接你的博客，同时去判断你的Orchard是否支持XML-RPC功能，以及下载当前网站的主题（用于发布前预览）。如果在连接期间，软件提示你创建临时的博文，在弹出框中选择“Yes”。

![][106]

Live Writer配置完成后，点击 **Finish**.

![][107]

在Live Writer编辑区域，输入标题及博文内容。

![][108]

你同样可以利用工具栏中的 **Insert Picture** 按钮，为你的博文插入图片

![][109]

![][110]

要自定义博文的链接地址，点击菜单中的 **View / Properties**

> **新版操作为：点击工具栏下方最右边的*View all***

![][111]

 **Slug** 将显示在编辑下方——用于输入博文所用的路径的一部分。

![][112]

要预览博文在Orchard当前主题下的的显示效果，点击 **Preview** 标签。当你觉得调好博文显示后，点击**Publish**按钮发布

![][113]

Live Writer会发布你的博文，然后自动在浏览器中打开博文地址以供查看。

![][114]


***
译：[奇葩史][000]