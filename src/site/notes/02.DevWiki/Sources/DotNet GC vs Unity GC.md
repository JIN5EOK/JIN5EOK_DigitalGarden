---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/DotNet GC vs Unity GC/","noteIcon":""}
---

### .NET GC vs Unity GC
* **세대구분**
	* **.NET** : **0~2세대** 구분
	* **Unity** : **없음🥲**
* **콤팩트 작업**
	* **.NET** : **2세대 수거** 시점에서 실행
	* **Unity** : **없음..🥹**
* **Stop-The-World 방지책**
	* **.NET** : **멀티스레드** 실행
	* **Unity** : **점진적 가비지 컬렉션** - **여러 프레임**에 걸쳐 실행
### 결론
* **Unity GC**는 .NET GC 대비 **비효율적**
* 콤팩트 작업도 수행 안하므로 **메모리 파편화**가 잘 발생
---
### 관련 문서
[[02.DevWiki/Sources/DotNet Garbage Collection (닷넷 가비지컬렉션)\|DotNet Garbage Collection (닷넷 가비지컬렉션)]]
[[02.DevWiki/Sources/Unity Garbage Collection (유니티 가비지컬렉션)\|Unity Garbage Collection (유니티 가비지컬렉션)]]