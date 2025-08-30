---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/Unity Garbage Collection (유니티 가비지컬렉션)/","noteIcon":""}
---

> 보헴GC 알고리즘 사용, 전반적으로 .NET GC에 비해 성능이 떨어짐

* .NETGC에 대해선 [[02.DevWiki/Sources/DotNet GC vs Unity GC\|DotNet GC vs Unity GC]] 참고

* **Bohem GC** (보헴GC)
	* 단순히 객체들을 **살아있는** 객체와 **죽어있는** 객체 **두가지로 구분**
* **점진적 가비지 컬렉션**
	* **여러 프레임**에 걸쳐 가비지 컬렉션을 **수행**하도록 하여 **Stop-the-world 최소화**
		* 유니티 2019년 버전부터 추가된 기능