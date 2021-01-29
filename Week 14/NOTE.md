学习笔记

# 前端组件化的基本概念和基本组成部分
## 两个重要概念
	- 前端组件化
	- 前端架构模式 mvvm, mvc
## 对象与组件
	我们一般说组件它区别于模块，区别于对象，为什么我们不说模块化，模块化其实也是一个我们架构里面非常通用的概念，对象也是架构里面非常重要的一个概念。一般来说组件它是和UI强相关的东西，某种意义上我们可以认为它是一种特殊意义的模块或者是特殊的对象，注意它即是模块又是对象，它可以以树形结构来进行组合，平且它有这种模板化的配置能力，这就是我们组件的一个基本概念。
	组件和对象的区别：
	对象：
		1. Properties 属性
		2. Methods    方法
		3. inherit    继承
	组件：
		1. Properties 属性
		2. Methods    方法
		3. inherit    继承
		4. Attribute  特性
		5. Config & State  组件的配置 & 组件的状态
		6. Event      事件，组件往外去传递数据的桥梁
		7. LifeCycle  声明周期
		8. Children   树形结构的必要性，必要条件，没有Children,就形不成树形结构，没有树形结构，描述UI的能力就大打折扣


## Attribute VS Property  不同点

* Attribute 强调描述性   (来自xml的Attribute)
* Property  强调从属关系 (来自于对象的属性)

**html中 Attribute和Property的不一致**

* Property不能被Markup这种声明式语言去设置的，但是可以被js设置和改变，大部分情况下不应该由用户输入去改变，少数情况下比如说来自业务逻辑去由用户输入改变
* Attribute是可以由Markup设置, js改变和设置都是可以的，然后用户输入和Property类似
* State有一个很大的特点，就是它只能由组件的内部去改变，不会从组件的外部去改变，但是一定要保证用户输入可以改变State,比如用户点击某个Tab，某个Tab则被激活了，这种一般是通过state去控制
* Config 是一个一次性的结果，只有在组件构造的时候去触发，能够一次性的传进来，它是不可更改的,通常留给全局。

## 生命周期
	生命周期，我们最容易想到的就是Created和destroyed, 世间万物皆有这两个周期。
那一个组件会有以下周期
	一个组件创建之后，被屏幕显示出来，这个叫mount, 从屏幕上卸载下来叫做unmount，mount和unmount是会反复发生的，unmount之后可以回到created状态。
	一个组件还有什么时候会改变自己的状态呢？ 有两个： 1.组件的使用者可以通过代码去更改组件，2.组件的终端用户，用户输入去改变组件。这两个时候都会产生一个组件的生命周期，统一称为Update.

## Children
	Children分两种：Content型和Template型
* Content: 有几个Child就会显示出几个child
* Template型: 整个child充当一个模板的作用，比如说一个list的结构，一般list需要接收一个data, 它最终的渲染的child数量是有data的长度来决定的，child模板会被复制100份。
在设计组件树的时候，需要考虑以上两种情况



# 搭建JSX环境
1. 新建目录项目
```shell
mkdir jsx && cd jsx
npm init   //一路回车 使用默认值
```
2. 安装webpack和webpack-cli
```shell
yarn add webpack@4.44.1 webpack-cli@3.3.12 -D   //这里和老师版本保持一致
```

3. 安装babel-loader
```shell
yarn add babel-loader@8.1.0 -D
```

4. 新建webpack.config.js,并写入简单配置
// vi webpack.config.js
```js
module.exports = {
	entry: "./main.js",
};
```

5. 新建main.js, 写入一下内容
//touch main.js
```js
for (let i of [1, 2, 3]) {
	console.log(i);
}
```

6. 命令行执行
```shell
npx webpack
```
可以看到生成了一个dist目录，并且生成了main.js文件，在最后，有我们自己写的main.js的for循环代码
从以上可以看出 babel-loader 是一个webpack的loader, 并没有依赖babel, 但是其实目前babel-loader还没有起到作用，这里卸载了babel-loader执行npx webpack 依然可以得到和上面的dist/main.js相同的内容

7. 安装babel/core和babel/preset-env
```shell
yarn add @babel/core@7.11.1 @babel/preset-env@7.11.0 -D
```

8. 配置babel, 在webpack.config.js里面加入babel相关配置
```js
module.exports = {
	entry: "./main.js",
	module: {
		rules: [
			{
				test: /\.js$/,
				use: {
					loader: "babel-loader",
					options: {
						presets: ["@babel/preset-env"],
					},
				},
			},
		],
	},
};
```
9. 再次执行 npx webpack 可以得到一个新的dist/main.js文件，
可以看到最后的部分，我们用for of写的for循环被编译成了普通的for循环， 这个就是babel的preset-env起到的作用了

10. 在webpack中加入开发者模式的配置
```js
module.exports = {
	entry: "./main.js",
	mode: "development",
	module: {
		rules: [
			{
				test: /\.js$/,
				use: {
					loader: "babel-loader",
					options: {
						presets: ["@babel/preset-env"],
					},
				},
			},
		],
	},
};
```
11. 再次执行 npx webpack 可以得到一个新的dist/main.js文件，
可以看到这次代码并未做压缩，而且我们自己写的代码放在了eval里面，这样调试时就可以作为一个单独的文件调试了·

12. 在main.js中加入一个jsx语法, 执行npx webpack， 发现它报错了，说明目前还不支持jsx语法， webpack把"<"认成了小于符号

13. 安装@babel/plugin-transform-react-jsx
```shell
yarn add @babel/plugin-transform-react-jsx@7.10.4 -D
```

14. webpack.config.js加入jsx配置
```js
module.exports = {
	entry: "./main.js",
	mode: "development",
	module: {
		rules: [
			{
				test: /\.js$/,
				use: {
					loader: "babel-loader",
					options: {
						presets: ["@babel/preset-env"],
						plugins: ["@babel/plugin-transform-react-jsx"],  //加入jsx的语法配置
					},
				},
			},
		],
	},
};
```

11. 再次执行 npx webpack 可以得到一个新的dist/main.js文件，
可以看到jsx语法被翻译成了React.createElement函数。 到此我们的配置已经支持了jsx语法

12. 增加 "@babel/plugin-transform-react-jsx" 的pragma配置，修改jsx函数名称, 修改webpack.config.js如下：
```js
module.exports = {
	entry: "./main.js",
	mode: "development",
	module: {
		rules: [
			{
				test: /\.js$/,
				use: {
					loader: "babel-loader",
					options: {
						presets: ["@babel/preset-env"],
						plugins: [["@babel/plugin-transform-react-jsx", { pragma: "createElement" }]],
					},
				},
			},
		],
	},
};
```
11. 再次执行 npx webpack 可以得到一个新的dist/main.js文件
可以看到jsx语法被翻译成了createElement函数。 到此我们的项目内容已经和react没有任何关系了








