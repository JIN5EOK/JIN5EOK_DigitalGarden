---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp string/","noteIcon":"","created":"2024-10-24T10:59:36.000+09:00","updated":"2025-08-16T15:24:09.977+09:00"}
---

# CSharp string

> 연속된 문자를 표현하는 자료형
> 문자열은 변경이 되지 않는 **불변 객체**임, 이 사실을 염두에 두면 문자열 최적화와 관련된 많은 부분들을 쉽게 이해할 수 있다.
## 인터닝

> 문자열은 [[02.DevWiki/Sources/인터닝 (Interning)\|인터닝 (Interning)]]이라는 최적화 기법을 사용.
> 여러 string개체가 동일한 문자열을 저장할 경우 **같은 힙 메모리 주소**를 가리키게 됨

* 인터닝이 가능한 것도 문자열이 **불변 객체**이기 때문이다, 같은 객체가 같은 값을 제공하는게 보장되므로

### 인터닝과 관련된 예시

> **문자열 상수**를 사용할때 **인터닝이 동작**한다고 보면 될 듯

``` C#
string string1 = "Hello"; // 문자열 상수 대입, 인터닝 O
const string ConstString = " World!" // 문자열 상수, 인터닝 O

string string2 = "Hello" + ConstString; // 문자열 상수 조합, 인터닝 O

string string3 = new string("Hello".ToCharArray()); // 인터닝 안 거치고 무조건 생성됨..
string string3 = string.Intern(string3) // 단 나중에 수동으로 인턴풀에 넣을 수는 있다
```


## 문자열은 변경시킬 때 마다 할당이 발생함!

> 역시 **불변 객체**의 특성 때문에 일어나는 일, 새로운 문자열을 담기 위해 기존 개체를 변경시킬 수 없으니 새로운 객체를 만들 수 밖에 없다

* 🥹 따라서 아래 코드는 **100번의 문자열 생성**이 일어난다..
``` Csharp
string s = "";

for (int i = 0; i < 100; i++)
{
    s += i; // 더할 때 마다 새로운 문자열이 생성됨..
}
```

### 많은 문자열 변경이 필요할 땐 StringBuilder를 사용
* 위와 같이 **여러번 문자열을 변경**해야 할 땐 ***StringBuilder***를 사용하자
* 내부 **문자열 버퍼**를 사용하여 동작하여 문자열 조합시 발생하는 임시 할당과 복사가 적게 발생함

``` csharp
var sb = new StringBuilder();

for (int i = 0; i < 3; i++)
{
    sb.Append(i); // 내부 버퍼에만 추가
}

string result = sb.ToString(); // 마지막에 딱 한 번만 string 생성됨
```
## String 에서의 Equals와 ==

* string은 **참조 형식**이지만 **값 비교**를 해야하는 경우가 많고 값과 유사하게 동작하기 때문에 기본적으로 String의 == 연산자는 값 비교를 수행하며 Equals도 같은 기능을 수행하도록 오버라이딩 되어 있다. 

* 😩 다만 **object 형식으로 캐스팅**된 상태에서 **\==** 사용시 **참조 형식 비교**가 일어날 수 있으니 주의!
	* 함수 오버라이딩의 특징을 생각해보면 왜 그런 차이가 일어나는지 알기 쉽다
	* 오버라이딩을 하면 형변환이 된 상태에서도 자식 클래스의 기능이 호출되기 때문임
	* 참고 : [[02.DevWiki/Sources/CSharp 오버라이드 키워드 유무의 차이\|CSharp 오버라이드 키워드 유무의 차이]]

