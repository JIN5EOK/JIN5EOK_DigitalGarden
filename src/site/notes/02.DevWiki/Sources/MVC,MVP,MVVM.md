---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/MVC,MVP,MVVM/"}
---

## MVC (Model-View-Controller)

### 개요
* 기능을 **Model, View, Controller** 세 가지 역할로 구분
* UI와 비즈니스 로직을 분리하는것이 목표

### 구성 요소
*   **Model** 
	* **데이터**와 **비즈니스 로직** 담당
	* **View**와 **Controller**에 대해 **알지 못함**, 상태 변경을 알리는 **이벤트**를 가질 수 있음
*   **View** 
	* 사용자에게 보여지는 **UI** 담당
	* Model의 **데이터를 표시**하며, 사용자의 **입력**을 받아 **Controller에 전달**.
	* 변경된 **Model**의 데이터를 전달받거나 **모델 데이터 변경 이벤트** 등 간접 참조를 통해 View 업데이트
*   **Controller**
	*  **사용자의 입력을 처리**하고, 이에 따라 **Model과 View를 변경**
	*  Model과 View의 중재자 역할 수행

### 작동 방식
1.  사용자의 입력이 **View**를 통해 들어옴
2.  **View**는 입력을 **Controller**에 전달
3.  **Controller**는 비즈니스 로직에 따라 **Model**의 상태를 업데이트
4.  **Model**의 상태가 변경 되면 컨트롤러가 View에게 데이터를 전달해주거나 등록된 이벤트를 실행해 **UI를 업데이트**

### 특징
* **View와 Model의 의존성**: View가 Model을 직접 참조하므로, 둘 사이의 **결합도가 높음**
* **Controller와 View의 관계**: 하나의 Controller가 여러 View를 관리하는 **1:N 관계**가 가능

> Controller와 View의 1:N 관계를 만들기 용이하나 View와 Model간의 결합도가 높은것이 단점

## MVP (Model-View-Presenter)

### 개요
* MVC의 단점인 **View와 Model의 높은 결합도**를 해결하기 위해 등장한 패턴
* **Presenter**가 View와 Model 사이의 모든 상호작용을 중재하며, **View와 Model을 완전히 분리함**

### 구성 요소
*   **Model** 
	*   MVC와 동일하게 **데이터와 비즈니스 로직**을 담당
*   **View** 
	*   사용자 입력을 받으면 모든 처리를 Presenter에 위임하며, Presenter의 지시에 따라 UI를 업데이트.
	*   보통 인터페이스(`IView`)로 정의되어 Presenter와의 결합도를 낮춤
*   **Presenter**
	*   View와 Model 사이의 중재자 역할을 수행
	*   View로부터 입력을 받아 Model을 업데이트하고, Model의 변경 결과를 다시 View에 전달하여 UI 갱신을 요청

### 작동 방식
1.  사용자 입력이 **View**에 들어옴
2.  **View**는 입력을 **Presenter**에 그대로 전달
3.  **Presenter**는 **Model**의 데이터를 업데이트하고, 필요한 데이터를 가져옴
4.  **Presenter**는 **View**의 인터페이스를 통해 **UI 업데이트를 직접 지시**
5.  **View**는 Presenter의 지시에 따라 **UI를 갱신**

### 특징
*   **View와 Model의 분리**: Presenter를 통해 상호작용하므로 **View와 Model이 완전히 분리**
*   **Presenter와 View의 관계**: Presenter가 View의 메서드를 직접 호출하므로, **1:1 관계**로 강하게 연결

> MVC대비 Presenter와 View가 더욱 끈끈하게 이어진 대신 Model과 View는 분리되는 방식이라고 할 수 있다

## MVVM (Model-View-ViewModel)

### 개요
* Presenter와 View의 강한 결합을 **데이터 바인딩(Data Binding)** 을 통해 해결한 패턴

### 구성 요소
*   **Model**
	* MVC, MVP와 동일하게 데이터와 비즈니스 로직을 담당
*   **View**
	* UI와 관련된 시각적 요소 및 레이아웃을 담당
	* **ViewModel**의 데이터를 **바인딩**하여 화면에 표시하고, 사용자 입력을 **커맨드(Command)** 를 통해 ViewModel에 전달
*   **View-Model** 
	* View를 표현하기 위한 **상태(State)와 프레젠테이션 로직**을 가짐
	* **View에 표시될 데이터**와 **View의 동작을 정의**하는 **커맨드**를 노출
	* **Model을 참조**하여 필요한 데이터를 가져오거나 가공
	* **View에 대한 참조가 전혀 없음!**

### 작동 방식
1. 사용자 입력이 **View**에 발생하면, 바인딩된 **커맨드**를 통해 **ViewModel**에 전달
2. **ViewModel**은 커맨드를 실행하여 **Model**의 데이터를 업데이트
3. **ViewModel**은 Model로부터 변경된 데이터를 가져와 자신의 상태 데이터
4. **ViewModel**의 데이터가 변경되면, **데이터 바인딩**을 통해 **View**의 UI가 자동으로 갱신

### 특징
* **View와 ViewModel의 분리**: 데이터 바인딩을 통해 View와 ViewModel이 **느슨하게 연결(Decoupled)** ViewModel은 View를 전혀 알지 못함.
* **ViewModel과 View의 관계**: 하나의 ViewModel을 여러 View에서 재사용하는 **1:N 관계**가 가능
* **테스트 용이성**: ViewModel이 View에 대한 의존성이 전혀 없으므로, UI 없이도 **프레젠테이션 로직을 쉽게 테스트**할 수 있음
