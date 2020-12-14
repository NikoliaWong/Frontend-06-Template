学习笔记

## 运算符与表达式

### 运算符

* Member
    * a.b
    * a[b]
    * foo`string`
    * super.b
    * super['b']
    * new.target
    * new Foo()

* New 比Member类运算符低
    * new Foo

带括号的new的优先级较高

Example:
new a()() ---> 先是new a()，然后是new运算后的结果再接上()
new new a() ---> 先是new a()，然后是new运算后的结果再接上new

### Reference (规范中的类型，语言中没这个类型)

分成两个部分，第一个部分是对象，第二个部分是一个key。记录了Member运算的前半部分和后半部分。

delete和assign这类基础设施就会用到Reference类型。

用来让delete知道删除是哪一个对象的哪一个属性，assign也类似。

### Expressions

* Call 优先级低于new，也低于Member运算
    . foo()
    . super()
    . foo()['b']
    . foo().b
    . foo()`abc`
如果在call expressions里有用到Member表达式，则都统一降级为call expressions级别

Example:
new a()['b'] ---> 先是new a()（Member），然后是new运算后的结果再接上['b']

总结来说，就是为了解决()跟谁先结合的问题，才有了Member、New、Call Expressions的优先级

* Left Handside & Right Handside 左手右手运算

Example:
左手运算 a.b = c 可以放在等号左边
右手运算 a + b = c 不可放在等号左边，只有Left Handside才能放在等号左边

* Update（自增自减表达式，Right Handside）
    * a++
    * a--
    * -- a
    * ++ a

Example:
++ a ++  a优先跟右边的自增结合 但运行时还是会显示不合法
++ (a ++)

* Unary（单目运算符）
    * delete a.b
    * void foo() void运算符的作用 是把后面的结果都变成undefined
    * typeof a
    * + a
    * - a
    * ~ a 位运算 把一个整数按位取反 若不是整数 则强制取整
    * ! a 常用两个!!做强制类型转换
    * await a

* Exponental（**，右结合）
    ** 乘方运算

Example:
3 ** 2 ** 3
3 ** (2 ** 3)

* Multiplicative 会发生强制类型转换
    * /
    * *
    * % 取余

* Additive
    * +
    * -

* Shift 移位运算
    * <<
    * >>
    * >>>

* Relationship 关系比较
    * <
    * >
    * <=
    * >=
    * instanceof
    * in

* Equality
    * == 
    * !=
    * ===
    * !==

* Bitwise 比相等的比较优先级更低
    * &
    * ^
    * |

* Logic
    * && (短路原则) &&左边的结果为false的时候 &&右边的表达式不会执行
    * || (短路原则) ||左边的结果为true的时候 ||右边的表达式不会执行

* Conditional（三目运算符）
    * ? : (短路原则)


### Type Convertion 类型转换

|      原始值      | 转换为 Number |   转换为 String   | 转换为 Boolean |
| :--------------: | :-----------: | :---------------: | :------------: |
|      false       |       0       |      "false"      |     false      |
|       true       |       1       |      "true"       |      true      |
|        0         |       0       |        "0"        |     false      |
|        1         |       1       |        "1"        |      true      |
|       "0"        |       0       |        "0"        |      true      |
|       "1"        |       1       |        "1"        |      true      |
|       NaN        |      NaN      |       "NaN"       |     false      |
|     Infinity     |   Infinity    |    "Infinity"     |      true      |
|    -Infinity     |   -Infinity   |    "-Infinity"    |      true      |
|        ""        |       0       |        ""         |     false      |
|       "20"       |      20       |       "20"        |      true      |
|     "twenty"     |      NaN      |     "twenty"      |      true      |
|        []        |       0       |        ""         |      true      |
|       [20]       |      20       |       "20"        |      true      |
|     [10,20]      |      NaN      |      "10,20"      |      true      |
|    ["twenty"]    |      NaN      |     "twenty"      |      true      |
| ["ten","twenty"] |      NaN      |   "ten,twenty"    |      true      |
|   function(){}   |      NaN      |  "function(){}"   |      true      |
|        {}        |      NaN      | "[object Object]" |      true      |
|       null       |       0       |      "null"       |     false      |
|    undefined     |      NaN      |    "undefined"    |     false      |

### UnBoxing 拆箱转换

* ToPremitive
* toString vs valueOf
* Symbol.toPremitive

Example:
var o = {
    toString() { return '2'},
    valueOf() { return 1 },
    [Symbol.toPrimitive]() { return 3 }
}

console.log('x' + o)
+一般先调valueOf，然后是toString。只要有[Symbol.toPrimitive]，就一定会是[Symbol.toPrimitive]

var x = {};x[o] = 1;
console.log(x + o)
o作为属性名的时候，优先调用toString方法。只要有[Symbol.toPrimitive]，就一定会是[Symbol.toPrimitive]

### Boxing

* Number ---> new Number(1)  值：1
* String ---> new String('a')  值：a
* Boolean ---> new Boolean(true)  值：true
* Symbol ---> new Object(Symbol('a'))  值：Symbol('a')


## 简单语句

* ExpressionStatement (核心，计算)
* EmptyStatement （空语句 单独的一个分号）
* DebuggerStatement（debugger;）
* ThrowStatement (抛出异常)
* ContinueStatement (结束单次循环)
* BreakStatement (结束整个循环)
* ReturnStatement (返回函数值)


## 复合语句

* BlockStatement {语句列表。。} 
* IfStatement （条件语句）
* SwitchStatement （不建议使用，用if代替）
* IterationStatement （循环语句集合）
* WithStatement
* LabelledStatement（与ContinueStatement和BreakStatement搭配使用）
* TryStatement（try catch finally return无法打断）

## 声明 Statement

* FunctionDeclaration (函数声明)
* GeneratorDeclaration (Generator函数声明)
* AsyncFunctionDeclaration (异步函数声明)
* AsyncGeneratorDeclaration (异步产生器函数声明)
* VariableStatement (var 变量声明)
* ClassDeclaration
* LexicalDeclaration (let、 const)

* function
* function *
* async function
* async function *
* var

以上5种声明都没有先后关系，永远当作第一行去声明。作用域的作用范围只认function body。

* class
* let
* const

以上3种声明在声明之前不能用声明的变量。

# 预处理（pre-process）
    所有的声明都有预处理机制 都可把这个变量变成局部变量
    区别是const 变量在声明前使用会抛错，这个错可以被try和catch去处理
Example
    var a = 2;
    void function(){
        a = 1;
        return;
        var a;
    }();
    console.log(a);//2

    var a = 2;
    void function(){
        a = 1;//抛错
        return;
        const a;
    }();
    console.log(a);//2

# 作用域
Example
    var a = 2;
    void function(){
        a = 1;
        {
            var a;
        }
    }();
    console.log(a);//2

    var a = 2;
    void function(){
        a = 1;
        {
            const a;
        }
    }();
    console.log(a);//报错 Missing initializer in const declaration

## 结构化 | 宏任务和微任务

### JS执行力度

* 宏任务（传给js引擎的任务）
* 微任务（es2020中，只有Promise产生微任务，js引擎内部的任务）
* 函数调用（Execution Context）
* 语句/声明（Completion Record）
* 表达式（Reference）
* 直接量/变量/this...

### 事件循环

获取代码 ---> 执行代码 ---> 等待 ---> 获取代码 ....

### 函数调用

函数调用会形成执行上下文栈（Execution Context Stack），而栈里面的单元是执行上下文（Execution Context）。而正在跑的栈叫做执行中执行上下文（Running Execution Context）。

【当前正在跑的语句就会在Running Execution Context中获取一切信息。而闭包，就在这个单元里。这也解释了我之前的疑问，a文件通过import引入b文件，在b文件里访问不到a文件的变量，我还以为

可以通过闭包访问，但是是不行的。只有在同一份js文件里或通过脚本引入不同文件的才可以。】其实【而闭包，就在这个单元里】不对，闭包在环境记录里面体现

#### Execution Context

* code evaluation state（用于async和Generator的，保存代码执行到哪的信息）
* Function
* Script Or Module（要么是脚本，要么是Module）
* Generator
* Realm
* LexicalEnvironment
    * this
    * new Target
    * super
    * 变量
* VariableEnvironment
    * var

#### Environment Record

* Declarative Environment Records
    * Function Environment Records
    * module Environment Records
* Global Environment Records
* Object Environment Records

#### Function-Closure

每一个函数都会生成一个闭包

Example
    var y = 2
    function foo () {console.log(y)}
    export foo

Function:foo
    Environment Record(定义时所在的):
            y:2
    Code:
            console.log(y)

