---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 델리게이트 이벤트 실행과 멀티스레드/","noteIcon":""}
---

> 멀티스레드 환경에서 델리게이트 이벤트를 실행할 경우 동기화 문제가 발생할 수 있다, 이를 해결하는 방법들을 정리하였다.

* 델리게이트에 대한 내용은 [[02.DevWiki/Sources/CSharp 델리게이트\|CSharp 델리게이트]] 참고 
### 이벤트 핸들러를 얕은 복사

```csharp
var handler = myDele
if (handler != null)
	handler.Invoke()

```

- 원자적으로 이벤트를 복사해와 사용하므로 원본 객체의 이벤트 목록이 변하더라도 상관 없다
- 다만 당연하게도 예외만 발생하지 않을 뿐 멀티스레드 환경에선 **실제 객체 이벤트와 얕은 복사된 이벤트가 달라질 수 있고** 이 때문에 문제가 발생할 여지는 여전히 존재함

### Null 조건문 연산자
```csharp
myDele?.Invoke()
```

* 델리게이트 Null 체크와 실행이 원자적으로 수행되므로 안전하다!

### Lock 키워드 등을 사용해 단일 접근 보장

- 스레드에 안전한 임계 영역을 설정하여 스레드 안정성 보장
- 조금이라도 의도치 않게 동작하기 바라지 않는다면 사용하자

```csharp
private readonly object _eventLock = new object();
public void RaiseEvent()
{
    lock (_eventLock)
    {
        myDele?.Invoke();
    }
}

```