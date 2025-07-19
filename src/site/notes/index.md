---
{"dg-publish":true,"permalink":"/index/","tags":["gardenEntry"]}
---


디지털 노트 테스트
### 개발 위키
[[03.Resource/Development Wiki/Algorithm Wiki\|Algorithm Wiki]]
[[03.Resource/Development Wiki/CS Wiki\|CS Wiki]]
[[03.Resource/Development Wiki/CSharp Wiki\|CSharp Wiki]]
[[03.Resource/Development Wiki/Data Structure Wiki\|Data Structure Wiki]]
[[03.Resource/Development Wiki/Unity Wiki\|Unity Wiki]]


> 개별 애니메이션의 시작이나 종료 등 특정 상태에 진입할 때 실행할 로직을 정의할 수 있게 해준다

- 이벤트 함수 종류
    - **OnStateEnter**
        - 해당 상태에 **처음** 들어왔을 때 호출
    - **OnStateUpdate**
        - 상태에 진입한 동안 **매 프레임** 호출
    - **OnStateExit**
        - 상태가 **종료** 될 때 호출
    - **OnStateMove**
        - **루트모션 사용시 매 프레임** 호출
        - 루트모션? : 애니메이션을 통해 대상의 실제 위치가 변하는 애니메이션 방식
    - **OnStateIK**
        - **IK 사용시** 호출
        - IK? : 애니메이션의 관절(팔, 다리 등)을 목표 위치에 **자동으로 맞춰주는 보정 시스템**
    - **OnStateMahineEnter**
        - **서브 상태머신에 진입**할 때
    - **OnStateMachineExit**
        - **서브 상태머신에서 나올 때**
- OnStateEnter, OnStateMachineEnter는 사실상 발동조건이 유사하지만 Behaviour 스크립트가 클립에 붙어있을 땐 OnStateEnter, 서브 상태머신에 붙어있을 경우 OnStateMachineEnter가 실행된다는 차이가 있음