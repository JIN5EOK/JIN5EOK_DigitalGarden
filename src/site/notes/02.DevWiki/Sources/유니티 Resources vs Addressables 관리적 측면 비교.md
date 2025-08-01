---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 Resources vs Addressables 관리적 측면 비교/","noteIcon":"","created":"2024-09-21T14:28:36.000+09:00","updated":"2025-07-19T22:58:36.994+09:00"}
---

## 둘은 메모리 해제 조건이 제법 다르다

### Resources의 메모리 해제 조건

- 특정 에셋에 대한 Unload 혹은 UnloadUnusedAssets를 호출할 때, 불러온 에셋을 어디서도 참조하고 있지 않아야 한다!
- Unload 예약은 불가능하다!! 오직 Unload를 호출한 시점의 조건만 판단한다.

### Addressables의 메모리 해제 조건

- 에셋에 대한 참조카운트가 0이 될 때 메모리 해제된다.
    - 어드레서블을 통해 에셋을 Load하거나 게임 오브젝트를 Instantiate할때 마다 Handle이 반환되고 참조 카운트가 1 증가한다
    - 해당 에셋, 게임 오브젝트, 핸들중 하나를 Release하면 참조 카운트가 1 감소한다

## 장단점

### Resources

- **장점**
    - 사용하기 쉽고 직관적이다
    - 참조가 없어야 해제 된다는 점에서 사용중인 에셋이 의도치 않게 메모리에서 내려가 오동작 하는 경우를 막을 수 있다.
    - Unload를 놓치더라도 UnloadUnusedAssets을 통해 사용하지 않는 리소스 정리, 메모리 누수 막기 용이함
- **단점**
    - 사용자가 메모리 언로드를 통제하기 어려움, Unload시 결과를 알수도 없고 해당 에셋에 대한 참조를 관리하기도 쉽지 않음

### Addressables

- **장점**
    - 참조카운트 관리만 잘 한다면 메모리 해제 시점을 사용자 마음대로 컨트롤 가능
- **단점**
    - 사용중인 에셋이 메모리에서 내려가 오동작하는 문제가 발생할 위험성
    - 참조카운트 관리의 까다로움, Release를 놓칠경우 메모리 누수

> Resources는 프로토타이핑과 간단한 프로젝트에 적합, Addressables는 관리 시스템만 잘 구성해 놓으면 Resources보다 메모리 외에도 기능과 관리 측면에서 우수하므로 본격적인 프로젝트에서는 Addressables를 사용하는것이 좋겠다!
