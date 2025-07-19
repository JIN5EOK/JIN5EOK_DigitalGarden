---
{"dg-publish":true,"permalink":"/DevLog/Sources/250103_UnityPurchasing 구글 플레이,앱스토어 인앱결제/","noteIcon":"","created":"2025-05-23T02:15:10.342+09:00","updated":"2025-07-20T02:49:56.119+09:00"}
---

# 개요

### 목표
- 게임 내에 `GooglePlay`/`AppStore` 구매 항목을 가져오고 인앱 결제 수행

### 사용 라이브러리
- `UnityEngine.Purchasing`

# 상세

## 주요 키워드
- `ConfigurationBuilder` : IStoreListener를 생성하기 위한 빌더 클래스
- `IStoreListener` : 스토어 관련 이벤트 발생시 이벤트를 수신할 객체가 상속받는 인터페이스
- `IStoreController` : 스토어 관련 기능을 수행하는 컨트롤러 인터페이스

## 개발과정

### `IStoreListener` 의 구체 클래스 선언

- `IStoreListener` 이벤트 함수가 포함된 인터페이스일 뿐이므로 사용 목적에 맞게 적절한 구체 클래스를 구현해야 한다
- `IStoreController` 는 이미 구현되어있는 구체 클래스가 있으므로 추가 기능을 붙이고 싶은 상황이 아니라면 굳이 구현해주지 않아도 됨

### `IStoreController` 초기화 및 상품 추가

- `ConfigurationBuilder` 를 통해 `IStoreListener` 를 초기화 할 수 있다
    
    - 상품 항목 추가하기
        
        - Product ID : 구독/인앱결제 상품의 ID, `GooglePlayConsole`이나 `AppStoreConnect` 에서 세팅 가능
        - ProductType : 상품의 타입, 예를들면 구독상품인지, 한번 구매하면 끝인 상품인지 등..
    - `ConfigurationBuilder` 로 상품을 추가하고 IStoreListener 생성 예시
        
        ```csharp
        ConfigurationBuilder builder = ConfigurationBuilder.Instance(StandardPurchasingModule.Instance());
        foreach (var product in products)
        {
            builder.AddProduct(product.id, product.type);    
        }
        UnityPurchasing.Initialize(myStoreListener, builder);
        ```
        
- `ConfigurationBuilder` 를 통해 성공적으로 초기화에 성공했다면 `IStoreListener` 의 초기화 함수가 호출된다.
    
- `IStoreListener` 의 초기화 함수
    
    - `void OnInitialized(**IStoreController controller**, IExtensionProvider extensions);`

> 성공 함수에서 반환된 IStoreController를 사용하여 스토어 관련 작업을 수행할 수 있다

### 상품 구매 화면 호출

- `IStoreController` 를 통해 상품을 구매할 수 있다
    - `storeController.InitiatePurchase(SubscriptionId);`

> 상품 구매시도 결과는 IStoreListener의 이벤트 함수를 통해 전달받을 수 있고 이를 통해 구매 관련 기능들을 구현하면 된다