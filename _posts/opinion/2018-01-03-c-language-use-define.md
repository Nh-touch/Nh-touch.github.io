---
layout: post
title:  【C语言】宏定义#define的应用场景小结
category: opinion
description: 简单介绍C语言中宏定义#define的几个简单应用场景
---

## 1.常出现的遗漏的场景
如不使用返回值的函数添加(VOID)常常忘记，就可以用下面的方式进行定义。

```
#define VOS_MEM_SET (VOID)memset
```

## 2.规范常用函数的使用，增加代码可读性
每个模块可以定义一组常用函数的宏，将模块的名称作为函数的一部分，利于规范使用函数并增加可读性。   

```
/* 如定义一个名称为XXX的模块的一些基础函数 */
#define XXX_MEM_SET memset
#define XXX_MEM_CPY memcpy
#define XXX_MEM_CMP memcmp
```

## 3.节省代码行数，也利于维护 

```
#define setValue(value1,value2,value3) \
        a = value1; \
        b = value2; \
        c = value3;
```

## 4.定义一些多维度数组时，用宏定义可减少数组维度，增加可读性

```
#define event(val1, val2) \
        {val1, val2}

int arr[][] = {event(1,2), event(2,3)...};
```

## 5.定义一些容易拼写错误的单词 flase等等，用于屏蔽错误 
```
#define flase false
```

## 6.用于名称的统一问题
有时候需要调用其他模块的api函数，但命名和本模块不同，可通过宏定义解决名称不统一的问题。  

```
/* XXX模块调用YYY模块的API函数 */
#define XXX_GET_VALUE YYY_GET_VALUE
```

## 总结：  
`#define`不是一种安全的写法，因为编译器仅对代码中的宏进行简单的替换，不会做类型检查，不容易发现代码中的错误。但一些简单的宏替换，仍然能够提升函数的规范使用和代码的可读性。

    

<div align="right" style="color:red;font-size:1px"><b>欢迎转载 如有话要说请在下方留言~ 谢谢！^ ^</b></div>


