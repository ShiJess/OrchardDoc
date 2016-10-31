<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Creating-global-ready-applications/
[002]: https://crowdin.net/
[003]: https://crowdin.net/project/orchard-cms
[004]: http://gallery.orchardproject.net/List/Modules/Orchard.Module.Vandelay.Industries
[005]: http://orchardproject.net/localization
[006]: https://crowdin.net/download/project/orchard-cms.zip
[007]: https://crowdin.net/download/project/orchard-cms-gallery.zip

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots/add_cultures_settings.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots/Culture_available.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots/Culture_newdefault.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/default_site_culture_fr_675.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/fr_po_file.png


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

### How to contribute

- Register on [Crowdin](https://crowdin.com/).
- Go to the project page of [Orchard CMS](https://crowdin.net/project/orchard-cms) and [Orchard CMS Gallery](https://crowdin.net/download/project/orchard-cms-gallery.zip) and apply to join the project.
- Your application will be accepted shortly and you'll be added to the project as "Proofreader" for the selected languages. This means that you'll be able to edit and approve translations (which is necessary for the translated strings to be included in the downloadable packages).
- If you are new to the Orchard translations, please consult with other translators of the same language and make sure you follow the same conventions.


#### Resource String Reference

The reference for a resource string in a _.po_ file (the `reference-string` value described in the previous section) is optional. If no reference is specified, the resource string will be used as a fallback whenever a resource with the same ID is queried with a reference that can't be found. This is a useful way to create generic resource strings that are used in multiple places in the application and are not context-sensitive. You can always override a generic fallback like this as needed.

The reference strings can be stored in different locations, depending on how the string is used in the application:

* **Strings from views**:  Use the virtual path of the view from the root of the application (for example, _~/Themes/TheThemeMachine/Views/User.cshtml_).
* **Strings from _.cs_ files**:  Use the fully qualified type name of the class where the string is being used (for example, `Orchard.Packaging.AdminMenu`).
* **Strings from module manifests or theme manifests**:  Use the virtual path of the manifest from the root of the application (for example, _~Themes/TheThemeMachine/Theme.txt_). Note that module and theme manifest localization uses a path for fields as the key. For example, the Author field uses the key "Author" and the Description field of the Gallery feature would be under the key "Gallery Description".


### Contributing files for third party modules

Our localization infrastructure is built to host translations for third party modules. If you are the author of a module or want to contribute translations for a module, you can generate po files for it using the [Translation Manager](http://gallery.orchardproject.net/List/Modules/Orchard.Module.Vandelay.Industries) module.

From an Orchard command line, type the following command (for the example of the Bing.Maps module):

    
    extract default translation /Extensions:Bing.Maps /Output:\temp


This will create a new Orchard.en-us.po.zip file with the strings for the module. The command looks at the source code for the module and creates entries for T-wrapped strings, manifest strings and everything that should be localizable.

Please send this file to <join-orchard-localization@lists.outercurve.org> so that we can add it to the online localization database.

# Localizing Database-Driven Content Items

In addition to application and module localization, Orchard provides the ability to translate content items that are stored in the database. To localize content items, you must enable the **Localization** feature. In the dashboard, click **Modules**, and then on the **Features** tab you will see **Localization**. Click the **Enable** link. 

![](../Upload/screenshots_675/Localize_enable_675.png)

By default, both the **Page** and **Blog Post** content types are localizable, because they both contain the **Localization** part. You can add the **Localization** part to other content types that need translation. Click **Content** on the dashboard, and then view the items in the **Manage Content** screen. Notice the **+ New Translation** link for each content item.

![](../Upload/screenshots_675/new_translation_675.png)

> **Note** This link appears only if you have more than one culture enabled on the site (see previous section), and if you have enabled the **Localization** feature.

Clicking the **+ New Translation** link allows you to define a translated version of the content item to be associated with the "parent" content item (in the site's default culture). Each translated content item is treated as a unique content item in the system. On the **Translate Content** editor screen, you can define the culture code for the content item.  The permalink will change accordingly in order to ensure that URLs are unqiue for each translation. You can then translate the content item from the default site culture to the selected culture.

![](../Upload/screenshots_675/Localize_content_675.png)

Add some translation text in the body of the page, and then click **Save**. After the content item is saved, the current culture code is indicated, along with links to any related content items in different cultures.

When you browse content items on the site, if there are translations available for a content item, links to those content items will be displayed. This makes it easy for your site visitors to switch between translations of the item.  This is what the site looks like when you view the English (en-US) item:

![](../Upload/screenshots_675/Localize_en_downloadpg_675.png)

Click the culture code link to see translated version of the page. When you do, the original cultural code (en-US) appears as a link to the original page.

![](../Upload/screenshots_675/Localize_fr_downloadpg_675.png)

To enable localization for custom content types, add the **Localization** part to the content type. For example, to add localization to a custom content type named **MyEvent**, click **Content** on the dashboard, and then click the **Content Types** tab.  Click **Edit** on the **MyEvent** type (this example assumes the custom type already exists).  Click **Add** in the **Parts** section of the type.  The **Add** screen is displayed, and you can select **Localization** or other parts to add.

![](../Upload/screenshots/add_localization_part_MyEvent.png)

For more information about creating and working with custom content types, refer to the [Creating Custom Content Types](Creating-custom-content-types) topic.

> **Note** The localization feature is a work in progress, and not all parts of the Orchard application are yet localizable. For example, Orchard does not yet provide an automatic way to filter and display only content items in a given culture (one instance of this is the browser's default culture). We will address this in a future release. In the meantime you can provide your own implementation of `ICultureSelector` in a module. If you want to give us feedback on localization support in Orchard (for example, to help us understand the scenarios that are important for your site), please contact at <join-orchard-localization@lists.outercurve.org> and drop us a line!

# Translating an Html Widget

> **Note** these steps apply to a clean installation using the default theme 'The Theme Machine'

In the admin panel, navigate to **Modules** and verify that you have the **Localization** module installed and enabled. The next step is to navigate to **Content** in the admin panel. Select the **Content Types** tab page on top and click **Edit** to adjust the **Html Widget**. Our goal is to translate a Html Widget. Click **Add Parts** in the Parts section. Here we select the **Localization** part and click **Save** to add this part. At the bottom of the page click **Save** again to save your Content Item adjustments.

Now we need to navigate to the **Settings** menu item in the admin panel. Under the section **Default Site Culture** you can add the cultures that you want to support. In our case we have nl-BE and en-US. Click **Save** to apply your culture settings.

Navigate to the **Widgets** menu item.
On the **Default** layer find for example the **FooterQuadThrid** section and click **Add** to add a Widget.
Now you need to **Choose A Widget**, select the **Html Widget**, because this is the one that we adjust.
Now fill in the needed information (Title and Content) and click **Save**. 
Your Html Widget is now added to the FooterQuadThird section.
Now we are ready to translate the item. Select you newly added widget to edit it. On top of the **Edit Widget** page you will find the following text: **+ New translation**. Click this to add the translation for another culture.



***
译：[奇葩史][000]