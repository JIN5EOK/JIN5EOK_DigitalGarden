---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/DotNet Garbage Collection (닷넷 가비지컬렉션)/","noteIcon":"","created":"2024-11-10T15:01:30.000+09:00","updated":"2025-07-19T22:58:36.976+09:00"}
---

> 세대별GC 알고리즘을 사용해 객체를 세대로 구분하는것이 특징

* **Generational GC** (세대별GC)
	* 객체들을 **0~2세대로 구분**
	* 세대가 **낮은** 객체 : **자주 검사**
	* 세대가 **높은** 객체 : **검사 빈도를 낮춤**
* **SOH / LOH**
	* **Small Of Heap,**
		* **작은 객체**들의 힙
		* 객체들은 **0세대**부터 시작하여 **2세대**까지 **승급**할 수 있음
	* **Large Of Heap**
		* **큰 객체**들의 힙
		* **85kb** 이상의 객체가 할당
		* 할당시 처음부터 **3세대**로 정의 
			* 3세대라고 특별할건 없고 그냥 **2세대와 동일**
* **콤팩트 작업**
	* GC 작업 수행 후 빈 **메모리 공간 압축**
	* **2세대** 객체 **수집 과정**에서 수행된다
* **멀티스레드에서 GC 수행**
	* Stop-The-World 최소화

---
### 관련 문서 
[[02.DevWiki/Sources/Dotnet 객체의 세대\|Dotnet 객체의 세대]]
[[02.DevWiki/Sources/DotNet GC vs Unity GC\|DotNet GC vs Unity GC]]
