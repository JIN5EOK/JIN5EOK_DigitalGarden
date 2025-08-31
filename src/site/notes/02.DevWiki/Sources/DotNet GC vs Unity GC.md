---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/DotNet GC vs Unity GC/"}
---

### .NET GC vs Unity GC

각 GC들에 대해선 아래 노트들을 참고하자
[[02.DevWiki/Sources/DotNet Garbage Collection (닷넷 가비지컬렉션)\|DotNet Garbage Collection (닷넷 가비지컬렉션)]]
[[02.DevWiki/Sources/Unity Garbage Collection (유니티 가비지컬렉션)\|Unity Garbage Collection (유니티 가비지컬렉션)]]


* **수거영역**
	* **.NET** : **class, string, 델리게이트, 컬렉션**등.. 일반적인 C#의 참조 객체
	* **Unity** : **Texture, GameObject**등 유니티 오브젝트나 에셋에 대한 **참조** (실제 객체는 C++ 네이티브 영역에서 담당하고 경우에 따라 Destroy나 Dispose등으로 수동 해제가 필요함)
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