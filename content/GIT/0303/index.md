---
emoji: πΆ
title: git branch
date: '2023-03-03 13:10:00'
author: κΆνμ
tags: git
categories: git gitbranch gitflow
---

> ![gitea.png](gitea.png) > <span style="color: #808080">νμ¬μ μμ¬ νκ³ , μ μνκ³ , νλ‘μ νΈλ μννλλΌ μ λ§ μ€λλ§μ λΈλ‘κ·Έμ κΈμ λ¨κΈ΄λ€.π­ μμΌλ‘ λ§€μΌ μμνκ²λλ§ μκ²λ, μ΅λν, κ³΅λΆν λ΄μ©μ κΈ°λ‘νκ³ μ νλ€.
> </span>

## π Git λΈλμΉ - rebaseμ μ€μμ±

- λΆνΈμΊ νμμ ννλ‘μ νΈλ₯Ό μννλ©΄μ, git mergeλ§ μ¬μ©νμλ κΈ°μ΅μ΄ μλ€.
- νμ¬μ μμ¬νκ³  λ ν, μ¬λ¬λͺμ΄ νλμ νλ‘μ νΈμ ν¬μλμλλ° λ¨μν `git merge`λ§ μ¬μ©ν  κ²½μ°, μ¬λ¬ λ¬Έμ μ μ΄ μ λ°λ  μ μμμ μΈμνκ² λμλ€.
  <br/>
  ![complecated.png](complecated.png)
  <span style="color: #808080">(λ³΅μ‘νκ² μ»€λ°κ·Έλνκ° μ½νμλ λͺ¨μ΅)</span>
  <br/>

> π₯΅ λ¬Έμ μ 

1. μ»€λ° κ·Έλνκ° μ½νμμ΄ λ³κ²½ μ¬ν­μ νμνκΈ° νλ¦
2. μλλ°©μ΄ μμνμ¬ μ»€λ°ν κ²°κ³Όλ¬Όμ λμ μ»€λ°μ΄ λ¬λΌλΆμ΄ μ½νμλ(...) λͺ¨μ΅
   <br/>

> ![down.png.png](down.png.png)
> κ·Ήλ¨μ μΌλ‘, Mergeλ§ ν  κ²½μ°, `μμ²­λκ² λ³΅μ‘ν μ»€λ° νμ€ν λ¦¬`κ° μμ±λ  μ μλ€.
> <br/>

> β μ΄λ° κ²½μ°, μ΄μ  κ·Έλνμμ μλ¬κ° λ°μνμ κ²½μ°, μ»€λ°μ μ μΆμ ν  μ μμκΉ?

<!-- <hr/> -->

## β Git Merge

Git Mergeλ μ¬λ¬ branchλ€μ΄ μ‘΄μ¬ν  λ, νλμ branchλ‘ ν΅ν©μν€λ κ°λμ΄λ€.

## β Git Rebase

Git Rebaseλ branchμ baseλ₯Ό μ¬μ€μ νλ€λ κ°λμ΄λ€.

> μ¦, νλμ λΈλμΉκ° λ€λ₯Έ λΈλμΉμμ νμλμ λμ¨ κ²½μ°, λ€λ₯Έ λΈλμΉμμ μ§νλ μ»€λ°μ `λ€μ κ°μ Έμ` baseλ₯Ό `μ¬μ€μ ` νλκ².

λμ μλλ°©μ΄ λμμ μμμ νκ³ , μλλ°©μ΄ λ¨Όμ  μ»€λ°μ νλ€λ©΄, `μλλ°©μ μλ‘μ΄ μ»€λ°μ base`λ‘ νλ λ°©μμΌλ‘ λ³ν© μ, conflict μμ΄ λμ μμλ¬Όμ λ°μν  μ μλ€.

> ![updated.png](updated.png)

<span style="color: #808080">νμ¬μμ μ§νμ€μΈ νλ‘μ νΈμ μ»€λ° κ·Έλν</span>

<br/>

### Rebase κ³Όμ 

```
git checkout fe/contract
git add
git commit
git pull -r upstream 'μκ²©λΈλμΉ'
git push 'origin λΈλμΉ'
pull request
```

```
π§βπ git pull -r upstream 'μκ²©λΈλμΉ'λ...
push μ΄μ μ λ€λ₯Έ μμ κ²°κ³Όλ¬Όμ pullνλ©΄μ -rμ΅μ(rebase)μ μ μ©νλ λ°©μ
```

#### reference

https://www.atlassian.com/ko/git/tutorials/rewriting-history/git-rebase

```toc

```
