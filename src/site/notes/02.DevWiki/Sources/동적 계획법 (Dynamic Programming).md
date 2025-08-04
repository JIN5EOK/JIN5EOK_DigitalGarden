---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/동적 계획법 (Dynamic Programming)/","noteIcon":"","created":"2025-06-07T03:15:43.000+09:00","updated":"2025-08-03T22:31:42.000+09:00"}
---


> 큰 문제를 작은 문제로 쪼개어 해결하는 기법

- 큰 문제를 작은 문제로 쪼갠다
- 한번 연산한 작은 문제의 답을 저장(메모이제이션), 중복 계산하지 않는다

### 특징
- **최적 부분 구조 (Optimal Substructure)**
    - 문제의 최적해가 부분 문제들의 최적해로 구성됨.
- **중복되는 부분 문제 (Overlapping Subproblems)**
    - 동일한 부분 문제가 반복적으로 나타나며, 부분 문제의 결과를 저장하여 재사용 한다.

### 접근 방식
- **메모이제이션 (Memoization)**
    - **재귀 호출**을 사용하여 문제를 작은 단위로 쪼갠다.
    - 한 번 계산한 부분 문제의 결과는 배열이나 해시 테이블에 저장하고, 동일한 문제가 다시 나타나면 저장된 값을 반환한다.
    - 예) 피보나치 수열을 재귀적으로 구할 때 n이 커질수록 동일한 문제를 계속 반복 수행하는 케이스가 있는데 메모제이션을 적용하면 횟수가 획기적으로 단축됨
- **타뷸레이션 (Tabulation)**
    - 반복문을 사용하여 계산하고 결과를 테이블(배열)에 순서대로 저장한다.
    - 반복문을 통해 미리 필요한 결과를 테이블에 저장한 이후 필요한 작업을 수행한다.

> 메모제이션은 재귀 호출로 인해 성능이 저하되는 부분이 있어 타뷸레이션이 성능적으로 우수한 경우가 많다

### 관련 문서
[[02.DevWiki/Sources/LCS (Longest Common Subsequence, Longest Common Substring)\|LCS (Longest Common Subsequence, Longest Common Substring)]]
[[02.DevWiki/Sources/그리디 알고리즘 (Greedy Algorithm)\|그리디 알고리즘 (Greedy Algorithm)]]
[[02.DevWiki/Sources/그리디 알고리즘과 동적 계획법의 차이\|그리디 알고리즘과 동적 계획법의 차이]]