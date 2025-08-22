---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 소멸자(Finalizer) vs IDisposable/","noteIcon":""}
---

>수동으로 해제해주어야 하는 리소스가 있을 때 어떤 방식을 사용하는것이 좋을까?

* **소멸자** 
	* **장점**
		* GC가 호출, 사용자가 **명시적으로 호출**하지 않아도 **알아서 동작**
	* **단점**
		* GC가 호출하므로 **해제시점** 통제 불가
		* **GC 부하**
			* 소멸자 구현 객체는 소멸자 호출때문에 **수집이 느릴 가능성**
			* 수집 못하고 수집 사이클이 끝나면?
			* 뜻밖의 **Finalizer Queue** 에 남은 객체 **세대 증가**
* **IDisposable**
	* **장점**
		* **사용자**가 원할 때 **해제 가능**
	* **단점**
		* 사용자가 **해제 안하면 해제 안됨**

* **결론**
	* **둘다 사용할 수 있도록 구현**하는것이 좋다
		* **IDisposable**을 구현해 **원할 때 해제**
		* **소멸자**를 구현해 **자동으로 해제**

[[02.DevWiki/Sources/DotNet Garbage Collection (닷넷 가비지컬렉션)\|DotNet Garbage Collection (닷넷 가비지컬렉션)]]