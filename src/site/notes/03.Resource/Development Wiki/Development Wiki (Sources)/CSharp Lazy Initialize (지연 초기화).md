---
{"dg-publish":true,"permalink":"/03.Resource/Development Wiki/Development Wiki (Sources)/CSharp Lazy Initialize (지연 초기화)/","noteIcon":"","created":"2024-11-10T14:59:28.000+09:00","updated":"2025-07-20T02:29:01.533+09:00"}
---

객체의 실제 초기화 시점을 객체를 사용하는 시점까지 미룰 수 있다

객체의 초기화 비용이 크거나 메모리 차지가 커 필요할때만 올리고 싶을 때 사용할 수 있다

```C#
static Lazy<T> _t = new Lazy<T>(() => new T())

```

Lazy\<T> 클래스를 사용하여 Lazy Initialize를 쉽게 구현할 수 있다

- Lazy\<T>클래스를 사용하여 생성하는 클래스는 기본적으로 최초 접근 시점에 초기화 됨
- 기본적으로 Thread-Safe하며 관련 설정을 조절할수도 있음