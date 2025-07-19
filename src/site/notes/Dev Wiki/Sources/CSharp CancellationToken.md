---
{"dg-publish":true,"permalink":"/Dev Wiki/Sources/CSharp CancellationToken/","noteIcon":"","created":"2024-11-17T15:45:29.000+09:00","updated":"2025-07-19T22:58:36.948+09:00"}
---

비동기 작업을 취소시키기 위한 구조체, CancellationToken을 이용해 외부에서 비동기 작업의 취소를 요청할 수 있다.

### CancellationToeknSource
CancellationToken을 생성하고 취소 요청을 발생시켜 자신이 발행한 CancellationToken들에게 전달한다
### CancellationToken
CancellationTokenSource에서 발행되며 취소 신호를 비동기 작업에게 전달한다
