---
emoji: 🪐
title: Context API
date: '2023-01-12 13:28:00'
author: 권형석
tags: blog, frontend
categories: ContextAPI,전역상태관리
---

# Context api

> props는 자신의 부모 컴포넌트로부터 받는 데이터이다.

매우 많은 컴포넌트들이 존재한다면 props를 넘겨줄 때 props drilling 현상이 일어날 수 있다.

> #### ☠️ 만약 컴포넌트들의 구조가 매우 복잡해서, `1번 컴포넌트의 자식 컴포넌트 -> 자식의 자식 컴포넌트 -> ....` 로 컴포넌트가 중첩되어 있는 구조인 상태라면?

props만으로 전달받아 후순위의 컴포넌트에서 사용한다면, 그 사이에 있는 어마어마하게 많은 컴포넌트는 단순한 `데이터 다리`역할을 하는것이다.

<strong> 이때 Context API를 통해, 즉 전역상태를 통해 이러한 문제점을 해결할 수 있다.<strong/>

- \_app.ts 파일에서 context Provider로 컴포넌트의 최상위부분을 묶어준다.

```
[_app.tsx]

import { createContext, useContext } from "react";

export const MyContext = createContext();

function MyApp({ Component, pageProps }) {
 return (
   <MyContext.Provider value="안녕안녕안녕">
     <Component {...pageProps} />
   </MyContext.Provider>
 );
}

export default MyApp;
```

- 그 이후, MyContext의 value를 받아 사용할 컴포넌트에서 useContext 훅을 이용해 정의한 context를 불러와서 사용하면 된다.
- props로 값을 넘겨받지 않고도 전역적으로 value를 불러올 수 있다.

```
import React from "react";
import { useContext } from "react";
import { MyContext } from "../../../../pages/_app";

export default function First() {
 const value = useContext(MyContext);
 return <div>{value}</div>;
}
```

#### 정보를 찾아보며 전역상태관리 라이브러리들도 context API를 활용하여 만들어졌다는것을 알게되었다.

- 기존에 사용하던 recoil도 컴포넌트들을 RecoilRoot로 묶어주는 방식을 통해 전역으로 상태를 관리했었는데, 고개가 끄덕여지는 부분.
