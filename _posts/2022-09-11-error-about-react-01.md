---
title:  "Manifest: Line: 1, column: 1, Syntax error."
layout: post
tags: Error
---

<p>
  깃허브에 리액트를 배포하려고 하는데 흰 배경만 뜬다. 개발자 도구를 눌러 어떤 오류가 발생했는지 확인해보니 <br>
  <strong>Manifest: Line: 1, column: 1, Syntax error.</strong>
</p>
  
![image](https://user-images.githubusercontent.com/108778921/189516802-c4b543bb-5f24-4e34-a0d1-e8aff3766b6f.png)

<p><strong>net::ERR_ABORTED 404</strong></p>
  
![image](https://user-images.githubusercontent.com/108778921/189516663-c6475c90-6cdb-44e9-bdbc-912d853bb3ab.png)<br>

  
<p>
  이렇게 두 가지 오류가 발생했다. 하나씩 해결해보자!
</p>

## 1. Manifest: Line: 1, column: 1, Syntax error.

<p> 1)  내 레파지토리에 있는 index.html 파일에 들어가서 link rel="manifest"를 찾는다. </p>
 
![image](https://user-images.githubusercontent.com/108778921/189516844-4fee2fae-6eb7-443d-b952-1e8c6934eff0.png)


<p> 2)  manifest 앞에 '/'만 추가 해주면 끝! </p>

![image](https://user-images.githubusercontent.com/108778921/189516935-56e15f36-bf55-4d2f-957b-a400f1808374.png)
