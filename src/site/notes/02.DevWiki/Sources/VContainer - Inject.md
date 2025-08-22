---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/VContainer - Inject/","noteIcon":""}
---

# `[Inject]` 속성

- 해당 **프로퍼티/필드/함수/생성자**를 의존성이 주입될 대상으로 삼는다
    
- 다만 생성자의 경우 `[Inject]`속성을 명시적으로 지정하지 않아도 된다
    
- 일반 C# 클래스의 경우 `IObjectResolver`(Container)를 이용하여 객체를 생성할 경우 [Inject]가 자동으로 실행된다
    
    ```csharp
    [Inject]
    private T1 _myfoo1;
    private T2 _myFoo2
    
    [Inject]
    public void Foo(T2 foo)
    {
    		_myFoo2 = foo;
    }
    ```
    
- 만약 `IObjectResolver`를 통해 객체를 생성하지 않았을 경우에도 수동으로 주입할 수 있다
    
    - `[Inject]` 수동 실행 함수
        - `IObjectResolver.Inject`
        - `IObjectResolver.InjectGameObject`

# `Monobehaviour`에게 적용되는 제약

- `Monobehaviour` 오브젝트들은 생성자를 통해 생성되지 않으므로
    - 생성자 `[Inject]`를 사용할 수 없다
    - 객체가 생성되더라도 자동으로 `[Inject]`가 실행되지 않는다

# `Monobehaviour`의 `[Inject]`실행 방법들

1. `IObjectResolver.Instantiate`
    1. 위 함수를 통해 프리펩 생성
2. `Auto Inject Game Objects`
    1. 인스펙터상의 `LifeTimeScope`의 `Auto Inject Game Objects`에 주입할 오브젝트 삽입
3. `IContainerBuilder`의 `RegisterComponent`
    1. **주입될 대상**이 아닌 **주입에 사용할 Monobehaviour를** 지정하는 종류의 함수지만 그쪽에도 Inject를 실행시킨다
4. `IObjectResolver.InjectGameObject`
    1. 수동으로 주입하기