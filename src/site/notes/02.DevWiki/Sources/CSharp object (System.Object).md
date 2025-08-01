---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp object (System.Object)/","noteIcon":"","created":"2024-10-01T11:42:45.000+09:00","updated":"2025-08-02T10:49:22.041+09:00"}
---

### System.Object
* **object** 키워드로 사용할 수 있음
* **.Net** 모든 타입이 상속받는 **기본 타입**
* **Value타입도 System.Object를 상속받는다!**
	* 다만 **System.ValueType**이라는 **System.Object의 추상 서브 클래스 타입**을 상속받아 Reference타입과 구분
	* **사용자**가 직접 System.ValueType **상속 불가**
### 기본 함수
> **GetType을 제외**한 함수들은 모두 **오버라이딩 가능**

* **ToString**
	* 객체를 **String으로 출력**
* **Equals**
	* **값 타입**
		* **값이 같은지** 비교
	* **레퍼런스 타입**
		* 레퍼런스 타입의 경우 **레퍼런스가 같은지** 비교
		* **string** 같은 경우 **비교시엔 값이 같은지 비교**하도록 오버라이딩 되어 있음
* **GetHashCode**
	* **int형 해시코드** 획득, **경우에 따라 해시중복**이 일어날 수 있음
* **GetType**
	* **타입** 획득
	* 다른 함수들과 달리 **오버라이딩 불가**
### 주의사항
* 값 타입들이 **object** 타입으로 업 캐스팅 할 경우 박싱이 일어난다!

---
### 연관 문서 
[[02.DevWiki/Sources/박싱과 언박싱\|박싱과 언박싱]]