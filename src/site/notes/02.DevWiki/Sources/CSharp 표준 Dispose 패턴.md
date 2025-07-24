---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 표준 Dispose 패턴/","noteIcon":"","created":"2025-05-23T01:32:08.072+09:00","updated":"2025-07-19T22:58:36.969+09:00"}
---


> Dispose 패턴은 _**종료자 및 IDisposable 인터페이스의 사용 및 구현을 표준화하기 위한 것** 입니다.
> [https://learn.microsoft.com/ko-kr/dotnet/standard/design-guidelines/dispose-pattern#basic-dispose-pattern](https://learn.microsoft.com/ko-kr/dotnet/standard/design-guidelines/dispose-pattern#basic-dispose-pattern)


```bash
public class DisposableResourceHolder : IDisposable {

    private SafeHandle resource; // handle to a resource

    public DisposableResourceHolder() {
        this.resource = ... // allocates the resource
    }

    public void Dispose() {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    protected virtual void Dispose(bool disposing) {
        if (disposing) {
            if (resource!= null) resource.Dispose();
        }
    }
}
```

> 핵심 요지는 IDisposable 인터페이스를 구현하면서 추가로 `protected void Dispose(bool disposing)` 함수를 구현하는 것이다.
> 
* **disposing 파라미터의 차이**
	* disposing == true → **괸리 메모리** 및 **비관리 메모리** 둘다 해제한다    
	- disposing == false → **비관리 메모리**만 해제한다

* 🤔 **왜 bool을 파라미터로 가지는 Dispose가 필요할까?**
	- **IDisposable** 자체는 **Dispose()** 함수밖에 제공해주지 않는데 왜?
	- **이유**
	    - GC의 메모리 수집은 순서가 보장되지 않으므로 상황에 따라 소멸자에서 참조하는 대상을 이미 GC가 수거해버린 상태일수도 있다, 따라서 소멸자가 **관리 메모리 영역**을 다뤄버리면 **예상할 수 없는 문제**가 발생할 수 있다
	    - 반면 **비관리 메모리 영역은 GC가 다루지 않는 영역**이라 위와 같은 문제가 발생하지 않는다, 그렇기 때문에 소멸자에서 호출하는 **Dispose는 비관리 메모리만 해제**하도록 하는 것이다
- **추가로**
    - Finalizer를 구현하면 가비지 컬렉터에 부하를 줄 수 있으니 메모리 누수에 대한 방어가 꼭 필요한 상황에만 최후의 방어선 느낌으로 사용해야 한다
    - 모든 상황에 표준 Dispose 패턴을 구현할 필요는 없다, **Dispose시 비관리 메모리를 다뤄야 하면서 관리 메모리도 다뤄줘야 하는 상황에 사용하자**