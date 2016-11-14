<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Adding-a-Blog-to-Your-Site/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Moderating-comments/
[003]: http://gallery.orchardproject.net/
[004]: http://docs.orchardproject.net/en/latest/Documentation/Organizing-content-with-tags/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/NewBlog.png
[102]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/ManageBlog.png
[103]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/NewPost1.png
[104]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/NewPost2.png
[105]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/PublishPost.png
[106]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/PublishedPostNotification.png
[107]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/WebsiteBlog.png
[108]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/PostComment.png
[109]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/CommentsSettings.png
[110]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/PostsByTag.png
[111]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/PostsByTagUrl.png
[112]: http://docs.orchardproject.net/en/latest/Attachments/Adding-A-Blog-To-Your-Site/AllTheTags.png

[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Adding a Blog to Your Site][001]

*文章内容基于Orchard 1.8版本*

Orchard提供一个博客引擎——这让添加一个新博客到你网站变得非常容易。
本文将介绍怎样添加一个新博客到你的网站，以及如何添加新的博文、设置评论与标签。

### 添加博客

展开Orchard控制面板中 **Blog** 子菜单。然后点击 **New Blog**.
在 *New Blog* 界面为博客添加标题、描述和菜单设置（是否显示及菜单文本），然后点击 **Save** 。

![][101]

保存成功后，将跳转到博客管理界面
> 注意: 你可以在你的Orchard网站建立多个博客。

![][102]

### 添加一篇博文到博客

点击 **New Post** 来添加一篇新的博文。在 **New Blog Post** 博文界面输入博文标题以及博文内容

![][103]

在 **Tags** 字段为博文添加标签（逗号分割）。勾选 **Show comments** , **Allow new comments** 和 **Allow threaded comments**。然后点击 **Save** 保存草稿。

![][104]

在控制面板中，点击 **Blog** 菜单就可以看到你的博文列表。在博文列表中，你刚添加的博文是一篇草稿（意味着网站访问者无法查看此博文）。点击 **Publish** 以允许网站访客查看此博文。

![][105]

发布成功后，界面会给予提示。   

![][106]

点击控制面板左上角 **网站标题** 跳转至首页查看。

一个新标签（**Blog**）已经被添加到菜单中。点击 **Blog** 标签展示博客及新添加的博文。要查看博文具体内容，点击博文内容最后的 **more** 链接。

![][107]

### 给博文添加评论

由于之前添加博文时允许用户评论，所以可以输入评论。新评论提交后可能不会立即显示，这取决于Orchard网站的设置——评论是否必须通过管理员审核方能发布。

![][108]

返回到控制面板界面，点击 **Settings**  下的 **Comments** 菜单。其中有两项设置：

1. 评论显示前必须被批准
2. 设置多久自动关闭评论功能

更多信息见： [原文：Moderating Comments][002]
> 注: 在 [Orchard Gallery][003] 有几个比较好模块可以为你的博客提供较好的垃圾邮件过滤。

![][109]

### 在博客中使用标签

Orchard提供通过标签浏览内容的功能。在博文中点击标签 (例如："Orchard")，就会显示含有此标签的内容列表。关于更多标签管理的内容见：[原文：Organizing Content with Tags][004].

![][110]

主要浏览标签内容的链接地址：  

![][111]

修改URL地址，保留至 _/Tags/_ 部分，页面将会显示你网站中使用到的标签列表。

![][112]


译：[奇葩史][000]