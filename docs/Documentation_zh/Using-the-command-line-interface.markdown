<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Using-the-command-line-interface/

<!--图片链接集合-->
[101]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/orchard_cmd_line.png
[102]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/help_commands_initial.png
[103]: http://docs.orchardproject.net/en/latest/Upload/screenshots_675/setup_cmd.png

[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Using the Command-Line Interface][001]

Orchard提供命令行接口——用于执行处理许多控制面板中可用的功能（某些不是）。命令行工具叫**orchard.exe**，位于网站根目录下的bin文件夹下。要运行命令行工具，首先要在网站根目录（例如：Orchard.Web）下打开命令提示符窗口。打开方式为：在资源管理器中打开到对应文件夹，按住shift键，同时鼠标右键，然后选择**在此处打开命令窗口**。最后，在当前命令窗口中输入`bin\orchard.exe`。脊注意：你需要在网站根目录下运行orchard命令行工具。

# 命令使用 

![][101]

要查看可用的命令列表，在提示符框中输入`help commands`：

![][102]

如果你在网站初始安装配置之前运行Orchard.exe，它仅仅提供安装设置命令。它执行的内容其实和你在浏览器中运行Orchard并完成设置表单的结果是一样的——其中有：输入网站名称，管理用户名，密码以及数据库选项。另外，安装设置命令还有一个可选参数——一个在安装期间需要启用的功能列表。

![][103]

在运行完安装命令后，你可以再次输入`help commands`查看到更多的命令：   
    
    orchard> help commands
    可用命令列表：
    ---------------------------
    
    blog create /Slug:<slug> /Title:<title> /Owner:<username> [/MenuText:<menu text>]
            Creates a new Blog
    
    blog import /Slug:<slug> /FeedUrl:<feed url> /Owner:<username>
            Import all items from <feed url> into the blog at the specified <slug>
    
    cultures get site culture
            Get culture for the site
    
    cultures list
            List site cultures
    
    cultures set site culture <culture-name>
            Set culture for the site
    
    feature disable <feature-name-1> ... <feature-name-n>
            Disable one or more features
    
    feature enable <feature-name-1> ... <feature-name-n>
            Enable one or more features
    
    feature list [/Summary:true|false]
            Display list of available features
    
    help <command>
            Display help text for <command>
    
    help commands
            Display help text for all available commands
    
    package create <extensionName> <path>
        Create a package for the extension <extensionName>
        (an extension being a module or a theme).
        The package will be output at the <path> specified.
        The default filename is Orchard.[Module|Theme].<extensionName>.<extensionVersion>.nupkg.
        For example, "package create SampleModule c:\temp" will create the package
        "c:\temp\Orchard.Module.SampleModule.1.0.0.nupkg".
    
    package install <packageId> <location> /Version:<version>
            Install a module or a theme from a package file.
    
    package uninstall <packageId>
        Uninstall a module or a theme.
        The <packageId> should take the format Orchard.[Module|Theme].<extensionName>.
        For example, "package uninstall Orchard.Module.SampleModule" will uninstall the Module under the "~/Modules/SampleModule" directory and
        "package uninstall Orchard.Theme.SampleTheme" will uninstall the Theme under the "~/Themes/SampleTheme" directory.
    
    user create /UserName:<username> /Password:<password> /Email:<email>
            Creates a new User



可用命令取决于你的网站当前启用了多少功能模块。要查看可以启用或禁用的功能列表，输入命令`feature list`或`feature list /Summary:true`。你可用在命令提示符中输入命令`feature enable <feature-name>`来启用额外的功能。

    
    orchard> feature list /Summary:true
    Common, Enabled
    Containers, Enabled
    Contents, Enabled
    Dashboard, Enabled
    DatabaseUpdate, Disabled
    Feeds, Enabled
    Gallery, Enabled
    HomePage, Enabled
    Lucene, Disabled
    Navigation, Enabled
    Orchard.ArchiveLater, Disabled
    Orchard.Blogs, Enabled
    Orchard.Blogs.RemotePublishing, Disabled
    Orchard.CodeGeneration, Enabled
    Orchard.Comments, Enabled
    Orchard.ContentTypes, Enabled
    Orchard.Email, Disabled
    Orchard.Experimental, Disabled
    Orchard.Experimental.TestingLists, Disabled
    Orchard.Experimental.WebCommandLine, Disabled
    Orchard.Indexing, Disabled
    Orchard.jQuery, Enabled
    Orchard.Lists, Enabled
    Orchard.Localization, Disabled
    Orchard.Media, Enabled
    Orchard.Messaging, Disabled
    Orchard.Migrations, Disabled
    Orchard.Modules, Enabled
    Orchard.MultiTenancy, Disabled
    Orchard.Packaging, Enabled
    Orchard.Pages, Enabled
    Orchard.PublishLater, Enabled
    Orchard.Roles, Enabled
    Orchard.Scripting, Enabled
    Orchard.Scripting.Dlr, Disabled
    Orchard.Scripting.Lightweight, Enabled
    Orchard.Search, Disabled
    Orchard.Setup, Disabled
    Orchard.Tags, Enabled
    Orchard.Themes, Enabled
    Orchard.Users, Enabled
    Orchard.Widgets, Enabled
    PackagingServices, Enabled
    Profiling, Disabled
    Reports, Enabled
    Routable, Enabled
    SafeMode, Disabled
    Scheduling, Enabled
    Settings, Enabled
    Shapes, Enabled
    TheAdmin, Disabled
    TheThemeMachine, Enabled
    TinyMce, Enabled
    XmlRpc, Disabled


# 批处理或脚本命令

orchard命令执行中有两种具体的非交互模式：单条命令和使用文件处理。每一个都允许在非交互的上下文中使用批处理命令。
命令仍然需要被启用，并需要在正确的位置启动每个命令类型。

## 单条命令

正如所料，单条命令可以运行，并在orchard.exe工具执行完成后直接退出。

在Orchard.Web/bin路径下执行：
    
    orchard package create "Orchard.Blogs" "c:\\temp\\"

## 使用文件处理

响应文件包含一些列的命令行——每一行表示一个要执行的命令。这在执行大量命令时，是一个很好的办法，它避免你在orchard上下文初始化时一步一步的输入。

例如响应文件内容如下(myfile.txt):

    package create "Orchard.Blogs" "c:\\temp\\"
    package create "Orchard.Users" "c:\\temp\\"
    
然后在orchard.exe中输入一条命令执行响应文件，注意参数前缀"@"——用于表示参数是一个响应文件。

    orchard @myfile.txt

# 添加命令

模块开发者可以继承`Orchard.Commands.DefaultOrchardCommandHandler`类来将自己的命令添加到系统中。命令在那个类里仅仅是一个带有CommandName特性的方法。以下代码创建了一个名为"hello world"的命令，它包含：一个name参数以及一个可选的"YouRock"转换器。
    
    [CommandName("hello world")]
    [CommandHelp(@"hello world <name> [/YouRock:true|false]
    Says hello and whether you rock or not.")]
    [OrchardSwitches("YouRock")]
    public void HelloWorld(string name) {
        Context.Output.WriteLine(T("Hello {0}.", name ?? "world"));
        Context.Output.WriteLine(YouRock ? "You rock." : "You do not rock.");
    }

转换器要在类中单独声明一个属性：

    [OrchardSwitch]
    public bool YouRock { get; set; }

命令可以运行在整个Orchard环境中，它可以查询数据库、注入依赖项，并且，一般情况下，在网站中通过执行命令行可以完成几乎所有事情。

## 命令异常抛出

在命令处理中抛出异常时不建议的。取而代之的是，在任何时候，如果可以，将上下文输出并返回。如果你想要抛出一个特定的异常，请抛出OrchardException类型异常。
    
***
译：[奇葩史][000]