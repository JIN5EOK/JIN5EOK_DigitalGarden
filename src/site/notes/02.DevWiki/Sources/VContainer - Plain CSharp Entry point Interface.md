---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/VContainer - Plain CSharp Entry point Interface/","noteIcon":"","created":"2025-05-23T02:08:29.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---

### 일반 C# 진입점(Entry Point) 인터페이스

- `MonoBehaviour`를 상속받지 않은 클래스라도 `PlayerLoop` 의 실행 흐름과 동기화하여 작동하도록 만들 수 있음
- Monobehaviour 객체를 대체하는 일반 C# 테스트용 목업 객체 제작등에 유용

| VContainer 진입점                        | 실행 타이밍                           |
| ------------------------------------- | -------------------------------- |
| `IInitializable.Initialize()`         | 컨테이너 생성 직후                       |
| `IPostInitializable.PostInitialize()` | `IInitializable.Initialize()` 직후 |
| `IStartable.Start()`                  | `MonoBehaviour.Start()`          |
| `IAsyncStartable.StartAsync()`        | `MonoBehaviour.Start()`          |
| `IPostStartable.PostStart()`          | `MonoBehaviour.Start()` 이후       |
| `IFixedTickable.FixedTick()`          | `MonoBehaviour.FixedUpdate()`    |
| `IPostFixedTickable.PostFixedTick()`  | `MonoBehaviour.FixedUpdate()` 이후 |
| `ITickable.Tick()`                    | `MonoBehaviour.Update()`         |
| `IPostTickable.PostTick()`            | `MonoBehaviour.Update()` 이후      |
| `ILateTickable.LateTick()`            | `MonoBehaviour.LateUpdate()`     |
| `IPostLateTickable.PostLateTick()`    | `MonoBehaviour.LateUpdate()` 이후  |

```csharp
public class GamePresenter : ITickable, IStartable
{
    private readonly HelloScreen _helloScreen;
    private readonly HelloWorldService _helloWorldService;
    public GamePresenter(HelloWorldService helloWorldService, HelloScreen helloScreen)
    {
        _helloScreen = helloScreen;
        _helloWorldService = helloWorldService;
    }

    public void Start()
    {
        // Start 시점에 실행됨
        _helloWorldService.SayHello();
        AddOnClick();
    }
    
    public void Tick()
    {
        // 매 Update마다 실행됨
    }

    private void AddOnClick()
    {
        _helloScreen.button.onClick.AddListener(() => _helloWorldService.SayHello());
    }
}
```