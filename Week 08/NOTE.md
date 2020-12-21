学习笔记
# 浏览器工作原理

# 第一部分：URL 到 HTTP

## 一. url->bitmap 解析流程
URL ---HTTP---> HTML ---parse---> DOM ---css computing---> DOM with CSS ---layout---> DOM with position ---render---> Bitmap

在计算机里面，最后显示在屏幕上的是图片的形式，术语叫做Bitmap
将bitmap传给显卡驱动设备转化成人眼可识别的光信号


![p1][p1]

1. http获取html文本
2. 解析html文本，形成DOM树
3. 对裸DOM树进行CSS Computing (dom树对应哪些CSS规则， 哪些css规则需要进行叠加、覆盖，得出最后的结果)，得到带样式的DOM
4. 对带样式的DOM进行布局/排版（计算DOM树元素产生的盒的位置）
5. 将DOM树画到一张图片上， 并调用系统接口展示到屏幕上

## 二. 有限状态机

* 每个状态都是一个机器

  * 在每个机器里， 我们可以做计算、存储、输出。。。。
  * 所有的这些机器接受的输入时一致的
  * 状态机的每一个机器本身没有状态， 如果我们用函数来表示的话，它应该是纯函数（无副作用，但只针对输入，不针对输出）

* 每一个机器知道下一个状态

  * 每个机器都有确定的下一个状态（Moore)
  * 每个机器根据输入决定下一个状态（Mealy)

* js中的有限状态机 （Mealy)

  ```js
  //每个函数都是一个状态
  function state(input){
      //在函数中， 可以自由的编写代码， 处理每一个状态的逻辑
      return next  //返回值作为下一个状态
  }
  
  //////以下是调用
  while(input){
   	//获取输入
      state = state(input) //把状态机的返回值作为下一个状态
  }
  ```


#  三 ISO网络模型

![p2][p2]

# 四 HTTP

* Request
* Response

    Request line: method path protocol/version
    Headers: KV结构
    \r\n
    Body: 由content-type决定，总体上也是KV结构，视content-type不同使用不同的分隔的字符和不同的格式

    Status line: protocol/version code desc
    Headers: KV结构
    \r\n
    Body: 由content-type决定。比较典型的格式为chunked body，由node默认返回的一种body的格式

    chunked body
    十六进制的数字单独占一行
    内容部分
    十六进制的0

### 1. http请求总结

* 设计一个http请求的类
* content-type是请求头里面必须的一个字段， 要有默认值
* body是kv模式
* 不同的content-type影响bodyText的格式

### 2. send函数总结

* 在Reqest的构造器中收集必要的信息
* 设计一个send函数， 把请求真实发送给服务器
* send函数应该是异步的， 所以返回Promise

Response 结构图解：

![p3][p3]

参考：

[HTTP 协议中的 Transfer-Encoding][https://imququ.com/post/transfer-encoding-header-in-http.html]

### 3. 发送请求

* 设计支持已有的connection或者自己新建connection
* 收到数据传给parser
* 根据parser的状态resolve Promise

### 4. ResponseParser总结

* Response必须分段构造， 所以我们要用一个ResponseParser来 “装配”
* ResponseParser分段处理ResponseText, 使用状态机来分析文本的结构

### 5. BodyParser总结

* Response的body可能根据Content-type有不同的结构， 因此我们会采用子Parser的结构来解决问题
* 以TrunkedBodyParser为例， 同样使用状态机来处理body格式

