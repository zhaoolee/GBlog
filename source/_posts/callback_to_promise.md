---
title: 将CallBack改写成Promise
date: 2019-07-01 07:05:30
top: 1
tags: 
- CallBack
- Promise
- Node.js
categories:
- 前端
---

> ![](https://raw.githubusercontent.com/zhaoolee/GraphBed/master/zhaoolee_images000002/dfa48c0ba968ca4d8c2f948f238692f3.png)


某天购物狂欢节, 你买了200件, 200件快递来自全国各地, 发往你在深圳的家, 为了节省快递成本, 快递小哥会等待200件快递全部到达网点后, 再开着小车一起送货

<!-- more -->

## 啥是回调函数?

- 我们可以把**回调函数**看做是**快递小哥**(回调函数=快递小哥)
- 把**互联网**看做是遍布全球的**快递系统**(互联网=快递系统)
- 把**网页数据**看做是**快递包裹**(网页数据=快递包裹)

- 把上面故事的送货策略抽象一下, 200件快递全部到达网点是事件A,  开着小车一起送货是事件B, 只有当事件A(200件快递全部到达网点)达成时, 才会进行事件B(开着小车一起送货), 事件B(开着小车一起送货)就是事件A(200件快递全部到达网点)的回调函数





CallBack回调函数是js的特色之一, 但CallBack回调方法, 非常容易造成**回调地狱(callback hell)**, **回调地狱**不仅形象丑陋,而且代码难以维护

- 以nodejs读取文件为例
```
const fs = require("fs");

// 回调函数的方式
fs.readFile('./zhaoolee.txt', (err, data)=>{
  if (err) {
    console.log(err);
  }else{
    let result = data.toString("utf8");
    
    console.log("CallBack方式读到的内容为==>>", result);
  }
})
```
## 用Promise改写上面的CallBack代码
```
const fs = require("fs");

// Promise的方式
async function myReadFile (){
  let result = await new Promise((resolve, reject)=>{
    fs.readFile('./zhaoolee.txt', (err, data)=>{
      resolve(data.toString("utf8"))
    })
  })

  console.log("Promise方式读到的内容为==>", result);
}

myReadFile();
```

关于上面👆代码出现的await和async两个词
- await是等待这一步完成后, 获得结果, 才能执行下一步
- async用于修饰函数, 如果函数内部出现了await关键词,函数前面必须添加async, 这是语法~

## 执行结果
> ![](https://raw.githubusercontent.com/zhaoolee/GraphBed/master/zhaoolee_images000002/cb9f9efdc99b789ec25492f9061d0dab.png)

- 本文章相关代码已经托管到github, 代码地址: [https://github.com/zhaoolee/GBlog/tree/master/Resource/callback_to_promise](https://github.com/zhaoolee/GBlog/tree/master/Resource/callback_to_promise)
