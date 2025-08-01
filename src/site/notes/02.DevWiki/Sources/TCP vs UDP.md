---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/TCP vs UDP/","noteIcon":"","created":"2024-11-23T21:30:26.000+09:00","updated":"2025-07-19T22:58:36.977+09:00"}
---

> 둘다 OSI 7계층 중 데이터 패킷의 전송을 담당하는 4계층-전송계층에 해당

## TCP (Transmission Control

### 전송 제어 프로토콜

- **연결지향**
    - 서로 연결됨 전제
- **3 way handshake**
    - SYN ->
    - <- SYN+ACK
    - ACK ->
- 데이터 전달과 순서 보장
    - **세그먼트**에 **전송 관련 정보**들을 같이 보내기 때문

## UDP (User Datagram Protocol)

### 사용자 데이터그램 프로토콜

- 연결지향 **아님**
- 데이터 전달 보증 **없음**
- 순서 보장 **안됨**

> 🤔 아니.. 그럼 TCP보다 안좋은거 아닌가? IP통신과 뭐가 다른거지?

- **TCP**와의 차별점
    - 기본 기능이 없으므로 **추가기능 구현**이 용이함
- **IP통신**과의 차이점
    - **포트 + 체크섬** 존재

## 사실 대부분은 TCP

- 사실 **대부분**의 통신은 **TCP**를 통해 이루어짐
- **HTTP3**에서 **UDP 프로토콜** 사용하면서 UDP도 주목받는 중