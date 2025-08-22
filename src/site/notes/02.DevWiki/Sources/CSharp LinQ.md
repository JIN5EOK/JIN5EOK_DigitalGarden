---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp LinQ/","noteIcon":"","updated":"2025-08-17T16:00:15.000+09:00"}
---

### LINQ가 뭔가?

데이터 컬렉션을 쿼리(문의,질의)하고 조작하는 데 사용하며 SQL과 비슷한 방식으로 데이터를 처리할 수 있다

### 기초 질의어
- `From`
    - 데이터 소스 정의
    - `from num in nums`
        - nums의 원소를 num으로 정의

- `Where`
    - 데이터 필터링
    - `where num % 2 == 0`
        - num을 2로 나누고 나머지가 0인 경우만 필터링

- `Select`
    - 원하는 데이터 추출
    - `select num`
        - 연산 결과에 부합하는 num들을 추출

- `OrderBy`
    - 데이터 정렬
    - `orderby num descending`
        - 데이터를 내림차순으로 정렬

- `Group By`
    - 데이터 그룹화
    - `group num by num % 2 == 0;`
        - 데이터를 2로 나누었을때 0인 그룹과 아닌 그룹으로 나눈다

- `Join`
    - 두 개 이상의 데이터 소스 결합
    - `from fruit in fruits`
    - `join name in names on fruit equals name`
    - `select new { fruitName = fruit, peopleName = name };`
        
- `Let`
    - 쿼리 작성중 중간 변수 선언