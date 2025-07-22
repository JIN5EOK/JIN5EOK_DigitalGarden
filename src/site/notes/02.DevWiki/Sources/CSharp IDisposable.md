---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp IDisposable/","noteIcon":"","created":"2024-10-13T23:54:47.000+09:00","updated":"2025-07-19T22:58:36.946+09:00"}
---

> 😊 IDisposable 인터페이스를 상속받고 Dispose 함수를 재정의하여 메모리를 해제시키는 동작을 수행할 수 있다

IDisposable 인터페이스는 Dispose(bool disposing) 함수를 제공
* IDisposable안에 또 다른 IDisposable객체를 품고 있다면 품고 있는 객체들도 Dispose를 잊지 말고 해줘야 함
### bool disposing이 뭔데..?
* **True**
	* 관리되는 리소스,관리되지 않는  **리소스 모두 해제**
* **False 
	* **관리되지 않는 리소스만** 해제
### **관리되지 않는 리소스** 해제

관리되지 않는 리소스란 가비지 컬렉터가 자동으로 수거하지 않는 리소스들을 말한다
* 파일 핸들
* 네트워크 연결
* 데이터베이스 연결
### Using문과의 연계
* Using 내부서 IDisposable 객체 사용
* Using문을 나갈 때 해당 객체의 **Dispose함수가 호출**된다

### ETC
* 수동으로 Dispose를 수행한 후 GC.SuppressFinalize(this)를 호출하여 가비지 컬렉터가 해당 객체를 수거할 때 Dispose가 중복으로 호출되지 않도록 막을 수 있다
