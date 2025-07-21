---
{"dg-publish":true,"permalink":"/DevWiki/Sources/유니티 조건부 컴파일 (CSharp지시문, 전처리기) 관련/","noteIcon":"","created":"2024-09-18T17:59:01.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---

## 에디터에서 유니티 조건부 컴파일(C# 지시문)시 주의
예를들어 에디터와 IOS에 대한 조건부 컴파일을 설정하고 에디터에서 실행할 때 빌드 플랫폼이 IOS로 잡혀있는 상황이라면
if UNITY_EDITOR
if UNITY_IOS

둘다 true에 해당함에 유의해야 함

## 커스텀 스크립팅 심볼
C#지시문을 사용하여 특정한 스크립팅 심볼이 정의됨, 되지 않음에 따라 조건부 컴파일을 수행할 수 있다

 **Edit** > **Project Settings** > **Player**로 이동한 다음 **Other Settings** 패널에서 **Script Compilation**까지 아래로 스크롤