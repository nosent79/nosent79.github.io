---
layout: post
title: 입문자를 위한 Disqus 연결하기
category: disqus
tags: [disqus, jekyll, blog]
comments: true
---

> '기록은 기억을 지배한다'

<br>
# 들어가기

- 많은 개발자가 *.github.io 를 사용하기에 나도 한 번 사용해 보려고 한다.
- 이번 포스팅은 댓글 플랫폼인 DISQUS를 붙여보는 것이다.


---

## 개요
- 아래 단계를 따라하시면 됩니다.

1. disqus 회원가입 (oauth2 가능)
2. ADMIN 메뉴 이동
3. SITE 만들기
4. Shortname 확인
5. _config.yml에 disqus short-name 기재
6. 끝

---

## 1. 회원가입
- [DISQUS](https://disqus.com/)

---

## 2. ADMIN 메뉴 이동
- 오른쪽 상단에 Admin 텍스트 클릭

---

## 3. SITE 만들기
- 왼쪽 상단 DISQUS 로고 이미지 옆 Your Sites 클릭하여 사이트를 생성한다.

---

## 4. Shortname 확인
- 3번 단계에서 Website Name 에 입력한 값에 따라 Shortname이 자동 생성된다.
- 위치는 Your Sites 클릭 - Edit Settings - Configure Disqus for Your Site 

---

## 5. _config.yml에 disqus short-name 기재
- 기본적으로 jekyll 테마를 사용하면 _config.yml에 `disqus:` 값만 넣어주면 연동이 된다.
이때, 반드시 Shortname을 기재한다.

---

## 덧붙이기
- 가급적 이미지를 통해 쉽게 설명하고 싶었으나 텍스트로만 설명할 만큼 어렵지 않다.