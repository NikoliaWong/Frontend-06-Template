学习笔记

# 泛用语言分类方法 
    语言按语法分类
    非形式语言：中文、英文
    形式语言（乔姆斯基谱系）

    乔姆斯基谱系：是计算机科学中刻画形式文法表达能力的一个分类谱系，是由诺姆·乔姆斯基于 1956 年提出的。它包括四个层次：
    0- 型文法（无限制文法或短语结构文法）包括所有的文法。
    1- 型文法（上下文相关文法）生成上下文相关语言。
    2- 型文法（上下文无关文法）生成上下文无关语言。
    3- 型文法（正规文法）生成正则语言。
    4种文法是上下包含关系。

# 产生式
    产生式： 在计算机中指 Tiger 编译器将源程序经过词法分析（Lexical Analysis）和语法分析（Syntax Analysis）后得到的一系列符合文法规则（Backus-Naur Form，BNF）的语句

    巴科斯诺尔范式：即巴科斯范式（英语：Backus Normal Form，缩写为 BNF）是一种用于表示上下文无关文法的语言，上下文无关文法描述了一类形式语言。
    它是由约翰·巴科斯（John Backus）和彼得·诺尔（Peter Naur）首先引入的用来描述计算机语言语法的符号集。

    终结符： 最终在代码中出现的字符（ https://zh.wikipedia.org/wiki/ 終結符與非終結符)

# 产生式(BNF)
    法则：
    ::=表示定义；
    “ ”双引号里的内容表示字符；
    <>尖括号里的内容表示必选内容；
    | 竖线两边的是可选内容，相当于or；

    1.用尖括号括起来的名称来表示语法结构名
    2.语法结构分成基础结构和需要用其他语法结构定义的复合结构
        基础结构称终结符
        复合结构称非终结符
    3.引号和中间的字符表示终结符
    4.可以有括号
    5.*表示重复多次
    6.|表示或
    7.+表示至少一次

    四则运算：1+2*3
    终结符：Number、+、-、*、/
    非终结符：MultipicativeExpression AdditiveExpression

    <MultiplicativeExpression>::=<Number>|  
        <MultiplicativeExpression>"*"<Number>|
        <MultiplicativeExpression>"/"<Number>|

    <AdditiveExpression>::= <MultiplicativeExpression>|
        <AdditiveExpression>"+"<MultiplicativeExpression>|<AdditiveExpression>"-"<MultiplicativeExpression>

# 乔姆斯基谱系：
    是计算机科学中刻画形式文法表达能力的一个分类谱系，是由诺姆·乔姆斯基于 1956 年提出的。它包括四个层次：

    0- 型文法（无限制文法或短语结构文法）包括所有的文法。
    1- 型文法（上下文相关文法）生成上下文相关语言。
    2- 型文法（上下文无关文法）生成上下文无关语言。
    3- 型文法（正规文法）生成正则语言。
    终结符： 最终在代码中出现的字符（ https://zh.wikipedia.org/wiki/ 終結符與非終結符)

# 通过产生式理解乔姆斯基谱系
- 0型 无限制文法
- `?::=?`
- 1型 上下文相关文法
    - `?<A>?::=?<B>?`
- 2型 上下文无关文法
    - `<A>::=?`
- 3型 正则文法
    - `<A>::=<A>?`
    - `<A>::=?<A>` 错误

JavaScript是什么语法？
大部分是上下文无关文法，符合正则表达式的是正则文法。

有两个特例:

```
2**1**2, 乘方
是右结合文法，
结果为2
正则文法是左结合。
```
```
{
    get a {return 1},
    get: 1
}
get a 代表属性，get:1 是直接赋值
```

严格上来说，JavaScript是上下文相关文法。

## 现代语言分类
- 形式语言——用途
    - 数据描述语言
    JSON、HTML、CSS、SQL、XAML、YAML
    - 编程语言
    C、C++、Java、C#、python、JavaScript、Ruby、Perl、Lisp、T-SQL、Clojure、Hask、PHP、Lua、SmallTalk、VB、Delphi、Dart
- 形式语言——表达方式
    - 声明式语言
    JSON、HTML、XAML、SQL、CSS、Lisp、Clojure、Haskell
    - 命令型语言
    C、C++、Java、C#、Python、Ruby、Perl、JavaScript、Dart

## 图灵完备性
- 命令式——图灵机
    - goto
    - if和while
- 声明式——lambda
    - 递归

## 动态与静态
- 动态
    - 在用户的设备/在线服务器上
    - 产品实际运行时
    - Runtime
- 静态
    - 在程序员的设备上
    - 产品开发时
    - Compiletime（编译时）

## 类型系统
- 动态类型系统（用户）与静态类型系统（程序员）
- 强类型与弱类型
    - String + Number
    - String == Boolean
- 复合类型
    - 结构体
    - 函数签名
- 子类型
- 泛型
    - 逆变/协变

## 一般命令式编程语言
- Atom
    - Indentifier
    - Literal
- Expression
    - Atom
    - Operator
    - Punctuator
- Statement
    - Expression
    - keyword
    - Punctuator
- Structure
    - Function
    - Class
    - Process
    - Namespace
- Program
    - Program
    - Module
    - Package
    - Library 

语法 -> 语义 -> 运行时

### Types
- Number
    - IEEE 754 Double Float
        - Sign(1) 符号位 表示正负（0/1）
        - Exponent(11) 指数位
        - Fraction(52) 精度位
    - Grammar
        - DecimalLiteral 十进制
            - 0
            - 0.
            - .2
            - 1e3
        - BinaryIntegerLiteral 二进制
            - 0b111
        - OctalIntegerLiteral 八进制
            - 0o10
        - HexIntegerLiteral 十六进制
            - OxFF

0.toString()
    Uncaught SyntaxError: Invalid or unexpected token
0 .toString()
    "0"
0..toString()
    "0"

- String
    
- Boolean
- Object
- Null
- Undefined
- Symbol