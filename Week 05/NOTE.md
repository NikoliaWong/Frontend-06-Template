学习笔记

# Map 对象
    Map 对象保存键值对。任何值(对象或者原始值) 都可以作为一个键或一个值。

# Maps 和 Objects 的区别
    一个 Object 的键只能是字符串或者 Symbols，但一个 Map 的键可以是任意值。
    Map 中的键值是有序的（FIFO 原则），而添加到对象中的键则不是。
    Map 的键值对个数可以从 size 属性获取，而 Object 的键值对个数只能手动计算。
    Object 都有自己的原型，原型链上的键名有可能和你自己在对象上的设置的键名产生冲突。

# DOM createRange() 方法
    返回新创建的 Range 对象，两个边界点都被设置为文档的开头。
    该方法将创建一个 Range 对象，可以用来表示文档的一个区域或与该文档相关的 DocumentFragment 对象。

# Range.setStart(refNode,offset)
    设置范围的开始点。
    该方法将把范围的开始点设置为 startContainer 属性和 startOffset 属性指定的值。
    refNode	包含新的开始点的节点。
    offset	新开始点在 refNode 中的位置。

# Range.insertNode(newNode) 
    在Range的起始位置插入节点的方法。

# Element.getBoundingClientRect() 方法
    返回元素的大小及其相对于视口的位置。