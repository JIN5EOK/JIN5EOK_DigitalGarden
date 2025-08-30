---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 TestRunner/","noteIcon":""}
---

### 특징
- 유닛테스트를 수행하는 라이브러리

### 테스트 메서드 속성
- `[Test]` : **일반 테스트** 메서드
- `[UnityTest]` : **코루틴 테스트** 메서드
- `[SetUp]` : 클래스 내 테스트 메서드가 **실행되기 전 항상 호출**
- `[TearDown]` : 클래스 내 테스트 메서드가 **실행된 후 항상 호출**
- `[TestCase(변수 내용)]` : **동일한 테스트 로직을 여러 매개변수**로 실행하고 싶을 때 사용, **여러개 작성하면 여러 매개변수로 실행**됨

### EditMode와 PlayMode
- **EditMode**
    - 어셈블리 정의 Platforms 체크박스 Editor만 체크
    - **게임을 실행하지 않고 수행**
    - MonoBehaviour에 의존하지 않는 **순수 C# 클래스** 등 테스트 할때 사용
- **PlayMode**
    - 어셈블리 정의 의 Platforms 체크박스 Editor외의 항목 체크
    - **게임을 실행한채로 수행**
    - MonoBehaviour등 **유니티 엔진 의존적 기능 테스트** 할때 사용

### Assertions
* TestRunner를 위해 구현된 **Assert함수**, **조건에 맞을 경우 테스트가 실패처리**

| 메서드                                 | 설명                      |
| ----------------------------------- | ----------------------- |
| `Assert.AreEqual(expected, actual)` | 두 값이 같은지 확인             |
| `Assert.IsTrue(condition)`          | 조건이 true인지 확인           |
| `Assert.IsFalse(condition)`         | 조건이 false인지 확인          |
| `Assert.IsNull(obj)`                | 객체가 null인지 확인           |
| `Assert.IsNotNull(obj)`             | 객체가 null이 아닌지 확인        |
| `Assert.Greater(arg1, arg2)`        | `arg1`이 `arg2`보다 큰지 확인  |
| `Assert.Throws<T>()`                | 특정 타입 `T`의 예외가 발생하는지 확인 |
