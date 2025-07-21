---
{"dg-publish":true,"permalink":"/DevWiki/Sources/MVC,MVP,MVVM/","noteIcon":"","created":"2024-09-17T17:48:14.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---

## MVC (Model-View-Controller)

> MVC류 파생들의 **기본패턴**으로 **데이터,UI,기능 분리** 수행

* **Model** 
	* 데이터, 비즈니스 로직
	* 자신 외 참조 없음
* **View** 
	* UI 로직
	* Model을 참조, 혹은 간접 참조(Controller를 통해 이벤트 간접 등록) 
* **Controller**
	* 그외 전체 로직,
	* View,Model참조

### 작동 방식
* Model,View가 **연관 혹은 간접 연관**
	1. **View**
		* 사용자 입력
	2. **Controller**
		* Model 업데이트
	3. **Model**
		* 데이터 변경 실행
	4. **View**
		* 변경된 모델을 기반으로 업데이트
			* Model 데이터 이벤트
			* View가 모델 직접 참조
			* 그외 기타 등등
### 특징
* View, Model간 **높은 결합도**
* Controller와 View간 **1:N 관계 가능**
	* 컨트롤러가 직접 View를 업데이트하지 않으므로
## MVP (Model-View-Presenter)

> **모든 상호작용**을 **Presenter**를 통해 수행

* **Model** 
	* 데이터, 비즈니스 로직
* **View** 
	* UI관련 로직
* **Presenter**
	* UI를 제외한 로직
	* Model, View 참조

### 작동 방식
1. **View**
	* 사용자 입력
2.  **Presenter**
	*  Model 변경
3.  **Model**
	*  Presenter에게 변경 값 반환
4. **Presenter**
	* View에게 데이터 전달
5. **View**
	* 받은 데이터로 UI 업데이트

### 특징
* **Model**과 **View** **분리**
* **Presenter**와 **View**는 **1:1관계**
	* MVC와 달리 Presenter가 직접적으로 VIew를 변화시키기 때문
## MVVM (Model,View,View-Model)

> **View-Model <-> View**간 **데이터 바인딩**으로 인한 **느슨한 종속성**

* **Model**
	* 데이터
* **View**
	* UI관련 로직
* **View-Model** 
	* View와 바인딩
	* Model 참조

### 작동 방식
1. View
	* **사용자 입력**
2. View-Model
	* **Model** **업데이트 요청**
3. Model
	* **View-Model**에게 **업데이트 값 반환**
4. View-Model 
	 * **업데이트** -> **바인딩된 View가 업데이트**

### 특징
* **Model**과 **View** **분리**
* **View-Model : View**간 **1:N 관계** 가능
* **바인딩** 방식으로 인해 다소 **난이도 높음**