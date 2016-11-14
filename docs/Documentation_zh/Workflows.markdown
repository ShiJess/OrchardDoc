<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Workflows/
[002]: http://docs.orchardproject.net/en/latest/Documentation/Configuring-email/
[003]: http://docs.orchardproject.net/en/latest/Documentation/Creating-custom-content-types/
[004]: http://www.shisujie.com/blog/Creating-custom-content-types
[005]: http://docs.orchardproject.net/en/latest/Documentation/Creating-Custom-Forms "Use Custom Form to create subscribe and contact us pages in Orchard"
[006]: http://docs.orchardproject.net/en/latest/Documentation/Orchard-TV

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/workflows/workflowsmodule.PNG
[102]: http://docs.orchardproject.net/en/latest/Upload/workflows/emailmodule.PNG
[103]: http://docs.orchardproject.net/en/latest/Upload/workflows/contactform.PNG
[104]: http://docs.orchardproject.net/en/latest/Upload/workflows/createnewworkflow.PNG
[105]: http://docs.orchardproject.net/en/latest/Upload/workflows/contactnotification.PNG
[106]: http://docs.orchardproject.net/en/latest/Upload/workflows/workflowcreated.PNG
[107]: http://docs.orchardproject.net/en/latest/Upload/workflows/workflowstartingstate.PNG
[108]: http://docs.orchardproject.net/en/latest/Upload/workflows/editingworkflowactivity.PNG
[109]: http://docs.orchardproject.net/en/latest/Upload/workflows/addingtimer.PNG
[110]: http://docs.orchardproject.net/en/latest/Upload/workflows/editingtimer.PNG
[111]: http://docs.orchardproject.net/en/latest/Upload/workflows/addingsendemail.PNG
[112]: http://docs.orchardproject.net/en/latest/Upload/workflows/editingsendemail.PNG
[113]: http://docs.orchardproject.net/en/latest/Upload/workflows/submittingform.PNG
[114]: http://docs.orchardproject.net/en/latest/Upload/workflows/workflowrunning.PNG
[115]: http://docs.orchardproject.net/en/latest/Upload/workflows/blockingactivity.PNG
[116]: http://docs.orchardproject.net/en/latest/Upload/workflows/emailsent.PNG
[117]: http://docs.orchardproject.net/en/latest/Upload/workflows/emailsent1.PNG

[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Workflows][001]

*文章内容基于Orchard 1.8版本*

Orchard中的**工作流**模块为我们提供了创建自定义工作流的功能，它可以为事件或活动创建工作流（如：**内容创建，内容发布，内容移除，发送邮件，定时器**，以及更多）。  

*依赖项: Orchard.Tokens, Orchard.Forms, Orchard.jQuery-新版为Resource模块，此功能应该包含在模块Resource中*

![][101]

在本节demo示例中，我们会创建一个 **联系我们的邮件通知工作流——Contact us Email Notification Workflow**。要在**工作流**模块中发送邮件，需要启用**EmailMessaging**模块。

## Email.Messaging

*关于怎样配置邮件，参见：[原文：Configuring Emainl][002] —— 官网链接有误，此处修改*

![][102]

## 自定义窗体

*关于如何创建自定义内容类型，参见：[原文：Creating Custom Content Types][003]、[译文：Orchard网站内容管理——创建自定义内容类型][004]*

*关于如何创建自定义窗体，参见：[原文：Create Custom Forms][005]*

![][103]

## 工作流示例

**1.** **创建工作流**

![][104]

**2.** **将工作流命名为Contact Us Email Notification，然后保存**

![][105]

**3.** **编辑Contact Us Email Notification 工作流**

![][106]

**4.** **设置工作流初始状态**

*工作流至少要有一个活动设为初始状态*

![][107]

**5.** **编辑工作流活动（提交表单）**

> 即，此处需要制定哪一个表单提交时触发此工作流

![][108]

**6.** **添加定时器活动**

> 注：需要启用工作流里的Timer模块

*添加定时器活动意味着设置了延迟操作，这样可以保证进程不会被阻塞。*

![][109]

**7.** **编辑定时器活动**

![][110]

**8.** **添加邮件发送活动**

> 注：需要启用工作流部分的Email模块

![][111]

**9.** **编辑邮件发送活动**

*使用令牌来访问终端用户提交的数据*

	New Contact Request by {Content.Fields.ContactUs.Name}

	<p>New Contact Request by {Content.Fields.ContactUs.Name}</p>

	<p>Email : {Content.Fields.ContactUs.EmailAddress}</p>

	<p>Message : {Content.Fields.ContactUs.Message}</p>

> 关于此处取值不同版本、不同的窗体使用方式可能各不相同，建议研究Form创建后再看此部分内容，如本人在取值时，有`{FormSubmission.Field:Email}`来处理

![][112]

**10.** **表单提交**

![][113]

**11.** **工作流运行**

> 即，在上一步用户提交表单后，工作流会自动运行

![][114]

**12.** **阻止活动**

*定时器（阻塞活动）会延迟两分钟*

![][115]

**13.** **发送联系我们邮件通知**

![][116]

![][117]

*关于更多工作流内容，浏览[Orchard Tutorials Area][006] —— 英文视频教程*


***
译：[奇葩史][000]