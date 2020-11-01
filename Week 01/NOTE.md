学习笔记
# 1、TicTacToe 代码的思想
 01 绘制棋盘
 02 添加下棋事件
 03 判断胜负
 04 检查是否要赢
 05 AI
 （1）第一层策略：我要赢
 （2）第二层策略：别输
 （3）第三层策略：我方走完，对方怎么走都不会赢

# 2、对象的复制
    function clone(pattern) {
        return JSON.parse(JSON.stringify(pattern))
    }

# 3、块级作用域 {}

# 4、JavaScript的异步机制
（1）callback
（2）Promise
（3）async/await

# 5、while (true) {} 
 只要指定条件为 true，循环就可以一直执行代码块。

# 6、break continue
 break 语句“跳出”循环。break 语句会中断循环，并继续执行循环之后的代码（如果有）;
 continue 语句“跳过”循环中的一个迭代。continue 语句中断（循环中）的一个迭代，如果发生指定的条件。然后继续循环中的下一个迭代。

 continue 语句（不论有无标签引用）只能用于跳过一个迭代。
 break 语句，如果没有标签引用，只能用于跳出一个循环或一个 switch。
 如果有标签引用，则 break 语句可用于跳出任意代码块：


