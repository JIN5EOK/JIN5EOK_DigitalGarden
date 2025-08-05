---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 의존성 주입 - VContainer , Zenject, Extenject/","noteIcon":"","created":"2025-05-23T02:09:39.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---

# 의존성 주입이란..
[[02.DevWiki/Sources/의존성 주입\|의존성 주입]]

# 유니티 의존성 주입 프레임워크

- `Zenject`, `Extenject`
    - 기능이 많으나 다소 무겁고 어려움
    - `Zenject`는 현재 지원 중단, `Extenject`가 좀 더 최신까지 업데이트 되었음
    - 유니티의 씬 및 Monobehaviour에 최적화
- `VContainer`
    - 가장 널리 쓰이는 프레임워크
    - `Extenject`와 달리 `Monobehaviour`가 아닌 C#코드를 의존성 주입 시작점으로 잡을 수 있다
    - 기능이 많지는 않으나 가볍고 빠르고 단순함
        - `Zenject` 대비 5~10배 빠르다고 함

# VContainer
[[02.DevWiki/Sources/유니티 DI프레임워크 - VContainer\|유니티 DI프레임워크 - VContainer]]

# Zenject, Extenject
[[02.DevWiki/Sources/유니티 DI 프레임워크 - Zenject, Extenject\|유니티 DI 프레임워크 - Zenject, Extenject]]