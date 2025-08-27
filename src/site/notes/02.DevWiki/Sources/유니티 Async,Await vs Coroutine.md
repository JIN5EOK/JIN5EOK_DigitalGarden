---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 Async,Await vs Coroutine/","noteIcon":""}
---


# Async,Await vs Coroutine

## 🔎 각각의 특징 알아보기

* [[02.DevWiki/Sources/유니티 코루틴\|유니티 코루틴]]
* [[02.DevWiki/Sources/유니티에서의 Async,Await\|유니티에서의 Async,Await]]

## 🙄 현 시점에서는 코루틴을 사용할 이유가 크게 없다

* 코루틴의 가장 큰 장점은 유니티 엔진과의 동기화와 쉬운 난이도임
	* **난이도?**
		* async await 패턴도 비동기 코드의 가독성 증가를 통해 나온 기법이라 엄청나게 어려운 개념은 아님
	* **유니티엔진과의 동기화?**
		* **MainThreadDispatcher**, **UniTask**나 **Awaitable**등 해결 방법들이 존재함

* **하지만..!**
	* **Awaitable은 2023.1버전** 부터 지원되어 아직 사용하지 못하는 버전들이 많고
	* **UniTask는 서드파티 플러그인**이라 모든 프로젝트에 사용됨을 보장할 수 없고
	* **MainTrheadDispatcher**는 사용자가 구현해야 하는 기능임
	* 따라서 여러 환경의 불특정 다수가 사용할걸 염두에 둔 플러그인이나 프레임워크등의 기능들은 코루틴 사용을 지원하는것도 나쁘지 않다는 생각..

## 💡결론

- **코루틴**
	- **간단한 시간 지연**이나 **유니티 API를 사용하는 간단한 비동기 로직**에 제한적으로 사용
- **Async/Await**
	- **복잡한 비동기 로직**, **값 반환**, **예외 처리**가 중요한 경우, 혹은 그 외!
	- **MainThreadDispatcher**, **UniTask**나 **Awaitable**등을 이용하면 Async/Await을 사용하면서도 유니티 API 사용 제약을 덜 수 있음

---
### 관련 문서
[[02.DevWiki/Sources/유니티에서의 메인스레드와 멀티스레딩\|유니티에서의 메인스레드와 멀티스레딩]]
[[02.DevWiki/Sources/유니티에서의 Async,Await\|유니티에서의 Async,Await]]
[[02.DevWiki/Sources/유니티 코루틴\|유니티 코루틴]]