---
{"dg-publish":true,"permalink":"/03.Resource/Development Wiki/Development Wiki (Sources)/CSharp IEnumerable과 IEnumerator는 왜 나누어져 있을까/","noteIcon":"","created":"2024-10-01T11:39:43.000+09:00","updated":"2025-07-19T22:58:36.949+09:00"}
---

## IEnumerable과 IEnumerator는 왜 나누어져 있을까?
두가지 인터페이스의 역할은 아래와 같다
### IEnumerable
* IEnumerator를 반환하는 함수 GetEnumerator()를 구현해야 함
* 동일한 방법으로 컬렉션을 **반복 가능함을 정의**
### IEnumerator
* 컬렉션을 순회하는 함수 MoveNext, Reset, Current를 구현해야 함
* **실제 컬렉션을 반복하는 로직**에 대한 정의

이로인해 얻는 이점은..
* **책임 분리**
	* 두 가지 로직을 분리함으로써 단일 책임 원칙을 준수한다
* **유연성**
	* 예를들어 컬렉션에 대한 로직이 바뀌어도 IEnumerable은 바꾸지 않아도 된다

