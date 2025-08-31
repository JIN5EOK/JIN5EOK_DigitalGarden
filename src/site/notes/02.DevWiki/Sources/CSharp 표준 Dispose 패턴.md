---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 표준 Dispose 패턴/"}
---


> Dispose 패턴은 _**종료자 및 IDisposable 인터페이스의 사용 및 구현을 표준화하기 위한 것**
> [https://learn.microsoft.com/ko-kr/dotnet/standard/design-guidelines/dispose-pattern#basic-dispose-pattern](https://learn.microsoft.com/ko-kr/dotnet/standard/design-guidelines/dispose-pattern#basic-dispose-pattern)

* IDisposable 인터페이스에 대해선 [[02.DevWiki/Sources/CSharp IDisposable\|CSharp IDisposable]] 참고

```csharp
public class DisposableResourceHolder : IDisposable {

    private SafeHandle resource; // handle to a resource

    public DisposableResourceHolder() {
        this.resource = ... // allocates the resource
    }

		// 소멸자, 최후의 방어선 느낌
   ~DisposableResourceHolder() {
	   Dispose(false);
   }

		// 비관리, 괸리 리소스를 모두 해제하고 GC에게 수거 대상이 아님을 알림
    public void Dispose() {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

		// protected라 사용자는 호출 불가
    protected virtual void Dispose(bool disposing) {
        if (disposing) {
            if (resource!= null) resource?.Dispose();
        }
    }
}
```

> IDisposable 인터페이스를 구현하면서 추가로 `protected void Dispose(bool disposing)` 함수를 구현해야 한다.
> **public 함수와 파라미터가 추가되는 것이 아니므로 외부 사용자 입장에서는 알 수 없는 변화**이다.
### bool disposing이 뭘까?
* **True**
	* 관리되는 리소스,관리되지 않는  **리소스 모두 해제**
* **False**
	* **관리되지 않는 리소스만** 해제

* **disposing 파라미터의 차이**
	* disposing == true → **괸리 메모리** 및 **비관리 메모리** 둘다 해제한다    
	- disposing == false → **비관리 메모리**만 해제한다

* 🤔 **왜 bool을 파라미터로 가지는 Dispose가 필요할까?**
	- **IDisposable** 자체는 **Dispose()** 함수밖에 제공해주지 않는데 왜?
	- **이유**
		- Dispose를 놓쳤을때를 대비해 최후의 방어선 느낌으로 **소멸자에서 Dispose**를 호출하도록 만들어 두기 위함이다
    		- 만약 **비관리 리소스 / 관리 리소스를 모두 해제하도록 처리한 Dispose()** 를 소멸자에서 호출하면 문제가 발생할 수 있는데
		    - GC의 메모리 수집은 **순서와 타이밍이 보장**되지 않는다
			- 따라서 소멸자가 **관리 메모리 영역**을 다뤄버리면 **예상할 수 없는 문제**가 발생할 수 있다
			    - 예를들면 상황에 따라 **소멸자에서 참조하는 대상**을 **이미 GC가 수거**해버린 상태일수도 있다
		    - 반면 **비관리 메모리 영역은 GC가 다루지 않는 영역**이라 위와 같은 문제가 발생하지 않는다, 그렇기 때문에 소멸자에서 호출하는 **Dispose는 비관리 메모리만 해제**하도록 조치하는 것이다.
        - 또한 `Dispose(bool isDisposing)`이 **virtual로 구현**된걸 볼 수 있는데, **자식클래스에서 이를 오버라이딩**하여 자식에도 **Dispose 로직 구현**을 가능하게 할 수도 있다.
- **추가로**
    - 모든 상황에 **표준 Dispose 패턴**을 구현할 필요는 없다, **Dispose시 비관리 메모리와 관리 메모리를 구분해서 해제해줄 필요가 있을 때 사용하고** 상황에 따라 변형하여 사용할수도 있다!