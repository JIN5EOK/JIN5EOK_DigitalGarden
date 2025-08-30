---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp IDisposable/","noteIcon":""}
---

# IDisposable

> **관리되지 않는 리소스**를 해제시키는 Dispose() 함수를 제공하고 구현할 수 있도록 한다
### 관리되지 않는 리소스?

관리되지 않는 리소스란 가비지 컬렉터가 자동으로 수거하지 않는 리소스들을 말한다
* 파일 핸들
* 네트워크 연결
* 데이터베이스 연결

### Using문과의 연계
* **Using 내부서 IDisposable 객체 사용**
* Using문을 나갈 때 해당 객체의 **Dispose함수가 호출**된다

### Dispose 인터페이스에 대한 권장 구현으로 표준 Dispose패턴이 존재

* [[02.DevWiki/Sources/CSharp 표준 Dispose 패턴\|CSharp 표준 Dispose 패턴]]을 참고하자
