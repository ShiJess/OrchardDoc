<!--链接集合-->
<!--URL域 http://docs.orchardproject.net/en/latest -->
[000]: http://www.shisujie.com
[001]: http://docs.orchardproject.net/en/latest/Documentation/Using-the-localization-helpers/
[002]: http://www.shisujie.com/blog/Using-the-localization-helpers


[index]: http://www.shisujie.com/blog/OrchardIndex
> [返回目录索引][index]  
> 原文链接：[Using the Localization Providers][001]  
> 译文链接：[Orchard扩展——本地化提供程序使用][002]  

Orchard利用一个简单的API来支持本地化，其将输入的默认语言字符串（en-us）作为本地化数据的主键，然后返回当前语言环境最准确的本地化版本。

## 在Razor视图引擎(.cshtml)中使用T()

### 简单示例 —— 转化后的字符串将会返回输出

    @T("This was a triumph!")

简单字符串时使用上述内容。

### 格式化用户数据

有时，数据需要注入到本地化字符串中。

请勿使用字符串拼接，因为数据的位置在不同的语言中可能处于不同的位置：
    
    // 不好的用法:
    @T("You have ") + Model.SmsCredits + @T(" credits left.")

应该使用参数化格式字符串：
    
    // 推荐用法:
    @T("You have {0} credits left", Model.SmsCredits)

### 数据编码

请注意，参数应在添加之前进行编码。例如，如果以下示例的`noteText`中包含`<b>huge</b>`:
    
    @T("I'm writing a note here: {0}.", noteText)

这样，默认语言环境输出时，用户将看到标记：

    I'm writing a note here: <b>huge</b> success. 

在99%的情况下，这或许是你需要的。这种自动编码可以保护你免受黑客的注入攻击。 

但在极少数情况下，你对你所做的事很了解，并且希望注入未编码的字符串，这是你可以执行以下操作：
    
    @T("I'm writing a note here: {0}.", new HtmlString(noteText))

它的最终结果将是： 

"I'm writing a note here: <b>huge</b> success."
  
> 注意：实现IHtmlString类型的任何对象都将注入未编码，因为我们假设它已经正确编码。这就是使用`new HtmlString(noteText)`的功能。  
> 上述编码未编码比较拗口，未找到合适翻译，其实际表述就是：未编码 —— 将按原样显示，编码 —— 某些内容会进行转换。

例如，如果你进行如下处理：
    
    @T("{0}: We do what we must because {1}",
        Html.ItemDisplayLink(apertureScienceContentItem),
        justification)

这样，操作链接将不会编码，并且按预期显示，而justification字符串会编码。

还有需要注意的是，格式字符串本身是被认为安全的，因为它是由模块作者提供，所以下面内容将如预期的一样显示：

    @T("It's <em>hard</em> to overstate my <strong>{0}</strong>",
        emotion)

如果emotion中包含"&lt;satisfaction&gt;", 则其结果字符串为"It's <b>hard</b> to overstate my <b>&lt;satisfaction&gt;</b>".

### 注入没字符串值

基础值类型在格式化之前不是html编码的，并且当前的语言文化将会用于对它们进行格式化：
    
    @T("when {0} qty {1:#,##0.00} unit price {2:C}", _clock.UtcNow, 5.782, 87)

### 复数

资源字符串（如 `{0} comment` 或 `{0} comments`）的复数是比较棘手的，因为不同语言之间存在差异，其中包含复数的规则或者你需要多少字符串来应对所有情况。尽管Orchard尚未实现所有可能的情况，但其API已经准备在以后支持它们。

如果一个字符串需要进行复数处理，请为默认语言提供两个字符串，并将复数参数作为第一个格式化参数：

    @T.Plural("1 Comment", "{0} Comments", commentCount)
    @T.Plural("Deleted 1 item of type {1}", "Deleted {0} items of type {1}",
        deleteCount, contentType)

在单数字符串中使用`1`，以此可以为翻译者提供更好的上下文（如上所示）。

复数参数必须是整数。

不要再视图中使用自定义逻辑来决定字符串的内容，因为不同的文化下，其视图逻辑可能会不同。

## 通过代码使用T()

### 使用依赖 注入设置

你可以在代码（如驱动类、服务类以及其他类）中使用`T()`本地化辅助方法。

通过向你的类中添加公共属性，Orchard可以检测它，并利用Autofac的属性注入功能来使用当前的Localizer配置你的方法。

其过程如下：

1. 向你的类中添加公共属性：
  
        public Localizer T { get; set; }

技术上，你可以使用任何变量名，并不一定要用`T`作为属性名，但在此约定使用`T`。

2. 在构造函数中，为T属性赋一个默认值：
  
        protected YourClassName() {
        T = NullLocalizer.Instance;
        }
            
这是为了防止在Autofac配置好localizer之前，由于没有默认localizer而导致应用结束。

### 利用继承自接口IDependency的Component类来自动获取T()

Orchard中提供了一个抽象类——`Component`，它定义`Orchard.Framework`项目的`IDependency.cs`文件中:

    public abstract class Component : IDependency {
        protected Component() {
            Logger = NullLogger.Instance;
            T = NullLocalizer.Instance;
        }

        public ILogger Logger { get; set; }
        public Localizer T { get; set; }
    }
    
如果你的类实现了`IDependency`接口，那么你可以改为继承`Component`。这样，你的类就可以自动含有方法`T()`的声明和初始化。

### 在配置T()时使用它的属性

你可以再次查看上面的Razor示例来使用它。

唯一的不同是，当你通过代码使用localizer时，你不需要使用Razor的`@`符号来表示代码块的开始。

例如，在Razor中，示例如下：

    @T("You have {0} credits left", Model.SmsCredits)

而在代码中处理的示例如下：

    T("You have {0} credits left", Model.SmsCredits)

## 在ASPX视图引擎（.aspx）中使用T()

> 其使用方法几乎与Razor方式一样，只需将`@表达式`格式替换为`<%: 表达式 %>`格式。

如简单使用，将：

    @T("This was a triumph!")

替换为：

    <%: T("This was a triumph!") %>

其他复杂使用以此类推。

### 关于`<%= %>`与`<%: %>`

`<%: %>`适用于所有情况，因为它会自动处理编码。请勿使用`<%= %>`。如果你确实需要注入未编码的字符串，请使用HtmlString处理，同时继续使用`<%: %>`。


***
译：[奇葩史][000]