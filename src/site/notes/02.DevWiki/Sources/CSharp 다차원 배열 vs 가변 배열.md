---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 다차원 배열 vs 가변 배열/","noteIcon":"","updated":"2025-07-31T10:51:29.000+09:00"}
---



### 다차원 배열 (Multidimensional Array)
`int[,] values = new int[3, 4];`
- **연속된 공간**에 저장
- 인덱스 접근: **values\[x, y]**
- 차수별 크기를 모두 동시에 지정해야 한다
- 각 차원의 크기는 서로 다를 수 있지만, **형태는 고정**되어 있다 
	- 예: 3x4, 5x5 등
- 모든 요소가 한 번에 초기화된다

### 가변 배열 (Jagged Array)
 `int[][] values = new int[3][];`
- 각각의 **하위 배열은 별도 공간**에 존재
- 인덱스 접근: **values\[x]\[y]**
- 상위 배열의 크기만 먼저 지정, 하위 배열은 나중에 개별적으로 초기화할 수 있다
- 각 **하위 배열의 길이가 서로 달라도 된다**
	- 예: 첫 줄은 3개, 둘째 줄은 5개 등