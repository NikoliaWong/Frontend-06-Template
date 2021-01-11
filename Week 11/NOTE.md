学习笔记


# CSS总体结构

* @charset
* @import
* rules
  * @media
  * @page
  * rule

# CSS @规则的研究

* @charset ： https://www.w3.org/TR/css-syntax-3/
* @import ：https://www.w3.org/TR/css-cascade-4/
* @media ：https://www.w3.org/TR/css3-conditional/
* @page ： https://www.w3.org/TR/css-page-3/
* @counter-style ：https://www.w3.org/TR/css-counter-styles-3
* @keyframes ：https://www.w3.org/TR/css-animations-1/
* @fontface ：https://www.w3.org/TR/css-fonts-3/
* @supports ：https://www.w3.org/TR/css3-conditional/
* @namespace ：https://www.w3.org/TR/css-namespaces-3/

# CSS规则

* 选择器
* 声明
  * Key
  * Value

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

* Selector
  * https://www.w3.org/TR/selectors-3/
  * https://www.w3.org/TR/selectors-4/
* Decalartion:
  * Key
    * Properties
    * Variables:https://www.w3.org/TR/css-variables/
  * Value:https://www.w3.org/TR/css-values-4/

![p1][p1]

# 爬取W3.org Css属性小工具

1. 获取链接：

   ```js
   /*为了避免跨域问题，直接找一个w3.org的页面在console控制台运行一下代码*/	
   Array.prototype.slice
   		.call(document.querySelector("#container").children, 0)
   		.filter((item) => item.getAttribute("data-tag").match(/css/))
   		.map((item) => ({
   			name: item.children[1].children[0].textContent,
   			href: item.children[1].children[0].href,
       }))
   ```

2. 获取属性

   ```js
   /*为了避免跨域问题，直接找一个w3.org的页面在console控制台运行一下代码*/
   let standards = [
   	{
   		name: "CSS  Custom  Highlight  API  Module  Level 1",
   		href: "https://www.w3.org/TR/2020/WD-css-highlight-api-1-20201208/",
   	},
   	{
   		name: "CSS  Conditional  Rules  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/CR-css-conditional-3-20201208/",
   	},
   	{
   		name: "CSS  Text  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-text-3-20201119/",
   	},
   	{
   		name: "TTML Media Type Definition and Profile Registry",
   		href: "https://www.w3.org/TR/2020/NOTE-ttml-profile-registry-20201119/",
   	},
   	{
   		name: "CSS  Lists  and  Counters  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-lists-3-20201117/",
   	},
   	{
   		name: "CSS  Fonts  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-fonts-4-20201117/",
   	},
   	{
   		name: "CSS  Color  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-color-4-20201112/",
   	},
   	{
   		name: "CSS  Values  and  Units  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-values-4-20201111/",
   	},
   	{
   		name: "CSS  Scroll  Anchoring  Module  Level 1",
   		href: "https://www.w3.org/TR/2020/WD-css-scroll-anchoring-1-20201111/",
   	},
   	{
   		name: "CSS  Color  Adjustment  Module  Level 1",
   		href: "https://www.w3.org/TR/2020/WD-css-color-adjust-1-20201109/",
   	},
   	{
   		name: "Requirements for Chinese Text Layout中文排版需求",
   		href: "https://www.w3.org/TR/2020/WD-clreq-20201101/",
   	},
   	{
   		name: "CSS  Box  Model  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-box-3-20201028/",
   	},
   	{
   		name: "CSS  Box  Sizing  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-sizing-3-20201023/",
   	},
   	{
   		name: "CSS  Grid  Layout  Module  Level 2",
   		href: "https://www.w3.org/TR/2020/CRD-css-grid-2-20201021/",
   	},
   	{
   		name: "CSS  Grid  Layout  Module  Level 1",
   		href: "https://www.w3.org/TR/2020/CRD-css-grid-1-20201021/",
   	},
   	{
   		name: "CSS  Box  Sizing  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-sizing-4-20201020/",
   	},
   	{
   		name: "CSS  Properties  and  Values  API  Level 1",
   		href: "https://www.w3.org/TR/2020/WD-css-properties-values-api-1-20201013/",
   	},
   	{ name: "Worklets  Level 1", href: "https://www.w3.org/TR/2020/WD-worklets-1-20200908/" },
   	{
   		name: "CSS  Inline  Layout  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-inline-3-20200827/",
   	},
   	{
   		name: "CSS  Cascading  and  Inheritance  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-cascade-4-20200818/",
   	},
   	{
   		name: "CSS  Cascading  and  Inheritance  Level 3",
   		href: "https://www.w3.org/TR/2020/CR-css-cascade-3-20200817/",
   	},
   	{
   		name: "Requirements for Japanese Text Layout 日本語組版処理の要件(日本語版)",
   		href: "https://www.w3.org/TR/2020/NOTE-jlreq-20200811/",
   	},
   	{
   		name: "Media  Queries  Level 5",
   		href: "https://www.w3.org/TR/2020/WD-mediaqueries-5-20200731/",
   	},
   	{
   		name: "Media  Queries  Level 4",
   		href: "https://www.w3.org/TR/2020/CR-mediaqueries-4-20200721/",
   	},
   	{
   		name: "CSS  Overflow  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-overflow-3-20200603/",
   	},
   	{
   		name: "CSS  Containment  Module  Level 2",
   		href: "https://www.w3.org/TR/2020/WD-css-contain-2-20200603/",
   	},
   	{ name: "Encoding", href: "https://www.w3.org/TR/2020/NOTE-encoding-20200602/" },
   	{
   		name:
   			"Requirements for Hangul Text Layout and Typography : 한국어 텍스트 레이아웃 및 타이포그래피를 위한 요구사항",
   		href: "https://www.w3.org/TR/2020/NOTE-klreq-20200527/",
   	},
   	{ name: "Ethiopic Layout Requirements", href: "https://www.w3.org/TR/2020/WD-elreq-20200526/" },
   	{
   		name: "CSS  Positioned  Layout  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-position-3-20200519/",
   	},
   	{
   		name: "CSS  Display  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/CR-css-display-3-20200519/",
   	},
   	{
   		name: "CSS  Text  Decoration  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-text-decor-4-20200506/",
   	},
   	{
   		name: "CSS  Ruby  Layout  Module  Level 1",
   		href: "https://www.w3.org/TR/2020/WD-css-ruby-1-20200429/",
   	},
   	{
   		name: "CSS  Box  Alignment  Module  Level 3",
   		href: "https://www.w3.org/TR/2020/WD-css-align-3-20200421/",
   	},
   	{
   		name: "CSS  Box  Model  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-box-4-20200421/",
   	},
   	{ name: "CSS Speech Module", href: "https://www.w3.org/TR/2020/CR-css-speech-1-20200310/" },
   	{
   		name: "CSS  Transforms  Module  Level 2",
   		href: "https://www.w3.org/TR/2020/WD-css-transforms-2-20200303/",
   	},
   	{
   		name: "CSS  Color  Module  Level 5",
   		href: "https://www.w3.org/TR/2020/WD-css-color-5-20200303/",
   	},
   	{
   		name: "CSS  Conditional  Rules  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-conditional-4-20200303/",
   	},
   	{ name: "Resize Observer", href: "https://www.w3.org/TR/2020/WD-resize-observer-1-20200211/" },
   	{
   		name: "Timed Text Markup Language 2 (TTML2) (2nd Edition)",
   		href: "https://www.w3.org/TR/2020/CR-ttml2-20200128/",
   	},
   	{
   		name: "CSS  Basic  User  Interface  Module  Level 4",
   		href: "https://www.w3.org/TR/2020/WD-css-ui-4-20200124/",
   	},
   	{
   		name: "CSS  Writing  Modes  Level 3",
   		href: "https://www.w3.org/TR/2019/REC-css-writing-modes-3-20191210/",
   	},
   	{
   		name: "CSS  Spatial  Navigation  Level 1",
   		href: "https://www.w3.org/TR/2019/WD-css-nav-1-20191126/",
   	},
   	{
   		name: "CSS  Containment  Module  Level 1",
   		href: "https://www.w3.org/TR/2019/REC-css-contain-1-20191121/",
   	},
   	{ name: "CSS  Text  Module  Level 4", href: "https://www.w3.org/TR/2" },
   ];
   
   let iframe = document.createElement("iframe");
   iframe.width = 800;
   iframe.height = 600;
   document.body.innerHTML = "";
   document.body.appendChild(iframe);
   
   function happen(element, event) {
   	return new Promise((res, rej) => {
   		let handler = () => {
   			res();
   			element.removeEventListener(event, handler);
   		};
   		element.addEventListener(event, handler);
   	});
   }
   
   void (async function () {
   	for (let standard of standards) {
   		iframe.src = standard.href;
   		await happen(iframe, "load");
   		console.log(iframe.contentDocument.querySelectorAll(".propdef")
   	}
   })();
   ```

   

# 选择器语法

* 简单选择器
  * \*
  * 标签   div svg|a   
  * 类  .cls
  * ID  #id
  * 属性        	           理论上可以用属性选择器代替类和id选择器（如果不考虑选择器优先级的话）
    *  [attr]               有该属性    
    *  [attr=value]     属性值等于value
  *  [attr~=value]   属性值中的一个等于value，(适用于用空格相连的多个value)
    *  [attr|=value]    属性值以value开头
  * 伪类   :hover           （主要是元素的一些特殊状态[来自交互]，或者是带函数的选择器）
  * 伪元素  ::before 
  
* 复合选择器
  * <简单选择器><简单选择器><简单选择器>           多个简单选择器之间是 “与” 的关系
  * \* 或者div 必须写在最前面
* 复杂选择器
  * <复合选择器><sp><复合选择器>           (子孙)后代
  * <复合选择器>">"<复合选择器>               父子   
  * <复合选择器>"~"<复合选择器>	           后续邻居
  * <复合选择器>"+"<复合选择器>               第一个后续邻居
  * <复合选择器>"||"<复合选择器>               列选择器，表示选中对应列中符合条件的单元格

# 选择器优先级

* 简单选择器计数

![p2][p2]

> MDN
>
> [CSS选择器]:https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity
>
> 下面列表中，选择器类型的优先级是递增的：
>
> 1. [类型选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/Type_selectors)（例如，`h1`）和伪元素（例如，`::before`）
> 2. [类选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/Class_selectors) (例如，`.example`)，属性选择器（例如，`[type="radio"]`）和伪类（例如，`:hover`）
> 3. [ID 选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors)（例如，`#example`）。

* 伪类选择器的权重：

  * 问题：

    #a:not(#b)  为什么这个选择器的优先级是 0 2 0 0，而不是 0 2 1 0 （两个 id 选择器[#a #b]，一个伪类选择器[:not]） 呢？？

  * 答案：

    ：not这种伪类选择器的优先级会被他参数里最大的那个值替换

    > https://www.w3.org/TR/selectors-4/#specificity-rules

    ![p3][p3]

* 练习题：请写出下面选择器的优先级
  
  * 1、div#a.b .c[id=x] [0 1 3 1]    0\*N^3 + 1\*N^2 + 3\*N^1 + 1\*N^0 +1
  * 2、#a:not(#b) [0 2 0 0]          0\*N^3 + 2\*N^2 + 0\*N^1 + 0\*N^0 +1
  * 3、\*.a [0 0 1 0]                0\*N^3 + 0\*N^2 + 1\*N^1 + 0\*N^0 +1
  * 4、div.a [0 0 1 1]               0\*N^3 + 0\*N^2 + 1\*N^1 + 1\*N^0 +1

* 答案： 1 > 2 > 4 > 3

# 伪类

* 链接/行为

  * :any-link   	所有超链接
  * :link              未访问超链接
  * :visited         已访问超链接
  * :hover          鼠标放上去之后生效
  * :active          点击之后生效
  * :focus           
  * :target           当前url的hash指向了当前的锚点

* 树结构

  * :empty
  * :nth-child()
  * :nth-last-child()  //倒数
  * :first-child :last-child :only-child

  其中:empty，:nth-last-child(), :last-child和:only-child 破坏了ComputeCss的计算时机的问题

  :empty（StartTag入栈时并不知道是否有子元素）

  :nth-last-child()，:last-child （需要倒数的话，必须提前知道所有的子元素）

  :only-child（必须提前知道所有的子元素）

  :nth-child()和:first-child不会破坏ComputeCss的时机，因为只需要进入到第N个或者第一个子元素时计算css即可

  **注意破坏ComputeCss时机的选择器，性能上可能会稍微差一点，因为需要通过一些hack手段去实现**

* 逻辑型

  * :not伪类  （只支持复合选择器（多个简单选择器））
  * :where  :has (处于草案状态)

# 伪元素

* ::before
* ::after
* ::first-letter
* ::first-line

### ::before,::after

```html
<div>
    <::before/>
    content content content content content
    content content content content content
    content content content content content
    content content content content content
    <::after/>
</div>
```

### ::first-letter   适合报纸中第一个非常大的字

```html
<div>
    <::first-letter>c</::first-letter>content content content content content
    content content content content content
    content content content content content
    content content content content content
    content content content content content
</div>
```

first-letter 可以设置的属性

* font系列
* color系列
* background系列
* word-spacing
* letter-spacing
* text-decoration
* text-transform
* line-height
* float
* vertical-align
  * 盒模型系列：margin,padding,border

### ::first-line

```html	
<div>
    <::first-line>content content content content content</::first-line>
    content content content content content
    content content content content content
    content content content content content
    content content content content content
</div>
```

first-line 可以设置的属性

* font系列

* color系列

* background系列

* word-spacing

* letter-spacing

* text-decoration

* text-transform

* line-height

  

## 思考题： 为什么 first-letter 可以设置 float 之类的，而 first-line 不行呢？

first-letter是在布局完成之后，确定了一段文字中的第一个文字，可以对其操作布局时性能开销小；
而first-line选中的是第一行文字，不同的宽度选中的文字内容不一样，要对其重新布局排版消耗性能大,所以first-letter 可以设置 float 之类的，而 first-line 不行。

* 根本原因在于**:first-line**描述的文本长度不是一个确定的值。因此会触发一些重新计算或者改变 文档流的属性被限制使用

* [sel-first-line](https://www.w3.org/TR/selectors-3/#sel-first-line)

* > The [`::first-line`](https://www.w3.org/TR/selectors-3/#sel-first-line) pseudo-element is similar to an inline-level element, but with certain restrictions. The following CSS properties apply to a [`::first-line`](https://www.w3.org/TR/selectors-3/#sel-first-line) pseudo-element: font properties, color property, background properties, ‘`word-spacing`’, ‘`letter-spacing`’, ‘`text-decoration`’, ‘`text-transform`’, ‘`line-height`’. UAs may apply other properties as well.

