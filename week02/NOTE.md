# Week02-编程语言通识



### 按语法分类

* 非形式语言

  中文、英文

* 形式语言（乔姆斯基谱系）

  * 0 型 无限制文法
    * `?::=?`，如 `<a><b> ::= "c"`
  * 1 型 上下文相关文法
    * `?<A>?::=?<B>?`，如`"a"<b>"c"::="a""x""c"`
  * 2 型 上下文无关文法
    * `<A>::=?`
    * JS，大部分情况下是上下文无关
  * 3 型 正则文法
    * `<A>::=<A>? `✅
    * `<A>::=?<A>` ❌
    * 限制表达能力



### 产生式（BNF）

* 用尖括号括起来的名称来表示语法结构名
* 语法结构分成基础结构和需要用其他语法结构定义的复合结构
  * 基础结构称终结符
  * 复合结构称非终结符
* 引号和中间的字符表示终结符
* 可以有括号
* `*` 表示重复多次
* `|` 表示或
* `+` 表示只少一次

```html
"a"
"b"

<Program>:= (<Program> "a"+ | <Program> "b"+)+

整数加

// 十进制整数
<Number> = "0" | "1" | "2" | ... | "9"
<DecimalNumber> = "0" | (("1" | "2" | ... | "9") <Number>*)

// + 、连 +
<AdditiveExpression> = <DecimalNumber> | 
											 <AdditiveExpression> "+" <DecimalNumber>

// *、连 *
<MultiplicativeExpression> = <DecimalNumber> | 
														 <MultiplicativeExpression> "*" <DecimalNumber>

// 逻辑
<LogicalExpression> = <AdditiveExpression> |
											<LogicalExpression> "||" <AdditiveExpression> |
											<LogicalExpression> "&&" <AdditiveExpression>
	
	
=> 进而

// * /
<MultiplicativeExpression> = <DecimalNumber> | 
														 <MultiplicativeExpression> "*" <DecimalNumber> |
														 <MultiplicativeExpression> "/" <DecimalNumber>
														 
// + - * /
<AdditiveExpression> = <MultiplicativeExpression> | 
											 <AdditiveExpression> "+" <MultiplicativeExpression>
											 <AdditiveExpression> "-" <MultiplicativeExpression>

// logic
<LogicalExpression> = <AdditiveExpression> |
											<LogicalExpression> "||" <AdditiveExpression> |
											<LogicalExpression> "&&" <AdditiveExpression>
											
											
// 括号
<PrimaryExpression> = <DecimalNumber> | "(" <LogicalExpression> ")"
  
=> 进而

// * /
<MultiplicativeExpression> = <PrimaryExpression> | 
														 <MultiplicativeExpression> "*" <PrimaryExpression> |
														 <MultiplicativeExpression> "/" <PrimaryExpression>
```



* JS 并不使用 BNF，但原理类似



### 现代语言特例

* C++ 中，* 可能表示乘号或者指针，具体指哪个，取决于星号前面的标识符是否被声明为类型
* VB 中，< 可能是小于号，也可能是 XML 直接量的开始，取决于当前位置是否可以接受 XML 直接量
* Python 中，首行的 tab 符和空格会根据上一行的行首空白以一定规则被处理成虚拟终结符 indent 或者 dedent
* JavaScript 中， / 可能是除号，也可能是正则表达式开头，处理方式类似于 VB，字符串模版中也需要特殊处理，in蛋还有自动插入分号规则

### [图灵完备性](https://zh.wikipedia.org/wiki/%E5%9C%96%E9%9D%88%E5%AE%8C%E5%82%99%E6%80%A7)

* 命令式 -- 图灵机
  * goto
  * if 和 while
* 声明式 -- lambda
  * 递归

### 动态与静态

* 动态
  * 在用户的设备/在线服务器上
  * 产品实际运行时
  * Runtime
* 静态
  * 在程序员的设备上
  * 产品开发时
  * Complietime

### 类型系统

* 动态类型系统与静态类型系统

* 强类型与弱类型

  * String + Number
  * String == Boolean
  * C++ 是弱类型，有隐式转换的为弱类型？

* 复合类型

  * 结构体
  * 函数签名（T1, T2） => T3

* 子类型

  * 逆变

    如凡是能用 FUnction<Child> 的地方，都能用 Function<Parent>

  * 协遍

    如凡是能用 Array<Parent> 的地方，都能用 Array<Child>

>  设计一门语言首先需考虑以上几点



### 一般命令式编程语言

* Atom

  * Identifier
  * Literal

* Expression

  * Atom
  * Operator
  * Punctuator

* Statement

  * Expression
  * Keywork
  * Punctuator

* Structure

  * Function
  * Class
  * Process
  * Namespace

* Program

  * Program
  * Module
  * Package
  * Library

  > JS 有 Program 和 Module



### UTF-8 编码过程

* UTF-8是Unicode的超集
* UTF-8 最多占 6 个字节

对于一个str，编码过程如下：

1. 查看 char 对应二进制

   ```
   var code = "中".charCodeAt(0);
   // 100111000101101
   // 不足 8 位前面补 0
   // => 01001110 00101101
   ```

2. 根据二进制码对应范围，进行补码

   * 补位码第一个字节前面有几个1就表示整个UTF-8编码占多少个字节
   * 判断落在哪个区间

   ![image-20200503232214758](/Users/gangwang/Library/Mobile Documents/com~apple~CloudDocs/notes/前端/重学前端/2-编程语言通识/image-20200503232214758.png)

   该值落在第三行，使用三个字节编码方式，从前向后进行补位 1110xxxx 10xxxxxx 10xxxxxx

   => 11100100 10111000 10101101

3. 转成 16 进制数

   0xE4 0xB8 0xAD