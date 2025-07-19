---
{"dg-publish":true,"permalink":"/DevWiki/Sources/CSharp IDisposable이 반드시 구현해야하는 것/","noteIcon":"","created":"2024-12-01T17:25:23.000+09:00","updated":"2025-07-19T23:03:14.672+09:00"}
---

### Dispose가 수행해야 할 일들
- 비관리 및 관리 리소스 해제
- 객체가 이미 Dispose됨을 알리는 상태플래그 설정하여 Dispose 호출시 Object Disposed 예외 발생시키기
- GC.SuppressFinalize (this) 호출하여 소멸시 소멸자 호출 방지
### 주의사항
* Dispose나 Finalizer에서 리소스 해제 외의 다른작업은 절대로 수행해선 안된다
	* 소멸자 호출시 이미 객체 수집이 완료되었다고 판단되므로 그 이후로 생성되는 객체들은 수집이 되지 않을 수 있다.