---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 포매팅 vs 문자열 보간/","noteIcon":"","created":"2024-10-06T14:31:03.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---

## 포매팅

포매팅은 C언어 시절부터 사용해온 문자열 포매팅 방법 (%d, %s 등으로 사용하던 그것)

``` csharp

String.Format(“I am {0}! And {1}”, value1, value2);

```

인자의 순서를 고려해야 하고 가독성이 떨어짐


## 문자열 보간

``` csharp

$”I am {value1} And {Value2 + Value3}”;

```

가독성 Good, 또한 값 뿐만 아니라 간단한 수식도 첨부할 수 있다