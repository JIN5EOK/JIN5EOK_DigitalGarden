---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 TestRunner/","noteIcon":"","created":"2025-05-23T02:13:13.645+09:00","updated":"2025-07-19T22:58:36.996+09:00"}
---

### 특징
- 유닛테스트를 수행하는 라이브러리

### 테스트 메서드 속성
- `[Test]` : 일반 메서드
- `[UnityTest]` : 코루틴 방식 실행

### EditMode와 PlayMode
- EditMode
    - 어셈블리 정의 Platforms 체크박스 Editor만 체크
    - 게임을 실행하지 않고 수행
- PlayMode
    - 어셈블리 정의 의 Platforms 체크박스 Editor외의 항목 체크
    - 게임을 실행한채로 수행