---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 정적 멤버 초기화 구문 vs 정적 생성자/"}
---

``` csharp
정적 멤버 초기화 구문
public static T _member = new T();

정적 생성자

public static T()
{
	// 초기화 내용..
}
```

* **정적 멤버 초기화 구문** 
	* 프로그램 **실행과 동시에 초기화**

* **정적 생성자** 
	* 클래스에 **처음 접근**하는 시점에 호출

* 즉 실행순서는 정적 멤버 초기화 구문 > 정적 생성자
* **예외 처리가 필요하거나 Lazy초기화**가 필요한 상황에서는 정적 생성자 사용