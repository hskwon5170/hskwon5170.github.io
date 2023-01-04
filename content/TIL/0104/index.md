---
emoji: 😃
title: Too many re-renders (SetState 관련 에러)
date: '2023-01-04 14:42:00'
author: 권형석
tags: blog
categories: Error
---

># 👨‍💻 에러상황
>![blog01.png](blog01.png)

<br/>

># 📚 어떤 에러인가?
>`리액트 무한루프 렌더링`
저장할 값을 setState에 넣을때 무한루프가 걸렸다.<br/>
에러가 발생하는 원인은 렌더 과정에서 state를 변화하는 함수가 있다면 리랜더링이 계속 일어나면서 발생하는 에러임을 확인했다.<br/>
(setState는 콜백으로 다시 렌더링을 트리거한다.)<br/>
setState는 비동기 방식으로 콜백큐가 모두 비워진 이후에 최종적으로 실행된다.<br/>
아마 state의 계속된 변경으로 이러한 에러가 발생된듯하다.

<br/>


<br/>

> ## 에러 핸들링 방법
>`useEffect를 이용`하고 sideEffect로부터 보호하기.<br/>
useEffect `내부`에서 setState 로직을 넣어줬더니 문제 해결.<br/>
의존성 배열을 빈배열로 놓았기 때문에 컴포넌트가 처음에 마운팅되고 난 이후에 로직실행.
>```javascript
>useEffect(()=>{
>    setMyData(data)
>},[])
>
>```

<br/>


> ## 💡컴포넌트가 리렌더링 되는 조건은...
>`state`가 변경되었을때<br/>
`부모컴포넌트`가 변경되었을때<br/>
`props`가 변경되었을때

<br/>


> ## 💡 추가로 알게된점
> 버튼 태그 부분에서 
>```
>const Counter = () => {
>    const [value, setValue] = useState(0);
>    return(
>        <div>
>            <div>{value}</div>
>            <button onClick={setValue(prev => prev+1)}>+1</button>
>            <button onClick={setValue(prev => prev-1)}>-1</button>
>        </div>
>    )
>}
>```
>`Arrow function 방식`으로 state를 변경해야 에러가 발생하지 않는다.
>```
><button onClick={()=>setValue(prev=>prev+1)}>+1</button>
>```
