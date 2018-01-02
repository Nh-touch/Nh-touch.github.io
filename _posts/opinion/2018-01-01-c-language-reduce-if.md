---
layout: post
title:  【C语言】如何减少if...else条件判断
category: opinion
description: 介绍C语言中减少条件判断语句数量的几种方式，降低代码圈复杂度。
---
代码中的圈复杂过高，往往会导致可读性降低，有必要在平时养成良好的编码习惯，避免冗余的条件判断。

## 1.使用if...return结构替换if...else
if...return结构通常用于异常条件排除(如函数入参检查）  

```
    /* if...else 圈复杂度:2 */
    {
        if (条件A) {
            操作A;
        } else (条件B) {
            操作B;
        }

        return;
    }

    /* if...return 圈复杂度:1 */
    {
        if (条件A) {
            操作A;
            return;
        } 
        
        操作B;
        return;
    }
```

## 2.用预设语句+if结构减少else分支
```
    /* if...else 圈复杂度:2 */
    {
        if (条件A) {
            操作A;
        } else (条件B) {
            操作B;
        }

        return;
    }

    /* if预设 + if结构 圈复杂度:1 */
    {
        操作B;

        if (ConditionA) {
            操作A;
        } 
        return;
    }
```

## 3.设表+for循环的方式，减少if分支（有多个if判断）
这种方式并没有减少实际的if分支数量，只是减少了圈复杂度，而弊端是会造成代码的可读性降低。

```
    /* 两个if结构 圈复杂度:2 */
    {
        if (Variable == a) {
            操作A;
        } 

        if (Variable == b) {
            操作B;
        }

        return;
    }

    /* 设表 + if结构 圈复杂度:1 */
    {
        uint32_t array[2] = {a, b};
        int i;

        for (i = 0; i < 2; i++) {
            if (Variable == array[i]) {
                对应操作;
            }
        }

        return;
    }
```

## 4.用移位的方式减少if分支
用空间换时间，即原本两个条件的，将他们连接起来，变成一个新的条件，然后使用switch做对应处理。

```
    /* if直接判断 圈复杂度:2 */
    {
        if ((Variable1 == 0x01) && (Variable2 == 0x10)) {
            操作A;
        } 

        return;
    }

    /* 将条件连接后用if结构判断 圈复杂度:1 */
    {
        uint32_t newCodition = a & b;

        if ((Variable1 & Variable2) == newCondition) {
            操作A;
        } 

        return;
    }
```
 
## 5.将以上的3和4结合起来使用效果更佳
即用位移将多个条件判断值合并，构造场景，然后用设表+for循环+if的方式遍历，从可读性、实际分支减少和降低圈复杂度的角度都是有利的，前提是有足够多的复杂情况需要用到这种结构。

## 6.映射表的方式
这种方法可以彻底去除条件判断。预先设定每个场景对应的处理函数指针数组，并设定每种情况的index定义成枚举。之后就可以直接通过调用数组[index]的方式获取函数指针进行处理。
原本可能需要if或者switch的。也是一种常用的空间换时间的方式。但这种方式是真正减少的if，对性能的提升还是比较大的（条件多的话），可以和4结合起来进行处理

## 总结：
if语句在编码中较常用，养成良好的if...else语句使用习惯，应对不同的使用场景是编码过程中较为重要的一点。

<div align="right" style="color:red;font-size:1px"><b>欢迎转载 如有话要说请在下方留言~ 谢谢！^ ^</b></div>


