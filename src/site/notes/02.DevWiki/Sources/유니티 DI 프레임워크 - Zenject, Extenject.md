---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 DI 프레임워크 - Zenject, Extenject/","noteIcon":"","updated":"2025-07-19T22:58:36.000+09:00"}
---

> VContainer가 더 널리 쓰이는 상황이라 간단하게만 훑었음

### 특징
- VContainer대비 기능이 많으나 다소 무겁고 어려움
    - 유니티의 씬 및 Monobehaviour에 최적화
- `Zenject`, `Extenject` ???
    - `Zenject`는 현재 지원 중단, `Extenject`가 좀 더 최신까지 업데이트 되었음

### 기능
- `Scene Context`
    - 씬상에 존재하는 Installer 클래스들을 관리한다
    
- `Installer`
    
    - `ScriptableObjectInstaller`, `MonoInstaller`, `PrefabInstaller`
    - 의존성 주입 관리자로 사용할 스크립트에 상속하여 의존성을 관리한다
	- `Bind<IScoreManager>()` `To<IntScoreManager>()` IScoreManager 타입을 IntScoreManager 타입으로 바인드
	- `FromNewComponentOnNewGameObject()` 새 게임오브젝트 + 새 컴포넌트로 생성하여 주입
	- `AsSingle()` 다른 대상에게 주입할때도 처음 만든 객체를 다시 재사용

```csharp
public class InstallerTest : MonoInstaller
{
	public override void InstallBindings()
	{
		Container.Bind<IScoreManager>().To<IntScoreManager>().FromNewComponentOnNewGameObject().AsSingle();
	}
}
```

- `[Inject]` 속성
    - 의존성을 주입할 대상에게 작성, 생성자의 경우 자동지원
```csharp
[Inject]
public IScoreManager ScoreManager
{
	get => _scoreManager;
	set
	{
		Debug.Log($"의존성 주입 완료");
		_scoreManager = value;
	}
}
```
        

---

### 연관 문서

[유니티 의존성 주입](https://www.notion.so/17f858a4236480f989c4e367614b723d?pvs=21)

[VContainer : 유니티 DI 프레임워크](https://www.notion.so/VContainer-DI-194858a4236480ceb821e6e9dc292a7f?pvs=21)