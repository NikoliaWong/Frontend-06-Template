学习笔记
# 1. RegExpObject.exec(string)
    exec()方法返回的是一个数组，数组的第一个元素是匹配到的字符串，之后的元素则分别对应匹配到的字串，也就是正则表达式中用括号括起来的那些。
    如果使用exec()方法的正则表达式没有全局标志，则只会匹配第一个，如果正则表达式有全局标志，则可以循环使用exec()来得到所有的匹配，直到exec()返回null为止，也就是找不到匹配了。这里能够循环使用同一个正则表达式的exec()方法，靠的就是lastIndex，因为带全局标志的正则表达式每次匹配后都会更新lastIndex的值作为下次查找匹配的起点。

# 2. RegExpObject.lastIndex 属性
    lastIndex 属性用于规定下次匹配的起始位置。
    注意： 该属性只有设置标志 g 才能使用。
    上次匹配的结果是由方法 RegExp.exec() 和 RegExp.test() 找到的，它们都以 lastIndex 属性所指的位置作为下次检索的起始点。
    这样，就可以通过反复调用这两个方法来遍历一个字符串中的所有匹配文本。
    注意：该属性是可读可写的。只要目标字符串的下一次搜索开始，就可以对它进行设置。
    当方法 exec() 或 test() 再也找不到可以匹配的文本时，它们会自动把 lastIndex 属性重置为 0。

# 3. 空字符串，中间有空格时布尔值是true



# LL算法

## 理解编译原理：一个四则运算的解释器

### 分析（四步）

- 定义四则运算：产出四则运算的词法定义和语法定义。
- 词法分析：把输入的字符串流变成 token。
- 语法分析：把 token 变成抽象语法树 AST。
- 解释执行：后序遍历 AST，执行得出结果。

### 定义四则运算

#### 词法定义

- Token:
    - 1 2 3 4 5 6 7 8 9 0 的组合
    - Operator: +、-、*、/之一
- Whitespace: \<SP>
- LineTerminator: \<LF><CR>


#### 语法定义

BNF（Backus-Naur Form）范式

> 以美国人巴科斯(Backus)和丹麦人诺尔(Naur)的名字命名的一种形式化的语法表示方法。

- 语法：

1. 在双引号中的字("word")代表着这些字符本身。而double_quote用来代表双引号。

2. 在双引号外的字（有可能有下划线）代表着语法部分。

3. 尖括号( < > )内包含的为必选项。

4. 方括号( [ ] )内包含的为可选项。

5. 大括号( { } )内包含的为可重复0至无数次的项。

6. 竖线( | )表示在其左右两边任选一项，相当于"OR"。

7. ::= 是“被定义为”。

采用BNF范式定义语法

加法：

```
<Expression> ::= 
    <AdditiveExpression><EOF>

<AdditiveExpression> ::= 
    <MultiplicativeExpression>
    |<AdditiveExpression><+><MultiplicativeExpression>
    |<AdditiveExpression><-><MultiplicativeExpression>
```

乘法：

```
<MultiplicativeExpression> ::= 
    <Number>
    |<MultiplicativeExpression><*><Number>
    |<MultiplicativeExpression></><Number>
```

### 词法分析：状态机

