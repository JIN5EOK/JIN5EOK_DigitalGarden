---
{"dg-publish":true,"permalink":"/01.DevLog/Sources/241129_메인스레드에서만 실행 가능한 Mixpanel SDK 문제 해결하기/","noteIcon":"","created":"2024-11-29T21:03:48.000+09:00","updated":"2025-07-20T02:49:56.000+09:00"}
---

# 개요
Mixpanel에서 제공해주는 유니티 SDK를 설치하고 아래와 같이 믹스패널에 로그 이벤트를 전송할 수 있다.
``` C#
// import mixpanel package to your code
using mixpanel; 
// start using library methods
Mixpanel.Track("event_name");
```
일반적으로는 잘 작동한다 (지금까지 잘 작동해왔고) , 그러나 메인스레드가 아닌 곳에서 위 코드를 수행하면 아래와 같은 오류를 발생시킨다.
```
Unknown encountered on server. Message:'HasKey can only be called from the main thread. Constructors and field initializers will be executed from the loading thread when loading a scene. Don't use this function in the constructor or field initializers, instead move initialization code to the Awake or Start function.' when writing an object UnityEngine.Debug:LogError (object) 
```
Mixpanel.Track 함수의 내부 구조를 타고 올라가다 보니 **PlayerPrefs**를 사용하여 데이터를 사용하고 있었고 **PlayerPrefs는 메인스레드 외의 상황에서는 사용이 불가능**하기 때문에 발생한 문제였다.

> 🤔 이 오류의 원인을 파악하자마자 가장 먼저 든 생각은 "데이터와 로그 전송 로직만 따로 빼서 메인스레드에서 실행될 수 있도록 코드를 우회하면 되지 않을까?"였다. 하지만..

이번 로그 작업의 주요 요구사항은 **모바일 환경에서 다른 앱으로 전환한 상태**에서도 로그 전송이 되야한다는 것이었다. 즉, **메인스레드가 정지된 상태**에서도 로그가 전송될 수 있어야 했다..

# 해결 방안

논의된 해결책은 다음 두가지였다.

### 1. Mixpanel API 직접 호출
https://developer.mixpanel.com/reference/track-event
믹스패널 API를 직접 호출하자
- **장점:
    - 추후에 필요할 경우 Mixpanel SDK에서 제공되지 않는 기능들도 구현 가능함
- **단점:
    - 기존 SDK를 통해 전송하던 로그와 API 전송 방식이 섞여 관리가 복잡해질 수 있다.
    - 추후 유지보수 시 직접 호출한 API 호출 부분이 더 많은 코드를 필요로 할 수 있다.

### 2. Mixpanel SDK 수정
믹스패널 SDK를 수정하여 멀티스레드에서도 동작 가능하도록 하자!
* **장점:
	* 기존 SDK 사용 방식에서 벗어나지 않는다
* **단점
	* SDK를 수정함으로써 생기는 사이드 이펙트 발생 여지?
	* 추후 SDK 버전 업데이트시 대응이 어려워질 수 있다

# 선택

우리 프로젝트의 요구사항을 고려했을 때, **1번 방안**이 더 현실적이라는 결론을 내렸다.

그 이유는 다음과 같다:
- 백그라운드에서 전송해야 하는 로그 종류가 많지 않으므로 구현 비용이 크지 않고 관리가 그렇게 복잡해지지 않을거라는 판단, 오히려 기존 SDK를 수정함으로써 발생하는, 기존의 수많은 로그들에 생기는 사이드 이펙트가 훨씬 크리라고 생각된다
- Mixpanel의 공식 문서에서 API 사용법이 잘 정리되어 있어 구현이 어렵지 않으리라고 판단

> 😇 만약 SDK만으로 해결 불가능한 이슈들이 더 생긴다면 그때는 SDK를 삭제하고 API로 완전 대체하는 방향도 생각할 수 있으리라 생각된다.
