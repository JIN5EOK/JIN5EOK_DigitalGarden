---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp string/","noteIcon":"","created":"2024-10-24T10:59:36.000+09:00","updated":"2025-08-05T12:04:57.018+09:00"}
---

## string, 문자열

> string은 그 길이와 크기가 가변적으로 변하는 특징이 있다

* 동일한 **string 개체의 문자열을 변경**하면 스택 메모리에서 가리키는 주소의 힙 메모리의 값을 변경시키는 것이 아닌 ***다른 주소에 새로운 객체***를 만들어 냄 
* [[02.DevWiki/Sources/인터닝 (Interning)\|인터닝 (Interning)]]이라는 최적화 기법을 통해 여러 string개체가 동일한 문자열을 저장할 경우 **같은 힙 메모리 주소**를 가리키게 됨

### 인터닝을 거치지 않는 예외가 있다!
``` C#
string string1 = "Hello"; 
string string2 = new string("Hello".ToCharArray());
```
* "Hello" 형태의 경우 [[02.DevWiki/Sources/인터닝 (Interning)\|인터닝 (Interning)]]을 거치지만 new 키워드를 통해 생성하는 경우 인터닝을 거치지 않고 새로운 개체가 만들어진다

## String 에서의 Equals와 ==
* string은 **참조 형식**이지만 **값 비교**를 해야하는 경우가 많고 값과 유사하게 동작하기 때문에 기본적으로 String의 == 연산자는 값 비교를 수행하며 Equals도 같은 기능을 수행하도록 오버라이딩 되어 있다. 
* 😩 다만 **object 형식으로 캐스팅**된 상태에서 **\==** 사용시 **참조 형식 비교**가 일어날 수 있으니 주의!
	* 함수 오버라이딩의 특징을 생각해보면 왜 그런 차이가 일어나는지 알기 쉽다
	* 이 문서를 참고하자 : [[02.DevWiki/Sources/CSharp 오버라이드 키워드 유무의 차이\|CSharp 오버라이드 키워드 유무의 차이]]
## 만약 string 개체를 계속 변경시켜야 하는 상황이라면?
* ***StringBuilder***를 사용하자
* **문자열 버퍼**를 사용하여 동작해 새 문자열 생성을 하지 않음

