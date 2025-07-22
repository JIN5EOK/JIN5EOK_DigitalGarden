---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 델리게이트/","noteIcon":"","created":"2024-10-06T14:30:40.000+09:00","updated":"2025-07-19T22:58:36.957+09:00"}
---

## Action
Return값이 없는 메서드

## Func
Return값이 있는 메서드 마지막 파라미터가 반환값

## Predicate
Return 값이 bool, 매개변수는 하나로 고정된 메서드

## Func, Predicate 등 반환값이 있는 델리게이트 사용시 주의사항
> 🧐 델리게이트는 멀티캐스트를 지원한다, 그렇다면..?

* 반환값이 있는 함수라면 여러가지 반환값이 반환될 수 있다!!
* 물론 반환되는 값은 하나뿐이므로 마지막 반환값만을 사용하게 된다

> ☺️만약 각각 함수들의 반환값을 별도로 처리하고 싶다면..

GetInvocationList() 라는 함수를 이용해보자

---
[[02.DevWiki/Sources/CSharp 델리게이트 이벤트 실행과 멀티스레드\|CSharp 델리게이트 이벤트 실행과 멀티스레드]]