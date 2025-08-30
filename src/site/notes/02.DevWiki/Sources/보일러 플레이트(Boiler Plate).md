---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/보일러 플레이트(Boiler Plate)/","noteIcon":""}
---

## 보일러 플레이트(Boilerplate)?
* **여러 곳에서 재사용되어 반복적으로 나타나는 코드**를 의미
* 보통 코드의 핵심 로직을 담고 있기보단 **프로그램을 실행시키기 위해 언어나 프레임워크가 요구하는 기본적인 구조**를 갖추는 역할을 수행한다.
* **이름의 유래**
    * 19세기, 자주 사용되는 문구나 광고 문구를 미리 찍어둔 **강철 인쇄판** 을 만들어 여러 신문에 배포했는데, 여기서 **미리 만들어져 반복적으로 사용되는 틀**이라는 의미로 사용되었고 추후 프로그래밍쪽 용어로 의미가 확장되었다

## 예시

### C# 코드 예시

> C# 에서 "Hello, World!"를 출력하기 위한 기본 코드 구조, `Class` 선언과 `Main` 메소드 부분을 보일러 플레이트 코드라고 볼 수 있다

```csharp
using System;

public class HelloWorld {
    public static void Main(string[] args) {
        Console.WriteLine("Hello, World!");
    }
}
```