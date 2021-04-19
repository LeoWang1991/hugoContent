---
title: "Js深拷贝实现"
date: 2021-04-09T14:12:02+08:00
draft: true
tags: [实现, javascript]
categories: [前端]
---

### 前言

1. 深拷贝和浅拷贝概念
2. 深拷贝实现
3. 常用库lodash underscore中如何实现额



### 堆栈内存

1. 我们知道在js中基本数据结构和对象数据结构两种，分别存储在stack栈内存和heap堆内存。
2. 对象变量实际的数据值存储在heap堆内存中，在栈内存中保存该数据的位置（指针）。

![Jo6l3V](https://blog-img-1256179672.cos.ap-shanghai.myqcloud.com/img/Jo6l3V.jpg)



### 拷贝和赋值

```javascript
const obj1 = { name: 'xiaofei', age: 20 };
const obj2 = obj1;
```

首先得弄清楚对象拷贝和赋值

1. 赋值，两个对象变量的值（指针）指向同一个对象，改变其中一个，另一个也会影响
2. 拷贝，复制通过复制原对象生成一个新的对象，两者不相互影响。

### 浅拷贝

拷贝对象，正常理解就是我去内存中新开辟一块地方，然后把原对象中的属性获取出来放到新的地方。`Object.assign()` 来进行一个浅拷贝。

![sE7Lxl](https://blog-img-1256179672.cos.ap-shanghai.myqcloud.com/img/sE7Lxl.png)

如上如果说一个对象属性值都是基本数据结构，那通过浅拷贝就没什么问题。

![YCPerw](https://blog-img-1256179672.cos.ap-shanghai.myqcloud.com/img/YCPerw.png)

如果说属性值也是个对象，就会被相互影响。因为对象在堆中存储，属性值保存的是该对象的**地址指针**，所以浅拷贝到target对象时候保存的也是该指针。并没有为该对象内容在内存中开辟一个新的空间去保存一个新的对象内容。



### 深拷贝实现



