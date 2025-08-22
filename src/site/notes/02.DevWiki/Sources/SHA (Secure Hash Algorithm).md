---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/SHA (Secure Hash Algorithm)/","noteIcon":""}
---


> **단방향** 해시 알고리즘, 여러 버전이 존재하며 현 시점 널리 사용되는건 SHA-256 (문자들을 256비트의 해시값으로 변환)이다
* 특징
	* 단방향성, 결과값을 통해 입력값을 도출할 수 없다
	* 충돌 회피
		* 충돌이 일어날 가능성이 **매우 낮은 편** (가능성이 아예 없는 것은 아님)
	* 효율적 연산
		* MD5보단 느리지만 여전히 빠르다

---
### 관련 문서
[[02.DevWiki/Sources/MD5 (Message Digest Algorithm 5)\|MD5 (Message Digest Algorithm 5)]]