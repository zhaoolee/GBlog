---
title: 以import from与export default结合方式同时导出多个变量
date: 2019-07-18 07:05:30
top: 1
tags: 
- export default
- es6
- Node.js
categories:
- 前端
---



- export default 默认无法同时导出多个变量
- export default 导出变量的方式非常优雅, 当使用导出变量时, 无需了解导出变量原来的命名
- export 可以导出多个变量, 当使用导出变量时, 需要了解导出变量原来的命名

- main.msj

```main.mjs
import function_zhaoolee_info from './zhaoolee_info.mjs';
let {name, age} = function_zhaoolee_info();

// 运行方式为: node --experimental-modules main.mjs
console.log(name,"的年龄为", age);
```
- zhaoolee_info.mjs

```zhaoolee_info.mjs
export default ()=>{
  let name="zhaoolee";
  let age = new Date().getFullYear() - 1995;
  return {name, age};
}
```

- 运行命令 `node --experimental-modules main.mjs`

> ![](https://user-images.githubusercontent.com/15868458/61421636-8e2caa80-a93a-11e9-9f02-dd6694efaa7a.png)


## 小结
当我们需要以import from与export default结合方式, 同时导出多个变量时,函数不失为一种优雅简洁的方式~


## 相关资源下载
```
https://github.com/zhaoolee/GBlog/tree/master/resource/import_export_function
```

