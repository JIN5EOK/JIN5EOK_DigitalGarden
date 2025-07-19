---
{"dg-publish":true,"permalink":"/DevWiki/Sources/유니티 UniRX/","noteIcon":"","created":"2024-10-13T18:55:36.000+09:00","updated":"2025-07-19T22:58:36.987+09:00"}
---

### UniRX가 뭘까?
- **Unity Reactive Extensions**의 약자
- 유니티에서 **리액티브 프로그래밍**을 수행하기 위한 **라이브러리**
- 사용법이 **LINQ 쿼리**와 깊게 연관되어 있음

### 리액티브 프로그래밍이란?
- **데이터와 이벤트**의 **변화와 흐름에 반응**하여 **이벤트를 비동기적으로 수행**하는 프로그래밍 패러다임

### 왜 UniRX를 사용해야 하는가?
Network 및 비동기 작업에 코루틴을 사용하곤 한다, 그러나 코루틴에는 아래와 같은 단점이 존재함

- 코루틴은 반환값을 지정할 수 없다
- yield return문을 try-catch 문으로 둘러쌀 수 없어 예외처리가 불가하다

### 예전만큼 유용하지는 않음에 주의한다
> 오래 전 async/await 패턴조차도 활용할 수 없었을 땐 굉장히 유용한 라이브러리, 지금은 async/await, UniTask, Awaitable등 다양한 대체제가 존재해 예전만큼 존재감 크지 않음

- **UniRX가 유용한 상황**
    - UniRX의 다양한 오퍼레이터를 상황에 알맞게 사용할 수 있는 경우
    - 만약 그 외의 상황이라면 오히려 구현이 복잡해질 수 있음

* Observable
	* Subject나 Observer의 구독을 받을 수 있고 구독자에게 데이터를 방출할 수 있다
* Observer
	* Observable이나 Subject를 구독하여 데이터를 받을 수 있다
* Subject
	* Observable과 Observer의 기능을 모두 수행한다, 데이터를 받을수도, 데이터를 방출할수도 있다