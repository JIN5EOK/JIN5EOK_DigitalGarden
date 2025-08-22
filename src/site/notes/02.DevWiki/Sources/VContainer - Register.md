---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/VContainer - Register/","noteIcon":""}
---

# `IContainerBuilder.Register`

- 해당 타입으로 의존성을 주입하고자 할 때 어떤 방식으로 사용할지 결정
    
    ```csharp
    public class MyLifeTimeScope : LifetimeScope
    {
        public Foo foo;
        
        protected override void Configure(IContainerBuilder builder)
        {
            // PlayerLoop 진입점 인터페이스 대상으로 GamePresenter에 대한 의존성 주입 
            builder.RegisterEntryPoint<GamePresenter>();
            // HelloWorldService에 대한 의존성 주입, 싱글톤으로 (없다면 생성, 있다면 싱글톤 재활용)
            builder.Register<HelloWorldService>(Lifetime.Singleton);
            // 지정한 컴포넌트를 이용해 의존성 주입
            builder.RegisterComponent(foo);
        }
    }
    ```
    
- Lifetime 파라미터 기본값은 Singleton
    

### LifeTime의 종류

- Singleton
    - 전역적으로 단 하나의 인스턴스만 사용해 주입
- Transient
    - 주입할때마다 다른 인스턴스 생성하여 주입
- Scoped
    - 스코프 단위로만 동일한 인스턴스 사용

# `IContainerBuilder.RegisterFacotry`

- 의존성 주입시 ****`Func`를 사용, **매개변수**를 지정할 수 있으므로 생산과정을 쉽게 사용자 정의 가능
    
    ```csharp
    protected override void Configure(IContainerBuilder builder)
    {
        builder.RegisterFactory<int, Foo>(OnRegisterFactory);
        base.Configure(builder);
    }
    
    private FooUI OnRegisterFactory(int index)
    {
        return Resources.Load<Foo>($"Foo{index}");
    }
    ```
    
    ```csharp
    public class User : MonoBehaviour
    {
        [Inject]
        public void InstantiateFoo(Func<int, Foo> foo)
        {
            Instantiate(foo.Invoke(1));
        }
    }
    ```