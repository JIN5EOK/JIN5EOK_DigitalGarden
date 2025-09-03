---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 로컬라이제이션 SmartString, IVariable/"}
---

## 1. Smart String이란?

> **SmartString**은 **파라미터나 조건식을 사용**하여 동적인 텍스트를 생성하는 기능이다.
> 이를 통해 상황에 따른 문장의 변화 (변수 등)을 유연하게 구현할 수 있다.

* 플레이어 이름, 아이템 수량, 점수 등 게임 내에서 **실시간으로 변하는 데이터를 텍스트에 삽입할 수 있도록 해준다**. 
* 예를 들어, `Jin5eok님이 10개의 아이템을 획득했습니다!`와 같은 문장에서 **플레이어 이름과 아이템 갯수**를 변경할 수 있다

``` CSharp
 // 일반 변수를 전달하는 예시
message.Arguments = new object[] { "item", 5 };

// Variable 사용 예시
var vars = new DictionaryVariables();
vars["playerName"] = new StringVariable { Value = "Jinseok" };
message.Arguments = new object[] { vars };
```

* Smart String에 삽입하기 위한 변수 객체로 `IVariable` 인터페이스 또는 `Variable<T>` 클래스가 제공된다.
* 단 값 변경 등 갱신이 필요 없는 경우 Variable사용 없이 일반 C# 타입들을 변수로 사용해도 무방함. 


* `IVariable`은 Smart String에 사용될 변수들이 상속받는 기본 인터페이스이다.
- 다른 기능 없이 `GetSourceValue()` 라는 변수가 나타내는 값을 반환하는 기본 함수만이 정의되어 있다.

* **상속 및 기능 직접 구현시 주의사항**
	* **값을 얻는 함수만 기본 제공**하고 그 외의 기능들은 **개발자가 직접 구현**해야 한다
	* 따라서 이 방식으로 Smart String 변수를 구현하면, 변수의 값이 변경되더라도 **Smart String이 자동으로 갱신되지 않는다!** 🥹
	* 즉, **`IVariable` 인터페이스만을 상속받아 Variable을 구현**하면 텍스트를 **수동으로 다시 로드하거나 갱신하는 로직**을 추가해야 한다



* `Variable<T>`는 **유니티 로컬라이제이션 시스템에서 미리 구현한 제네릭 클래스**로 `IVariable` 인터페이스를 상속받는다.
- **Value 프로퍼티를 변경하면  해당 변수를 사용하는 Smart String이 자동으로 갱신**된다!

## 4. 요약

* Smart String 변수를 구현할 때는 대부분의 경우 유니티가 제공하는 `Variable<T>` 클래스를 사용하는게 효율적임
* `IVariable`을 직접 구현하는 경우는 **자동 갱신이 별로 중요하지 않으면서 복잡한 커스텀 로직**이 필요한 경우에만 고려하자!
