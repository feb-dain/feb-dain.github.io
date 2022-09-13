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
let a = c; ❌️    //재선언 불가능

let a = b;
a = c;    //재할당 가능
```

```
var a = b;
var a = c;
a = d;
//재선언, 재할당 가능
```

따라서 실수를 하더라도 알아차릴 수 없을 수 있으니 var 사용은 지양할 것.<br>
**기본적으로 const를 사용하고, 변수의 값을 바꿀 일이 있다면 let를 사용할 것.**
