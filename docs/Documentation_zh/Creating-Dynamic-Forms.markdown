<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Creating-Dynamic-Forms/
[002]: http://www.shisujie.com/blog/Creating-Dynamic-Forms

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/enable-dynamic-forms.png "Enable the Dynamic Forms module"
[102]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/dynamic-forms-new-content-type-subscribe-form.png "New Orchard CMS content type"
[103]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/subscribe-form-email-field.png "Add Email input field the Subscribe Form content type"
[104]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/subscribe-form.png "Subscribe Form content type"
[105]: https://raw.githubusercontent.com/ShiJess/OrchardDoc/chinesedoc/docs/Upload/dynamic-forms/add-widget-to-asidesecond.png "Add new Widget to AsideSecond zone"
[106]: https://raw.githubusercontent.com/ShiJess/OrchardDoc/chinesedoc/docs/Upload/dynamic-forms/add-widget-to-asidesecond2.png "Add new Widget to AsideSecond zone"
[107]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/dynamic-forms-edit-layout.png "Forms Widget Layout"
[108]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/dynamic-forms-edit-email-field.png "Edit Email Field"
[109]: https://raw.githubusercontent.com/ShiJess/OrchardDoc/chinesedoc/docs/Upload/dynamic-forms/open-edit-form.png "Add new Widget to AsideSecond zone"
[110]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/dynamic-forms-bind-form.png "Bind Form to Content"
[111]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/dynamic-forms-bind-email.png "Bind Email Field"
[112]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/news-letter-widget.png "Dynamic Forms Widget"
[113]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/page-view.png "Page view with new widget"
[114]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/remove-owner.png "Remove owner option from Common Part"
[115]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/no-content-type.png "No Content Type"
[116]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/subscribe-form-entries.png "Dynamic Forms viewed by content type - Subscribe Form"
[117]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/form-submissions.png "Form Submissions"
[118]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/import-export-enabled.png "Enable the Import/Export module"
[119]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/export.png "Export the emails by checking the Subscribe Form content type"
[120]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/enable-import-export.png "Enabling form submission import-export"
[121]: http://docs.orchardproject.net/en/latest/Upload/dynamic-forms/exporting-form-submissions.png "Exporting Form Submissions"


[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Create Dynamic Forms][001]  
> 译文链接：[Orchard网站管理——创建动态表单][002]

Dynamic Forms模块用于从网站前台获取访问者提交的信息。Dynamic Forms可以和其他内容类型合起来使用，也可以单独使用。Dynamic Forms可用于创建 *联系我们* 和 *订阅* 部件/页面等等。提交信息可以存储在Orchard中，而且可以在以后导出。


### 启用Dynamic Forms模块 ###

Dynamic Form模块与Custom Forms模块有所不同，它可以和其他内容类型合作获取前台用户输入，还可以选择存储表单提交内容。如果你选择存储提交的内容，你可以在控制面板中的**表单提交**菜单内查看。提交后存储的内容可以通过导入导出模块导出。要启用Dynamic Forms模块，可以在控制面板的**模块**中启用它。：

![Enabling Dynamic Forms in Orchard CMS][101]

一旦启用此功能模块后，在控制面板的**新建**下面会出现**Form**内容类型。

如前所述，Dynamic Forms可以和其他内容类型创建提交内容，也可以单独在网站中创建form。点击控制面板中**新建**下的**Form**创建一个新的form，然后会出现form编辑界面，可以让你创建自己的form。在此界面中，你可以选择存储提交，或者创建内容表单来提交值。下面，我们创建部件，然后添加到界面 —— 用于方便访问者添加邮件订阅。其中用户邮件地址将成为捕获的对象。

### 将表单提交作为一个内容类型存储 ###

为了获取动态表单上的访问者的邮件地址并将其存储为内容，我们需要在Orchard中创建一个新的内容类型。首先进入控制面板，选中**内容定义**，然后点击右上角的**创建新类型**按钮。在界面中输入类型名称'Subscribe Form'。

![Subscribe Form content type][102]

下一个界面会让我们选择新建的*Subscribe Form*内容类型需要添加什么元件。由于我们要获取的是一个电子邮件地址，所以此处不选择任何选项，然后点击保存。现在，我们已经创建了一个新的内容类型，下面我们为其添加一个电子邮件地址字段，类型为**Input Field**。

![Subscribe Form email field][103]

在添加了名为Email的输入字段后，我们现在可以自定义新的输入字段的类型验证 —— 此处我们在输入类型中下拉选择Email。其他字段自己看着办 —— 随便填。

![Subscribe Form][104]

至此我们的内容类型已经含有我们需要的所有部分，下面需要在界面上创建新的部件。我们现在已经启用了**Dynamic Forms**模块并创建了新的内容类型（Subscribe Form）—— 用于获取访问者的邮件地址。接下来就是创建部件了。

### 创建Form部件 ###

在控制面板中选择**部件**菜单，点击AsideSecond区域后的**添加**，以此添加一个Form部件。

> 此处官网图有误，故替换

![Add Widget to AsideSecond][105]

![Add Widget to AsideSecond][106]

剩下的事情就是调整我们新建的窗体部件设置。例如，将层设为**默认**，位置设为**1**。这将导致部件在所有页面都会在AsideSecond区域显示，且显示在最前。在窗体的布局部分，你需要添加表单字段，并将其绑定到你的内容类型。在布局部分，见下图突出显示部分，在界面右侧，拖动一个**Email Field**字段控件到布局界面上。

![Forms Widget Layout][107]

一旦你松开鼠标，一个 *Edit Email Field* 界面会弹出来。按照下图填写内容。

![Edit Email Field][108]

然后点击 *Validation* 标签，确保**Required**勾选框已勾选。现在可以保存窗体，但我们并没有完成。在保存之后，我们可以将其绑定到我们之前创建的内容类型上。将鼠标悬停在form上，然后点击尖括号，如下图：

![][109]  

你将可以看到 *Edit Form* 弹出框。勾选上**Create Content**，然后在下拉框中选择*Subscribe Form*，完成后点击保存。

![Bind Form To Content][110]

至此已经快完成了，现在将鼠标悬停在 *Email Field* 上面，并点击尖括号。点击 *Bindings* 标签，然后勾选你要绑定的字段，在我们的示例中为 *Subscribe Form* 内容类型下的 *Email.Text* 字段。如果你没有看到binding标签，请保持form后再重新回到此处编辑。

![Bind Email Field][111]

下图为一些示例设置：

![Dynamic Forms Widget][112]

在保存部件之后，浏览网站页面检查新功能。

![Page view with new widget][113]

**注意**: 如果输入字段对拥有者显示，可以在Subscribe Form内容类型定义中的Common部分，取消勾选“对拥有者显示编辑器——*Show editor for owner*”来移除它。—— *个人测试好像不起作用* 

![Common Part][114]

### 不通过内容类型存储表单提交 ###

此处理起来很简单，你只需要在form布局中勾选 *Store Submission* 。

![No Content Type][115]

### 查看提交的动态表单数据 ###

至此，经过以上步骤的处理，我们已经可以提交表单数据。由于我们在之前勾选了‘Create Content’，所以Orchard会将提交内容保存。而要查看内容保存在哪，进行如下操作：在控制面板中，点击**内容**即可。

![Subscribe Form Content Type][116]

在控制面板中，你还可以通过**表单提交**菜单查看不通过创建内容类型的提交数据。

![Form Submissions][117]

### 导出动态表单数据 ###

由于动态表单可以保存为内容类型或者表单提交，所以你会有不同的方式来导入导出。

#### 导出保存为内容类型的表单 ####

至此仅剩的事情就是导出提交数据列表，以便于被其他服务使用，类似于Publicaster, Campaign Monitor, MailChimp等。从Orchard CMS中导出任何内容最简单的方法是使用**导入/导出**模块。在Orchard 1.6版本及以后版本，**导入/导出**模块是附带的在内的，只是默认不启用。下面启用**导入/导出**模块。

![Import/Export module][118]

现在可以在控制面板左侧导航中看到**导入/导出**功能。在**导入/导出**模块页中，切换到**导出**标签。要导出已提交的邮件列表数据，则勾选**Subscribe Form**内容类型旁边的勾选框 —— *新版Orchard需要勾选内容和内容定义后方能显示类型*。 界面中第一项**元数据-Metadata**,表示包含内容类型定义 —— *新版直接在内容类型后有类型定义勾选框，与此处不同*。这提供了一种简单的方法来复制内容类型 —— 在从一个Orchard CMS迁移到另一个会比较有用。这种情况的一个主要例子是：将一个新的内容类型从开发环境的站点迁移到生产环境的站点。当Orchard导入同时含有元数据和数据的xml文件时，它会创建内容类型副本来导入对应数据。  

在当前示例中，我们只关注导出数据，所以不需要勾选元数据。同时，确保选择**仅包含草稿**，由于我们在前台提交的数据没有发布状态。—— *此处内容有问题，是否有发布状态取决于你在定义Form时的Create Content设置，可能是发布状态，也可能是草稿。*

![Export the Subscribe Form content][119]

导出的XML文件可以用MS Excel打开，并可以按照你的选择操作email内容等。至此，网站能够收集访问者的电子邮件地址，并将其导出以供后续联系。动态表单还常用于实现联系我们页面或其他任何需要收集用户信息的页面。

#### 导出保存为提交表单的表单内容 ####

要导出表单提交里的数据，你需要启用动态表单的导入导出模块。

> 注：新版中没有此模块，导入导出功能中已含有导出表单提交的选项

![Forms Import Export Module][120]

一旦启用，你可以在导出功能中自定义导出步骤中选择"Forms"来导出**表单提交**内容。

![Exporting Form Submissions][121]

***
译：[奇葩史][000]