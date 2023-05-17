```
---
emoji: 🧢
title: React Suspense
date: '2023-05-17 20:00:00'
author: hs
tags: react frontend suspense
categories: react
---
```

![suspense.png](suspense.png)

## React Suspense 란...

리액트의 `suspense`는 비동기적으로 `로딩`되는 컴포넌트를 처리할 수 있는 기능을 제공한다.
Suspense는 아직 렌더링이 준비되지 않은 컴포넌트가 있을때 로딩 화면을 보여주고 로딩이 완료되면 해당 컴포넌트를 보여주는 `React에 내장`되어 있는 기능이다.

## Suspense의 fallback?

suspense는 특정 컴포넌트가 로딩중일 때 보여줄 대체 내용을 제공하는 `fallback` 속성을 가지고 있다.
`fallback`은 한 컴포넌트 내부의 자식 컴포넌트가 아직 로딩되지 않았을 때 보여줄 컨텐츠 제공 속성이다.

일반적으로 `로딩 메세지` 혹은 `로딩 스피너`를 보여준다.

## Suspense / fallback의 장점

1. `suspense와 fallback 없이` 일시적으로 `빈 화면`을 마주해야 하는 불상사를 없앨 수 있다.
2. 사용자는 컴포넌트가 로딩중임을 인식할 수 있다.
3. 로딩이 완료될 때까지 대기할 수 있으며 사이트 이탈률이 줄어든다.

```javascript
// ✅ REACT에서 기본으로 제공하는 Suspense

import React, { Suspense } from 'react';
import { Spinner } from '@chakra-ui/react'

const MyComponent = React.lazy(() => import('./MyComponent'));

function App() {
  return (
    <div>
      <h1>앱</h1>
    // ✅ fallback 옵션으로 chakra-ui의 spinner를 입력해주었다.
      <Suspense fallback={<Spinner />}
        <MyComponent />
      </Suspense>
    </div>
  );
}

export default App;

```

<br/>

## JSON Placeholder를 이용한 예시

```javascript
import React, { Suspense, useEffect, useState } from 'react';
import axios from 'axios';

const UserList = React.lazy(() => import('./UserList'));

function App() {
  const [users, setUsers] = useState([]);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    async function fetchUsers() {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users');
        setUsers(response.data);
        setIsLoading(false);
      } catch (error) {
        console.log('Error fetching users:', error);
      }
    }

    fetchUsers();
  }, []);

  return (
    <div>
      <h1>User List</h1>
      <Suspense fallback={<Spinner />}>
        {isLoading ? <Spinner /> : <UserList users={users} />}
      </Suspense>
    </div>
  );
}

function Spinner() {
  return <div>Loading...</div>;
}

export default App;
```

<a href="https://jsonplaceholder.typicode.com/users">JSON Placeholder</a>를 이용해 userList를 fetch해올 동안 로딩스피너가 나타나고, fetch가 전부 끝났을때 setIsLoading을 false로 set 해줘서 UserList 컴포넌트가 나타나도록 작성했다.

```toc

```
