---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp Partial 클래스/","noteIcon":"","created":"2024-11-10T15:00:38.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
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

- partial 접근제한자는 **private와 유사**하게 동작
- **장점**
    - 규모가 큰 클래스를 나누어 작성할 수 있다
    - 한 클래스를 여럿이서 작업해야 하는 경우 충돌방지