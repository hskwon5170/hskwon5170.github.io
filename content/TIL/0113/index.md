---
emoji: ๐
title: ReferenceError - localStorage is not defined
date: '2023-01-13 14:00:00'
author: ๊ถํ์
tags: blog, frontend
categories: Error
---

![1.png](1.png)

# `localStorage is not defined `

> next.js (ssr)๋ฅผ ์ด์ฉํด์ ๊ฐ๋ฐํ๋ค ๋ง๋ ์๋ฌ  
> <br/>

## โ ์์ธ

localStorage๊ฐ `window`๊ฐ์ฒด์ ์ ์๋์ด ์์ง ์๊ณ  next.js๊ฐ ํด๋ผ์ด์ธํธ ์ฌ์ด๋ ๋ ๋ ์ด์ ์ ์๋ฒ ์ฌ์ด๋ ๋ ๋๋ฅผ ์ํํ๊ธฐ ๋๋ฌธ์ด๋ค.

<br/>

## โ ํด๊ฒฐ

window ๊ฐ์ฒด์ ์กด์ฌํ๋์ง ์ฌ๋ถ๋ฅผ ์ดํ ์ดํ์ ์ ๊ทผํ๋ฉด ์๋ฌ๋ฉ์ธ์ง๊ฐ ๋ฐ์ํ์ง ์๋๋ค. `์กด์ฌํ๋์ง๋ฅผ ๋จผ์  ํ์ธํ ๊ฒ!`

```
const readFromLocalStorag = () => {
  const arrays = typeof window !== 'undefined' ? localStorage.getItem("array") : null;
  return arrays ? JSON.parse(arrays) : [];
};
```
