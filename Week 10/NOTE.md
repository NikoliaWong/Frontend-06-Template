学习笔记

* 排版 - 根据浏览器属性进行排版
* 排版 - 分行：收集元素进row
* 排版 - 计算主轴
* 排版 - 计算交叉轴
* 渲染 - 绘制单个元素
* 渲染 - 绘制DOM树

## CSS中包含着三代的排版技术：  
* 第一代 - 正常流，接近于古典的排版策略：position、display、float等属性
* 第二代 - flex，比较接近人的自然思维
* 第三代 - grid
* 第四代 - CSS Houdini

main axis 主轴   
cross axis 交叉轴，与主轴垂直   

flex-direction决定main axis是哪个方向   
* row - main axis是横向
    * Main: width x left right
    * Cross: height y top bottom
* column - main axis是纵向
    * Main: height y top bottom
    * Cross: width x left right

收集元素进row是为了后面计算元素位置的准备工作 

## 分行（准备数据）
* 根据主轴尺寸，把元素进行分行
* 若设置了no-wrap，则强行分配进第一行

## 计算主轴（计算位置）
* 找到所有flex元素（只支持flex）
* 把主轴方向的剩余尺寸按比例分配给这些元素
* 若剩余空间为负数，所有flex元素为0，等比压缩剩余元素

## 计算交叉轴（计算位置）
* 根据每一行中最大元素尺寸计算行高
* 根据行高flex-align和item-align，确定元素具体位置

## 绘制单个元素（利用images库绘制）
* 绘制需要依赖一个图形环境
* 我们这里采用了npm包的images
* 绘制在一个viewport上进行
* 与绘制相关的属性
    * background-color
    * border
    * background-image
    等等

## 绘制dom（利用images库绘制）
* 递归调用子元素的绘制方法完成Dom树的绘制
* 忽略一些不需要绘制的点
* 实际浏览器中，文字绘制是难点，需要字体库
* 实际浏览器中，还会对一些图层做compositing
