---
{"dg-publish":true,"permalink":"/DevWiki/Sources/유니티 IL2CPP 컴파일 시 유의사항/","noteIcon":"","created":"2024-09-15T18:29:30.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---

### Reflection 방식 제한
* AOT방식은 **미리 모든 코드를 컴파일** 한다
	* 런타임 도중 타입을 만드는 **System.Reflection.Emit**을 사용할 수 없다

### 관리되는 코드 스트리핑 문제
* **Reflection, 문자열 기반 호출** 등 실제로 호출되는지 **파악하기 어려운 코드**들은 컴파일 과정에서 제거될 수 있다
* **link.xml**을 사용하면 명시적으로 제거 방지 가능

---
[[DevWiki/Sources/유니티 스크립팅 백엔드 Mono, IL2CPP\|유니티 스크립팅 백엔드 Mono, IL2CPP]]