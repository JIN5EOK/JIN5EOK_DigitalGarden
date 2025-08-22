---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 델리게이트/","noteIcon":"","updated":"2025-08-16T15:35:50.000+09:00"}
---

# CSharp 델리게이트

> **특정 메서드**에 대한 **참조를 저장**할 수 있는 형식

```csharp
delegate int CalcDelegate(int a, int b);

private CalcDelegate calc = Add;

private int Add(int x, int y) 
{
	return x + y;
}
```
### 기본 제공되는 델리게이트 형식들
## Action
* **Return값이 없는** 메서드

## Func
* **Return값이 있는** 메서드

## Predicate
* **Return 값이 bool**, **매개변수는 하나**로 고정된 메서드

## Func, Predicate 등 반환값이 있는 델리게이트 사용시 주의사항
> 🧐 델리게이트는 **멀티캐스트를 지원**한다, 그렇다면..?

* 반환값이 있는 함수라면 **여러가지 반환값이 반환**될 수 있다!!
* 물론 반환되는 값은 하나뿐이므로 **마지막 반환값**만을 사용하게 된다

> ☺️만약 각각 함수들의 반환값을 별도로 처리하고 싶다면..

* **GetInvocationList()** 라는 함수를 이용해보자

---
[[02.DevWiki/Sources/CSharp 델리게이트 이벤트 실행과 멀티스레드\|CSharp 델리게이트 이벤트 실행과 멀티스레드]]