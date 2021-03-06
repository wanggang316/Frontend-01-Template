# Week01-构建知识体系

## HTML

![20190418114107685](./NOTE.assets/20190418114107685.jpg)

SGML 定义电子文档和内容描述的标准。DTD 标准是SGML 的一部分

XML 是SGML 的子集，优化版

   HTML 是遵循了 DTD 标准的 SGML 的文档，也可以说是 SGML 的一个实例

   XHTML 是遵循了XML标准的 HTML 文档。

   HTML5 是HTML最新的HTML标准。但不基于SGML，所以不遵循 DTD 标准

### HTML

HTML（Hyper Text Mark-up Language）即超文本标记语言或超文本链接标示语言，是目前网络上应用最为广泛的语言，也是构成网页文档的主要语言。它告诉浏览器如何显示内容。

### SGML

SGML（Standard Generalized Markup language 即标准通用标记语言）

SGML 是国际上定义电子文档和内容描述的标准。源于 1969 年的 IBM 开发的 GML，GML 主要用来解决不同系统中文档格式不同的问题。经过多年发展，1986 年经 ISO 批准为国际标准 ISO8897，成为 SGML。

制定 SGML 的基本思想是把文档的内容与样式分开。在 SGML 中，标记分为两种：一种用来描述文档显示的样式，成为**程序标记**；另一种用来描述文档中语句的用途，称为**描述标记**。

一个 SGML 文件通常分三个层次：结构、内容和样式。

##### 结构

HTML 可以说是 SGML 结构里面的一个实例。

为了描述文档的结构，**SGML 定义了一个称为 “文档类型定义（Document Type Definition，DTD）” 的文件**。它为组织文档的文档元素（如章和章标题，节和主题等）提供了一个框架。此外，DTD还未文档元素之间的互相关系制定了规则。例如，“章的标题必须是在章开始之后的第一个文档元素”，“每个列表至少要有两个项目” 等。DTD 定义的这些规则可以确保文档的一致性。

##### 内容

这里指的就是信息本身。内容包括信息名称（标题）、段落、项目列表和表格中的具体内容，具体的图形和声音等。确定内容在 DTD 结构中的伪统治的方法称为 “加标签（tagging）”，而创建 SGML 文档实际上就是围绕内容插入响应的标签。这些标签就是给结构中的每一部分的开始和结束做标记。

#### Entity

HTML Entity 是一段以 “＆” 符号开头，以 “;” 符号结尾，能够表示 Unicode 符号的字符串文本。 用途 

1.显示 HTML 保留字符，如 &lt;、&gt;、&amp;、 &#34; 等（联想到防御 XSS 攻击）； 

2.表示难以用常规输入设备输入的字符，如 ©、®、± 等； 

3.表示给定的字符编码可能无法表达文档字符集的其他字符，如 ASCII 编码想想显示中文，使用 &amp;#x6C34; 表示 “水”。常用的&amp;nbsp;（空格）也是Entity。

### XML

XML（Extension Markup Language）是可扩展标记语言。**XML 用于描绘封装数据，而 HTML 超文本标记语言用于展示数据**

xmlns

```
<html xmlns="http://www.w3.org/1999/xhtml">

...
```

### XHTML

XHTML（Extensible HyperText Markup Language），目标是取代 HTML。

XHTML 就是用 XML 规范的 HTML，由于 XML 语法严格，因此，XHTML 要求：

* 元素被正确嵌套

* 必须有关闭标签

* 必须小谢

* 属性必须有值切用双引号，用 id 代替 name

  

### SGML、XML、HTML、XHTML 关系

* HTML是SGML的一个实例，它的DTD作为标准被固定下来
* XML 被设计用来传输和存储数据，其焦点是数据的内容。HTML 超文本标记语言被设计用来显示数据，其焦点是数据的外观

* SGML 是 XML 的前身，由于 SGML 难理解和浏览器支持差等原因被废弃，**XML 和 HTML 都是基于 SGML**。SGML 的 DTD 作为标准被固定下来。也就是说，DTD 标准是 SGML 的一部分。所以 HTML 4.0.1 基于 SGML，需要对 DTD 进行引用，才能告知浏览器文档所使用的文档类型。
* XML 是 SGML 的一个子集，比 SGML 要简单，但是能实现 SGML 的大部分功能。



### HTML5

HTML5 没有使用 SGML 或者 XHTML，它是一个全新的东西，因此你不需要参考 DTD，对于 HTML5，你仅需要放置下面的文档类型代码告诉浏览器识别这是 HTML5 文档。

```html
<! DOCTYPE html>
```

### ARIA

https://www.w3.org/TR/html-aria/

-----

* https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-262.pdf

* https://www.w3school.com.cn/html/html_entities.asp

* https://www.w3.org/1999/xhtml/

* https://html.spec.whatwg.org/multipage/

* https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element

* ARIA：Accessible Rich Internet Applications（[ https://www.w3.org/TR/html-aria/）](https://www.w3.org/TR/html-aria/）)

* 查看 https://html.spec.whatwg.org/multipage/semantics.html#the-html-element 下 html 所有 tag

  ```javascript
  Array.prototype.map.call($0.querySelectorAll(‘code’), e => e.innerText).join(’\n’)
  ```

  

