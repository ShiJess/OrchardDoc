<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Adding-and-managing-media-content/
[002]: http://openlivewriter.org/
[003]: http://www.microsoft.com/web/downloads/platform.aspx


<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/manage_media_675.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots/edit_media_1.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/manage_media_folders_675.png
[104]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/manage_folders_add_subfolder_675.png
[105]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/add_media_1_675.png
[106]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/upload_zip_media_675.png
[107]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/upload_zip_media_2_675.png
[108]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/upload_zip_media_3_675.png


[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Adding and Managing Media Content][001]  
> *注：此文内容相对较老，实际操作指导性不强，仅适合做研究*

当你利用富文本编辑器上传图片时（或者使用XML-RPC客户端，例如  [Open Live Writer][002]——*官网给出的为Windows Live Writer，且链接已失效*），图片将保存在Orchard网站的根目录下的 _Media_ 文件夹。
_Media_ 文件夹必须为可写的（针对网站托管的用户进程），这样才能保证图片可以成功上传。
如果你使用 [Web Platform Installer][003] 安装Orchard，_Media_ 文件夹会自动配置写权限。

要添加或删除媒体文件夹，点击控制面板中的 **Media** 即可。 

![][101]

浏览选择媒体中的一个图片文件，查看其详细信息。媒体文件主要有以下属性：——*最新版本有所不同*

* **缩略图 Screenshot**. 针对图片文件的缩略浏览
* **尺寸 Size** 和 **添加时间 Added on**. 媒体文件属性
* **嵌入 Embed**. 媒体文件的链接地址，你可以直接拷贝到富文本编辑器中的HTML源代码编辑框中，以此插入媒体图片到内容中。
* **文件名 Name**. 媒体文件名称

![][102]

在控制面板中点击**Media**，进入媒体文件夹（含子文件夹）管理。点击对应的文件夹进入相应的文件夹管理界面 

![][103]

当前界面中提供了添加或删除媒体文件以及创建子文件夹功能选项。

点击 **Add a folder** 创建子文件夹。

为子文件夹命名（如：命名子文件夹为“Pictures”）并保存。   

![][104]

进入新建的子文件夹并点击 **Add media**.

![][105]

Orchard提供单个媒体文件上传或者上传包含多个图片文件的_zip_压缩包。
如果你有大量图片文件需要上传，将它们压缩为_zip_包文件，然后仅上传_zip_压缩包，这要比一张一张图片上传要有效的多。 

为了看这是怎么工作的，在你本机上创建一个包含多张图片的_zip_压缩包，然后点击 **Upload**。 **Extract zip** 勾选框默认是选中的，这样我们上传_zip_压缩包就会被解压添加到文件夹中。

![][106]

上传解压后的图片会显示在其父文件夹下

![][107]

点击对应图片进行查看或编辑。 

![][108]

***
译：[奇葩史][000]