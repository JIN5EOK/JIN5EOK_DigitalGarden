---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp IDisposable/","noteIcon":"","created":"2024-10-13T23:54:47.000+09:00","updated":"2025-08-16T22:52:55.123+09:00"}
---

# IDisposable

> **관리되지 않는 리소스**를 해제시키는 Dispose() 함수를 제공하고 구현할 수 있도록 한다
### 관리되지 않는 리소스?

관리되지 않는 리소스란 가비지 컬렉터가 자동으로 수거하지 않는 리소스들을 말한다
* 파일 핸들
* 네트워크 연결
* 데이터베이스 연결

### Using문과의 연계
* Using 내부서 IDisposable 객체 사용
* Using문을 나갈 때 해당 객체의 **Dispose함수가 호출**된다

### ETC
* 수동으로 Dispose를 수행한 후 GC.SuppressFinalize(this)를 호출하여 가비지 컬렉터가 해당 객체를 수거할 때 Dispose가 중복으로 호출되지 않도록 막을 수 있다

## Dispose가 수행해야 할 일들
- 비관리 리소스 해제
- 객체가 이미 Dispose됨을 알리는 상태플래그 설정하여 Dispose 호출시 Object Disposed 예외 발생시키기
- GC.SuppressFinalize (this) 호출하여 소멸시 소멸자 호출 방지

### 주의사항
* Dispose나 Finalizer에서 리소스 해제 외의 다른작업은 수행해선 안된다
	* 소멸자 호출시 이미 객체 수집이 완료되었다고 판단되므로 그 이후로 생성되는 객체들은 수집이 되지 않을 수 있다.

---
### 관련 문서
[[02.DevWiki/Sources/CSharp 표준 Dispose 패턴\|CSharp 표준 Dispose 패턴]]
[[02.DevWiki/Sources/CSharp IDisposable이 반드시 구현해야하는 것\|CSharp IDisposable이 반드시 구현해야하는 것]]