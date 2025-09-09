---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/LCS (Longest Common Subsequence, Longest Common Substring)/"}
---

### Longest Common Subsequence (최장 공통 부분 수열)
* 두 문자열에서 연속된 문자들의 공통 패턴
* 문자들이 연속될 필요 없음
	* 예)
	* **B**C**AD**
	* F**B**GK**AD**
	* 가 있다면
	* BAD은 최장 공통 부분 수열임
### Longest Common Substring (최장 공통 부분 문자열 or 최장 공통 연속 수열)
* 두 문자열에서 연속된 문자들의 공통 패턴
* **문자들이 반드시 연속되어야 함**
	* 예)
	* B**CAD**
	* F**CAD**F
	* CAD가 최장 공통 부분 문자열임
	* 슬라이딩 윈도우를 사용해 쉽게 구할 수 있다!
        * [[02.DevWiki/Sources/슬라이딩 윈도우 (Sliding Window)\|슬라이딩 윈도우 (Sliding Window)]]