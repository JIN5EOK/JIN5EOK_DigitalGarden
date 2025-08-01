---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/UML - 클래스 다이어그램/","noteIcon":"","created":"2024-10-13T15:17:23.000+09:00","updated":"2025-07-20T02:14:54.298+09:00"}
---

# 클래스 다이어그램

> 클래스의 구조와 관계를 시각적으로 표현하여 시스템의 정적 구조를 보여줌

## 접근 제한자 기호

- Public
- : private
- #: protected

## 관계 화살표

- **화살표 방향 = 관계의 방향**
    - 의존자 -> 의존대상
- **다중성 표기**
    - **1** : **1개**의 인스턴스
    - **0..1** : **0~1개**의 인스턴스
    - **1..\**: **최소 1개 이상**의 인스턴스

### 연관, 집합, 합성

- **연관 관계**
    - **—>**
    - 특정 클래스를 **멤버**로 가짐
    - 화살표가 **없으면 양방향 참조관계**
- **집합 관계**
    - **◇—>**
    - **1:N 연관**
- **합성 관계**
    - **◆—>**
    - **1:N** 연관
    - **생명주기**를 함께 함
    - 1이 죽으면 N도 죽는다

### 의존

- **의존 관계**
    - **-->**
    - **함수 파라미터, 리턴 값**에 의존

### 상속과 실체화

- **상속 관계**
    - **—▷**
    - 클래스 상속
- **실체화 관계**
    - **- ▷**
    - 인터페이스 상속

### 뭔가 규칙이 있는 듯?

- 연관,의존 : >
- 상속 : ▷
- 끈끈함 : —
- 덜끈끈함 : ---