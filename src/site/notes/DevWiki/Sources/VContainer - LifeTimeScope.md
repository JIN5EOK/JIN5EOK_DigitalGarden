---
{"dg-publish":true,"permalink":"/DevWiki/Sources/VContainer - LifeTimeScope/","noteIcon":"","created":"2025-05-23T02:08:59.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---

# LifeTimeScope

- 의존성 생명주기 관리
- `Parent` : LifeTimeScope간 상속 기능
- Auto Inject Game Objects
    - 자동으로 의존성 주입을 실행할 게임 오브젝트 등록

### LifeTimeScope간 상속관계

- 클래스의 상속 관계와 비슷
    - 자식 `LifeTimeScope`는 상속받은 부모의 `LifeTimeScope` 의 의존성을 공유할 수 있다
- 상속관계는 에디터 `Hierarchy` 상의 계층구조에 의해 결정