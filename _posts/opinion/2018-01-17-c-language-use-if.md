---
layout: post
title:  【C语言】#if语句的使用
category: opinion
description: C语言#if语句的使用
---
## #if操作（主要是用于实现一些特殊功能的特殊值）： 
  
- `.h`文件避免重复包含，可以写`#ifndef XXXX`

- c和c++混用，cpp里面用c的定义，需要加`#ifdef Cplusplus (extern "C")`

- 控制一些程序的特性的相关定义

- `#ifdef dmt`节省DMT修改工作量

- #if可以作为普通的if来使用，可以包括基础的`&& ||`等逻辑关系，以及else等逻辑分支

<div align="right" style="color:red;font-size:1px"><b>欢迎转载 如有话要说请在下方留言~ 谢谢！^ ^</b></div>


