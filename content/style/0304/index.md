---
emoji: 🎇
title: Tailwind CSS 사용기
date: '2023-03-03 14:32:00'
author: 권형석
tags: style tailwind
categories: style
---

![tailwindcss.png](tailwindcss.png)

## 요즘 트렌드인 tailwind css

부트캠프에서부터 지금까지 프론트엔드 스타일링 라이브러리중 하나인 `@Emotion/styled-components`를 사용해왔다. 따로 `styles.ts`파일을 만들고, 그곳에 스타일링을 지정한 이후 사용할 컴포넌트로 `import`해온 뒤 적용해주는 방식으로. 하지만 스타일을 수정할 필요가 있는 경우, 한 depth를 더 들어가서야 스타일 수정이 가능한 구조였고 매번 코드 유지보수성과 가독성을 위해 `변수명`을 고민했어야 했다.

현재 입사한 회사의 프론트엔드 파트에서는 스타일링을 위해 `tailwind css`를 사용하고 있었고, 습득할 필요성이 생겼다. 어느정도 사용에 익숙해지고 나니 변수명을 고민할 필요도 없고, depth를 더 들어갈 필요도 없이 빠른 스타일링이 가능했다.

## Tailwind CSS란 무엇인가?

Tailwind CSS는 Utility-First 컨셉을 가진 CSS 프레임워크다. 부트스트랩과 비슷하게 `m-1`, `flex`와 같이 미리 세팅된 유틸리티 클래스를 활용하는 방식으로 HTML 코드 내에서 스타일링을 할 수 있다.

✍️ 예시로 똑같은 스타일을 `styled-components`와 `tailwind css`를 이용해서 적용해보면...
![example.png](example.png)

## 1.Styled-components

```
** style.ts **

export const RoundedBox = styled.div`
    border-radius = 10px;
    border: 2px solid black;
    display:flex;
    flex-direction:column;
    justify-contents:center;
    align-items:center;
    background-color:skyblue;
    padding:30px
`

export const FirstDiv = styled.div`
    font-weight:bold;
    font-size:30px;
    color:white;
`

export const SecondDiv = styled.div`
    color:#58d480;
    font-weight:bold;
`

export const
```

```
** index.ts **

import * as S from 'styles.ts'

<S.RoundedBox>
    <S.FirstDiv>Hello World!</S.FirstDiv>
    <S.SecondDiv>Fun coding!</S.SecondDiv>
</S.RoundedBox>
```

## 2.Tailwind css

```
** tailwind css **
    <div className="rounded-xl border-solid border-black border-2 flex flex-col justify-center items-center w-fit bg-blue-400 p-3 text-white">
        <div className="font-bold text-[30px]">Hello World!</div>
        <div className="text-green-400 font-bold">Fun coding!</div>
      </div>

```

> html 코드의 `className`에 바로 스타일링을 입혀주는 방식이다.

> 변수명을 고민할 필요도 없고, 스타일링을 위해 추가적인 파일을 생성할 필요가 없다.
