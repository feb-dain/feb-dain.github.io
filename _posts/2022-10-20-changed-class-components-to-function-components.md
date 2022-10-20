---
title: "클래스형 컴포넌트 함수형 컴포넌트로 바꾸기"
layout: post
tags: Study-Group
---

<a href="https://feb-dain.github.io/i-m-studying-react-with-study-mates-1/">리액트 스터디 1주 차 공부 완료</a>에서
말한대로 <span style="color:gray"> ― "Class형 컴포넌트를 유지 보수 해야할 일이 생길 수도 있으니 Class형 컴포넌트를 함수형 컴포넌트로 바꾸는 것도 공부하면 좋을 것 같다." ― </span>
클래스 컴포넌트를 함수형 컴포넌트로 바꾸는 연습을 했다. 






클래스형 컴포넌트 코드는 다음과 같다. 👇
```jsx
import React from "react";
import Notification from "./Notification";

const reservation = [
  { id: 1,
    message: "안녕하세요.",
  },
  { id: 2,
    message: "점심 시간입니다.",
  },
  { id: 3,
    message: "곧 미팅이 시작됩니다.",
  },
];

let timer;

class NotificationList extends React.Component {
  constructor(props){
    super(props);

    this.state = {
      notifications: [],
    };
  }

  componentDidMount(){
    const {notifications} = this.state;
    timer = setInterval(() => {
      if(notifications.length < reservation.length){
        const index = notifications.length;
        notifications.push(reservation[index]);
        this.setState({
          notifications: notifications,
        });
      }else{
        clearInterval(timer);
        this.setState({
          notifications: [],
        });
      }
    }, 1000);
  }

  render(){
    return (
      <div>
        {this.state.notifications.map((notification) => {
          return <Notification 
            message={notification.message}
            key={notification.id}
            id={notification.id} />
        })}
      </div>
    )
  }
}

export default NotificationList;
```

```jsx
import React from "react";
import styles from "../css/Notification.module.css"

class Notification extends React.Component {
  constructor(props){
    super(props);

    this.state = {};
  }

  // Lifecycle
  componentDidMount(){
    console.log(`${this.props.id} componentDidMount()`);
  }
  componentDidUpdate(){
    console.log(`${this.props.id} componentDidUpdate()`);

  }
  componentWillUnmount(){
    console.log(`${this.props.id} componentWillUnMount()`);
  }
  
  render() {
    return (
      <div className={styles.wrapper}>
        <span className={styles.messageTxt}>{this.props.message}</span>
      </div>
    );
  }
}

export default Notification;
```
<br>
위의 코드를 함수형 컴포넌트로 바꾸었다. 👇

```jsx
import { useState, useEffect } from "react";
import styled from "styled-components";

const Msg = styled.p`
  margin: 2rem 0;
`;
const Title = styled.h3`
  margin: 4rem 0 3.2rem;
  font-weight: 700;
  font-size: 2rem;
`;

const Notification = () => {
  const txt = ["안녕하세요.", "점심시간입니다.", "퇴근하세요."];
  const [notifications, setNotification] = useState([]);

  let timer;

  useEffect(() => {
    const index = notifications.length;
    if(notifications.length < txt.length){
        timer = setInterval(() => {
            setNotification([...notifications, txt[index]])
        }, 1000);
    } 
    return () => clearInterval(timer);

}, [notifications])

  return (
    <div>
      <Title>📌 알람 📌</Title>
      {notifications.map((msg, idx) => {
        return <Msg key={idx}>{msg}</Msg>
      })}
    </div>
  );
};

export default Notification;
```
최종 코드인데, 최종 코드는 스터디원(**감사합니다. 쩨로님!**)의 코드를 참고했다. 
<br>

처음 내가 짠 코드는 아래과 같다. useInterval을 응용해서 만들었다.
동작은 되는데... 코드가 좋아보이질 않았다. 😂 분명 더 간결한 방법이 있을 거라고 생각했다.
정말 골치가 아팠는데, 다른 스터디원의 코드를 보고 힌트를 얻었다.

스터디에서 클래스형 컴포넌트를 함수형 컴포넌트로 바꿔보자고 제안하길 잘했다. 😊
```jsx
import { useState, useRef, useEffect } from "react";
import styled from "styled-components";

const Msg = styled.p`
  margin: 2rem 0;
`;
const Title = styled.h3`
  margin: 4rem 0 3.2rem;
  font-weight: 700;
  font-size: 2rem;
`;

const NotificationListCopy = () => {
  const txt = ["안녕하세요.", "점심시간입니다.", "퇴근하세요."];

  const [count, setCount] = useState(0);
  const [notif] = useState([]);
  const callback = () => setCount(count + 1);
  const savedCallback = useRef();

  useEffect(() => {
    savedCallback.current = callback;
  }, [txt]);

  useEffect(() => {
    function tick() {
      savedCallback.current();
      if (notif.length < txt.length) {
        const index = notif.length;
        notif.push(txt[index]);
      }
    }
    if (2000 !== null) {
      let timer = setInterval(tick, 2000);
      return () => clearInterval(timer);
    }
  }, [2000]);

  return (
    <div>
      <Title>📌 알람 📌</Title>
      {notif.map((msg, idx) => {
        return <Msg key={idx}>{msg}</Msg>
      })}
    </div>
  );
};


export default NotificationListCopy;
```

<br>
<br>
