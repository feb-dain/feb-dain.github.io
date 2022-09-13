---
title:  "const, let and var의 차이점"
layout: post
tags: JavaScript
---

* const &nbsp;&nbsp;:&nbsp;&nbsp; 재선언 불가능, 재할당 불가능 
*  let &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  :&nbsp;&nbsp;  재선언 불가능, 재할당 가능  
*  var  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:&nbsp;&nbsp;  재선언 가능, 재할당 가능    

```
let a = b;
let a = c; ❌️ //재선언 불가능

let a = b;
a = c; //재할당 가능
```

```
var a = b;
var a = c;
a = d;
//재선언, 재할당 가능
```
