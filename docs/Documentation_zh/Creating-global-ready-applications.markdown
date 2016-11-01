<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Creating-global-ready-applications/
[002]: https://crowdin.com/
[003]: https://crowdin.net/project/orchard-cms
[004]: http://gallery.orchardproject.net/List/Modules/Orchard.Module.Vandelay.Industries
[005]: http://orchardproject.net/localization
[006]: https://crowdin.net/download/project/orchard-cms.zip
[007]: https://crowdin.net/download/project/orchard-cms-gallery.zip
[008]: https://crowdin.com/project/orchard-cms-gallery
[009]: http://gallery.orchardproject.net/List/Modules/Orchard.Module.Vandelay.Industries
[010]: http://docs.orchardproject.net/en/latest/Documentation/Creating-custom-content-types/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots/add_cultures_settings.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots/Culture_available.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots/Culture_newdefault.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/default_site_culture_fr_675.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/fr_po_file.png
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/Localize_enable_675.png
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/new_translation_675.png
[108]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/Localize_content_675.png
[109]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/Localize_en_downloadpg_675.png
[110]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/Localize_fr_downloadpg_675.png
[111]: http://docs.orchardproject.net/en/latest/Upload/screenshots/add_localization_part_MyEvent.png


> 原文链接：[Creating Global-Ready Applications][001]  
> 本文主要内容为本地化配置，同时介绍了如何为社区本地化项目提供贡献。


Orchard的本地化管理内容托管在外部服务商——[Crowdin][002]，此项目是公共使用的，并欢迎贡献内容的。本地化项目地址：[Orchard CMS][003]

Orchard支持两种本地化内容： 

- Orchard网站应用和内置模块的字符串文本本地化处理
- 数据库驱动内容项的本地化处理

关于以上两种本地化处理的功能特点，本文都将介绍。 

# 本地化Orchard应用和功能模块

Orchard应用中所有的字符串都一个独立的`T()` 方法输出 —— 以此控制字符串被翻译为网站默认语言。默认情况下，Orchard中包含英语（en-US）字符串，但是你可以添加额外的支持语言。控制面板界面和所有前段使用的静态字符串都可以通过导入 _.po_ 格式的翻译文件进行翻译处理。要本地化网站为特定语言，你需要下载并安装对应的 _.po_ 文件，然后按照本节所述，更新你的网站配置。

> **注意** 在.NET Framework 应用程序中，本地化处理常用 _.resx_ 文件与附属程序集。Orchard使用了一个更轻量级的方法——使用 _.po_ 文件。在Orchard中，翻译文件的数量是模块数量乘以支持的语言数量。翻译文件的数量可能快速增长，而附属程序集的设计不适合那种用法。另外，_.po_ 文件可以按需装载和卸载。和 _.resx_ 文件一样， _.po_ 文件同样在许多工具中使用。

## 安装翻译文件

举例来说，下载一组简体中文（zh-CN） *.po* 翻译文件。浏览以下地址获取翻译文件：

<https://crowdin.com/download/project/orchard-cms/zh-CN.zip>

点击链接下载 _.po_ 文件，将 _.zip_ 文件保存到你的计算机。

### 方法 1: 解压zip文件

解压下载的 _.zip_ 文件到网站的根目录。确保你确实直接解压到网站根目录，而不是在一个名字为 *.zip* 文件名的子文件夹。当系统提示**确定覆盖文件夹——*Confirm Folder Replace*** 以及合并相同名称文件夹内容询问时，选择 **全部使用相同操作——*Do this for all current items*** 并点击 **是——*Yes*** 来合并翻译文件。

此方法将解压的翻译文件添加到网站翻译文件目录中是非常简单的，但是，如果你的网站的模块相比于翻译文件中的少，你可能会有一些多余的目录。为避免这种情况，你可以尝试以下替代方案。

### 方法 2: 使用翻译管理功能

翻译管理功能在 [Vandelay Industries][004] 模块中，可以从功能库中获取，它利用命令行来精简翻译文件的安装。

一旦有心的模块安装后，你想要添加新的 *.po* 翻译文件，输入以下命令，必要时替换为po文件的文件路径：
    
    install translation c:\temp\fr.zip

这仅会解压那些已安装模块而又已经翻译的资源内容。如果模块没有找到，执行命令不会创建不必要的目录，这样你的Orchard网站仍然干净。

如果你后面添加新的模块，又有对应的翻译内容，你可能需要重新执行下命令。

## 切换网站语言环境

在控制面板中点击**设置**打开综合设置界面，配置网站默认语言环境。在**默认网站语言——*Default Site Culture***下，点击**Add or remove supported cultures for the site**. 

![][101]

在**语言**设置页面，在 **Add a culture** 列表中选择一种语言 (如：**zh-CN**) 然后点击 **Add**。支持语言对应的代码会被添加到**Cultures this site supports**下面。可以点击支持语言后的 **x** 按钮移除此语言支持。 

![][102]

在添加完语言支持后，点击控制面板中的**设置**返回到**综合设置**界面。

在 **Default Site Culture** 列表中，选择需要设置为默认的语言，完成后点击**Save**。

![][103]

如果你安装了合适的 _.po_ 文件集，应用新的语言设置后，控制面板的菜单和界面文本将会翻译为对应的语言。下图展示将语言设置为 **fr-FR**的效果。  

> 注: 此翻译文件可能没有翻译完。

![][104]

单纯设置网站语言不会有任何效果，除非安装了对应的翻译文件。Orchard从以下几个路径搜索翻译文件（从整体公用的部分到具体的内容部分）：

* **Core本地化文件路径** _~/Core/App\_Data/Localization/&lt;culture-code&gt;/orchard.core.po_
* **Modules本地化文件路径** _~/Modules/&lt;module-name&gt;/App\_Data/Localization/&lt;culture-code&gt;/orchard.module.po_
* **Theme本地化文件路径** _~/Themes/&lt;theme-name&gt;/App\_Data/Localization/&lt;culture-code&gt;/orchard.theme.po_
* **Root本地化文件路径** _~/App\_Data/Localization/&lt;culture-code&gt;/orchard.root.po_
* **Tenant本地化文件路径** _~/App\_Data/Sites/&lt;tenant name&gt;/Localization/&lt;culture-code&gt;/orchard.po_

## 翻译可用性

你可以从[http://orchardproject.net/localization][005] 下载其他语言的 _.po_ 文件。翻译内容由社区维护。如果你没有找到你需要的支持语言，你可以考虑自己贡献它。这是个几个小时的事，但有利于整个社区。

## 贡献新的翻译

### 利用纯文本编辑器工作

 [https://crowdin.net/project/orchard-cms][003] 本地化工具为特定语言提供了文件存根。Orchard翻译文件以po文件格式进行存储，你可以添加你自己的Orchard示例。那些语言包在每个小时开始时会重新生成（大概需要2-3分钟）。可以访问项目首页查看每一种语言的翻译进度。

以下两个链接都可以下载所有语言的翻译文件包：

* [Orchard CMS][006]
* [Orchard CMS Gallery][007]

你可以用文本编辑器编辑下载的 _.zip_ 压缩包中的 _.po_ 文件。当你编辑完成，请发送邮件至<join-orchard-localization@lists.outercurve.org> 订阅我们的本地化邮件列表，然后将 *.po* 文件打包为 zip压缩包发送至<join-orchard-localization@lists.outercurve.org>。

请确保 *.po* 文件以UTF-8-BOM格式编码保存。这通常会需要在你的文本编辑器中配置（如：在Notepad，你需要在“Save As”对话框 中的编码下拉框中修改对应的编码）。

#### 翻译文件的格式

下面截图展示了翻译文件的格式。每一个文本都是由下表元素来表示。

描述|使用元素
----------------------- | ---------------------
相关引用 | `#: reference-string`
ID,通常是原始（未翻译的）字符串。一旦ID值设置好后，就算英文字符串修改，这个值也不应该修改。这样尽管它们没有立即更新，但可以保证当前翻译仍然可以工作。 | `#| msgid "id-string"`
当前的英文参考。有助于翻译。 | `msgid "English-string"`
翻译的字符串。 | `msgstr "translated-string"`

![][105]

### 怎样提供贡献

- 在 [Crowdin][002] 网站上注册账户。
- 去 [Orchard CMS][003] 与 [Orchard CMS Gallery][008] 项目页申请加入项目。
- 你的申请很快就会批准，然后你将以你所选语言的“校对员”身份被添加到对应项目。这意味着你可以编辑和校对翻译内容（这是将翻译好的字符串添加到下载包里所必需的操作）。
- 如果你是Orchard项目新加入的成员，请与其他同语言的翻译者联系，确保你们遵循的是同一个规则。


#### 资源字符串引用

在 _.po_ 文件中资源引用字符串是可选的 —— (`reference-string`的信息在上面已经描述过)。如果没有定义引用，它将作为所有具有相同ID资源的备用 —— 如果一个具有相同ID的资源没有找到引用，那么它就取此资源的值。这在创建通用资源字符串（即字符串在多个地方使用且字符串是上下文无关的）时会很有用。这样你可以在需要的时候，随时覆盖通用的备用资源。

引用字符串可以存储在不同的地方，这取决于如何在应用中使用这个字符串：—— *？个人没怎么搞懂 - 待进一步研究？*

* **Strings from views**: 使用视图的虚拟路径——从应用的根目录开始（如：_~/Themes/TheThemeMachine/Views/User.cshtml_）。
* **Strings from _.cs_ files**: 使用完整的（含有命名空间）类名来找到对应的字符串（例如：`Orchard.Packaging.AdminMenu`）。
* **Strings from module manifests or theme manifests**: 使用清单文件的虚拟路径——从应用的根目录开始（如：_~Themes/TheThemeMachine/Theme.txt_）。 注意：模块和主题的清单本地化使用路径作为字段的键。例如，Author字段使用键“”“Author”，Gallery功能的Description字段可能使用键值“Gallery Description”。


### 为第三方模块提供贡献

我们的本地化基础建设是提供托管第三方应用翻译的。如果你是一个模块的作者（开发者）或者你想为一个模块贡献翻译内容，你可以使用 [Translation Manager][009] 模块来生成po格式文件。

在Orchard的命令行工具中输入以下命令（以Bing.Maps模块为例）：
    
    extract default translation /Extensions:Bing.Maps /Output:\temp

此操作将会创建一个包含模块字符串的 Orchard.en-us.po.zip 文件。命令将会遍历模块的源代码，然后创建所有需要被本地化处理的字符串条目——包括T方法包装的字符串，清单里的字符等。

然后请将此文件发送至 <join-orchard-localization@lists.outercurve.org> ，这样我们可以将它添加到在线的本地化处理数据库中。

# 数据库驱动内容项的本地化处理

除了应用程序和模块本地化，Orchard提供使用数据库存储翻译内容项的功能。要本地化内容项，需要启用 **Localization** 功能。。在控制面板中，点击 **模块-Modules**，然后在 **功能-Features** 标签中可以看到 **Localization**。点击 **启用-Enable** 链接。 

![][106]

默认情况下，**Page** 和 **Blog Post** 两种内容类型都是可以本地化的，因为他们都包含 **Localization** 部分。你可以将 **Localization** 部分添加到其他需要翻译的内容类型中。在控制面板中，点击 **内容-Content** ，然后将可以在**管理内容-Manage Content** 界面查看内容项。注意：**+新建翻译 —— + New Translation** 链接是针对每一个内容项的。

> 注：在新版中**Localization**模块的名称为**Content Localization**。同时要出现 **+新建翻译** 链接，你的网站首先需要配置多个支持语言。

![][107]

点击 **+ New Translation** 链接允许你定义内容项的翻译版本，并可以关联上相应的“父”级内容项（网站默认语言）。每一个翻译的内容项都是一个独立的内容项存储在系统中。在 **翻译内容-Translate Content** 编辑界面，你可以定义内容项要使用的语言代码。永久链接内容会根据选择的语言切换对应的链接地址以此保证每个翻译都独立存在。然后，你就可以将内容翻译为选定语言。

![][108]

在页面的主体部分添加一些翻译内容，然后点击 **保存-Save**。在内容项保存后，当前语言代码将会显示相应的不同语言的内容项链接。

当在网站上浏览内容项时，如果他又相应的翻译内容，翻译内容项的链接将会一起显示。这样对于你网站的访问者而言，他就比较方便的切换到其他语言。下图是浏览英文内容的示例：

![][109]

点击语言链接查看相应的翻译版本。当你其他语言版本时，原始语言页面的链接将会显示出来。

![][110]

要为自定义内容类型启用本地化功能，则添加 **Localization** 部分到内容类型中。例如：为一个名叫**MyEvent**的自定义类型添加本地化功能，在控制面板中，点击 **内容定义** ，然后在 **内容类型-Content Types** 标签中，点击 **MyEvent** 类型的 **编辑** 链接 (示例假设此自定义类型已经存在)。然后点击 **添加元件-Add** ，然后在显示的添加元件界面，选择 **Localization** 或者要添加的其他元件

![][111]

关于创建自定义内容类型的更多内容见：[原文：Creating Custom Content Types][010]。

> **注意** 本地化功能是仍在处理的工作，所以在Orchard应用中，不是所有的内容都已支持本地化。例如：Orchard还不支持通过给定Culture（浏览器默认Culture）自动筛选显示指定语言版本。我们会在以后的版本中解决这个问题。在此期间，你可以自己提供模块来实现`ICultureSelector`。如果你有什么关于本地化支持的内容要反馈给我们（如：帮助我们了解哪些场景对于你网站是比较重要的），请联系 <join-orchard-localization@lists.outercurve.org> ，并给我们发送相关信息。

# 翻译 Html 部件

> **注** 以下步骤适用于全新安装的默认主题'The Theme Machine'

在控制面板中，首先点击 **模块-Modules** ，然后确认 **Localization** 模块已经安装并已启用。下一步点击 **内容定义** ，定位到 **内容类型-Content Types** 标签页面，然后点击 **Html Widget** 后的**编辑**。我们的目的是翻译Html部件，点击 **添加元件**，然后选择 **Localization** 元件并点击 **保存-Save** 来添加元件。最后在内容类型编辑页面，点击最下面的 **保存-Save** 来保存内容项的改变。

现在在控制面板中点击 **设置-Settings** 菜单项。在 **网站默认语言-Default Site Culture** 中，你可以添加你想支持的语言。在此案例中，我们使用nl-BE 和 en-US。点击 **保存-Save** 应用语言设置。

点击 **部件-Widgets** 菜单项。
在 **Default** 层找到一个示例区域，如 **FooterQuadThrid** ，然后点击 **Add** 添加部件。
现在你需要选择一个部件，选择 **Html Widget** —— 之前配置的部件。
然后，输入必须的项（标题和内容）并点击 **保存-Save**。 
现在你的**Html Widget**已经添加到**FooterQuadThird**区域。
接下来准备翻译，选择新添加的部件编辑。在编辑页面顶部找到 **+添加翻译 —— + New translation**链接。点击它来添加其他语言的翻译。


***
译：[奇葩史][000]