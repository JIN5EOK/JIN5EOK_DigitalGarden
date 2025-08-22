---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp Lazy Initialize (지연 초기화)/","noteIcon":"","updated":"2025-08-17T16:11:50.000+09:00"}
---

> 객체의 실제 초기화 시점을 객체를 사용하는 시점까지 미룰 수 있다

* 객체의 **초기화 비용**이 크거나 **메모리 차지**가 커 실제로 사용할때만 초기화 하기 위해 사용

``` CSharp
static Lazy<T> _t = new Lazy<T>(() => new T())
```

* `Lazy<T>` 클래스를 사용하여 Lazy Initialize를 쉽게 구현할 수 있다

- Lazy\<T>클래스를 사용하여 생성하는 객체는 위 코드처럼 **멤버 초기화**를 하더라도 기본적으로 **최초 접근 시점에 초기화**가 수행 됨
- 기본적으로 **Thread-Safe**함