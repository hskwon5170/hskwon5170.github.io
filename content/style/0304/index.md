---
emoji: π
title: Tailwind CSS μ¬μ©κΈ°
date: '2023-03-03 14:32:00'
author: κΆνμ
tags: style Tailwind-CSS
categories: style
---

![tailwindcss.png](tailwindcss.png)

## μμ¦ νΈλ λμΈ Tailwind CSS

λΆνΈμΊ νμμλΆν° μ§κΈκΉμ§ νλ‘ νΈμλ μ€νμΌλ§ λΌμ΄λΈλ¬λ¦¬μ€ νλμΈ `@Emotion/styled-components`λ₯Ό μ¬μ©ν΄μλ€.

> λ°λ‘ `styles.ts`νμΌμ λ§λ€κ³ , κ·Έκ³³μ μ€νμΌλ§μ μ§μ ν μ΄ν μ¬μ©ν  μ»΄ν¬λνΈλ‘ `import`ν΄μ¨ λ€ μ μ©ν΄μ£Όλ λ°©μμΌλ‘.

νμ§λ§ μ€νμΌμ μμ ν  νμκ° μλ κ²½μ°, ν depthλ₯Ό λ λ€μ΄κ°μμΌ μ€νμΌ μμ μ΄ κ°λ₯ν κ΅¬μ‘°μκ³  λ§€λ² μ½λ μ μ§λ³΄μμ±κ³Ό κ°λμ±μ μν΄ `λ³μλͺ`μ κ³ λ―Όνμ΄μΌ νλ€.

νμ¬ μμ¬ν νμ¬μ νλ‘ νΈμλ ννΈμμλ μ€νμΌλ§μ μν΄ `tailwind css`λ₯Ό μ¬μ©νκ³  μμκ³ , μ΅λν  νμμ±μ΄ μκ²Όλ€. μ΄λμ λ μ¬μ©μ μ΅μν΄μ§κ³  λλ λ³μλͺμ κ³ λ―Όν  νμλ μκ³ , depthλ₯Ό λ λ€μ΄κ° νμλ μμ΄ λΉ λ₯Έ μ€νμΌλ§μ΄ κ°λ₯νλ€. μμ²­λ μ₯μ .

## Tailwind CSSλ λ¬΄μμΈκ°?

Tailwind CSSλ Utility-First μ»¨μμ κ°μ§ CSS νλ μμν¬λ€. λΆνΈμ€νΈλ©κ³Ό λΉμ·νκ² `m-1`, `flex`μ κ°μ΄ λ―Έλ¦¬ μΈνλ μ νΈλ¦¬ν° ν΄λμ€λ₯Ό νμ©νλ λ°©μμΌλ‘ HTML μ½λ λ΄μμ μ€νμΌλ§μ ν  μ μλ€.

βοΈ μμλ‘ λκ°μ μ€νμΌμ `styled-components`μ `tailwind css`λ₯Ό μ΄μ©ν΄μ μ μ©ν΄λ³΄λ©΄...
![why.png](why.png)

## 1.Styled-components

```
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
```

![code1.png](code1.png)

## 2.Tailwind css

<!-- ```
** tailwind css **

<div className="rounded-xl border-solid border-black border-2 flex flex-col justify-center items-center w-fit bg-blue-400 p-3 text-white">
    <div className="font-bold text-[30px]">Hello World!</div>
    <div className="text-green-400 font-bold">Fun coding!</div>
</div>
``` -->

![carbon6.png](carbon6.png)

> π μ½λ λΆλμ΄ μ€μ΄λ€μκ³ , λ³μλͺμ κ³ λ―Όν  νμλ μμλ€. λν, CSS νμΌμ μΆκ°λ‘ μμ±νμ§λ μμλ€!

μ€νμΌ μ½λλ HTML μ½λ μμ μκΈ° λλ¬Έμ HTMLνμΌκ³Ό CSS νμΌμ λ³λλ‘ κ΄λ¦¬ν  νμκ° μλ€. κ·Έ λλΆμ <strong>HTML-CSSλ₯Ό μλ€κ°λ€νλ©° μκ°μ μ°κ±°λ, VSμ½λ νλ©΄μ λΆν ν΄μ μ¬μ©νμ§ μμλ λλ€.</strong>

λν, <strong>νκ·Έμ λ³μλͺμ κ³ λ―Όν  νμκ° μλ€!</strong> μ¬λ¬ μ€νμΌλ§ λ°©λ²λ‘ μ΄ λμ¬ μ λλ‘ κΉλ€λ‘μ΄ κ²μ΄ ν΄λμ€λͺμ μ§λκ²μΈλ°, Tailwind CSSλ₯Ό μ¬μ©νλ©΄ νκ·Έμ ν΄λμ€λͺμ μ§λ κ²μμ ν΄λ°©λλ―λ‘ `Wrapper`, `InnerWrapper`, `Container`, `SmallWrapper` λ±μ ν΄λμ€λͺμ κ³ λ―Όνμ§ μμλ λλ€.

![intelli.png](intelli.png)
border-radiusκ° `rounded`, flex-direction:columnμ΄ `flex-col` λ± κΈ°μ‘΄κ³Ό μμ΄ν ν΄λμ€λͺμ΄ μ‘΄μ¬νλ€. λ°λΌμ Tailwind CSSκ° μ κ³΅νλ ν΄λμ€λ₯Ό νμ΅ν΄μΌ νκ³  μ΅μν΄μ ΈμΌ νμ§λ§, `Intelli Sense`νλ¬κ·ΈμΈμ΄ μ κ³΅λκ³  μμ΄ μ΅μν΄μ§λ§ κ³΅μ λ¬Έμ κ°μ΄λ μμ΄λ λΉ λ₯΄κ² μ€νμΌλ§ν  μ μλ€.

λν μ΄μ μλ λ°μν λμμΈμ μν΄ λ°λ‘ media-query νμΌμ μμ±νμ¬ import ν΄μ μ¬μ©νμλλ°, Tailwind CSSλ λ°μν λμμΈμ μν ν΄λμ€λͺλ μ κ³΅ν΄μ€λ€κ³  νλ€. λ°λΌμ νμ¬ μ§νμ€μΈ νλ‘μ νΈμ λ°μν λμμΈμ Tailwind CSSλ₯Ό μ΄μ©ν΄μ ν΄λ³Ό μκ°.

![profile.png](profile.png)
<br/>
![code.png](code.png)

<!-- ```
   <div className="bg-black py-20 px-20 flex justify-center items-center">
        <div className="bg-white overflow-hidden rounded-3xl shadow-3xl w-[330px]">
          <div className="bg-gray-400 py-10">
            <span className="text-white text-2xl ml-5">Profile</span>
          </div>
          <div className="rounded-3xl p-6 bg-white relative -top-5">
            <div className="flex relative -top-16 items-end justify-between">
              <div className="flex flex-col items-center">
                <span className="text-sm text-gray-500">Orders</span>
                <span className="font-medium">340</span>
              </div>
              <div className="h-24 w-24 bg-purple-500 rounded-full"></div>
              <div className="flex flex-col items-center">
                <span className="text-sm text-gray-500">Spent</span>
                <span className="font-medium">$340</span>
              </div>
            </div>
            <div className="flex flex-col items-center -mt-10 -mb-5">
              <span className="text-lg font-medium">HYUNG SEOK</span>
              <span className="text-sm text-gray-500">Mr.</span>
            </div>
          </div>
        </div>
      </div>
``` -->

```toc

```
