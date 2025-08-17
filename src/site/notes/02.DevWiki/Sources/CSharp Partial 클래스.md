---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp Partial 클래스/","noteIcon":""}
---

> 하나의 클래스를 여러개의 파일로 나누어 작성할 수 있다

```csharp
partial class Partial
{
    partial void Run();
}
```

```csharp
partial class Partial
{
    partial void Run()
    {
        Console.WriteLine("Run!");
    }
}
```

- **장점**
    - 규모가 큰 클래스를 나누어 작성할 수 있다
    - 한 클래스를 여럿이서 작업해야 하는 경우 충돌방지