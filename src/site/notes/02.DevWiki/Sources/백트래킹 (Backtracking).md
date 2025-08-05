---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/백트래킹 (Backtracking)/","noteIcon":"","created":"2025-08-05T10:10:32.775+09:00","updated":"2025-08-05T10:22:25.118+09:00"}
---

# 백트래킹 (Backtracking)

> 해를 찾는 도중, 현재 경로가 해가 될 가능성이 없다고 판단되면 이전으로 되돌아가 다른 경로를 탐색하는 알고리즘

- **[[02.DevWiki/Sources/DFS (깊이 우선 탐색, Depth-First Search)\|DFS (깊이 우선 탐색, Depth-First Search)]]** 혹은 재귀호출에 기반한 알고리즘
	- **가지치기(Pruning)** 를 통해 불필요한 탐색을 줄임.
- 모든 가능한 해를 탐색하는 [[02.DevWiki/Sources/브루트포스 (Brute-force)\|브루트포스 (Brute-force)]] 방식에 비해 효율적.

### 특징
- **가지치기 (Pruning)**
    - 현재 상태에서 더 나갈 필요가 없다고 판단될 경우 더 탐색하지 않고 이전 단계로 돌아감
	- 필요 없는 경우의 수를 판단하지 않으므로 성능 증가

---
### 관련 문서
[[02.DevWiki/Sources/DFS (깊이 우선 탐색, Depth-First Search)\|DFS (깊이 우선 탐색, Depth-First Search)]]
