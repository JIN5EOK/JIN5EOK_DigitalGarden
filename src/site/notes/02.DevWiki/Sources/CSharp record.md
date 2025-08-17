---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp record/","noteIcon":""}
---

> 불변의 값 형태의 데이터 구조를 선언하는데 사용된다

```C#
public record Item
{
    public string Name { get; init; }
    public int Count { get; init; }
}
```

## 불변성
* 한번 생성하면 값이 변하지 않는다
## Equals, GetHashCode, ToString 자동 구현
* 위 비교 함수들이 자동 구현되며 이를 통해 **값 형식의 비교**들이 가능함
* ToString이 자동 구현되어 **ToString 사용시 읽기 좋은 형태**로 출력됨
## with 표현식을 사용한 데이터 복사
**with 표현식**을 사용해 일부 값을 변경한 채로 값을 복사할 수 있다
```C#
var updated = before with { Count = 70 };
```
