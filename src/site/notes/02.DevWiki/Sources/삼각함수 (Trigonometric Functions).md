---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/삼각함수 (Trigonometric Functions)/"}
---

> **직각삼각형의 변들의 길이 비율을 각도와 연관시키는 함수**
## 기본 정의

**직각삼각형**의 **각(θ, 라디안)** 에 대한 **세 변(빗변, 높이, 밑변)의 비율**을 나타낸다.

* **삼각함수**
	* **각도(라디안)** -> **세 변중 두 변의 비율**로 변환
	- **Sin(θ)** = **높이 / 빗변**
	- **Cos(θ)** = **밑변 / 빗변**
	- **Tan(θ)** = **높이 / 밑변**
- **역삼각함수**
	- **세 변중 두 변의 비율** -> **각도(라디안)** 으로 변환
	- **Asin(높이 / 빗변)** = **θ**
	- **Acos(밑변 / 빗변)** = **θ**
	- **Atan(높이 / 밑변)** = **θ**
		- 변의 비율을 통해 각도를 역으로 계산할 때 사용한다.

---

## 주요 활용 사례

### 원형 운동 혹은 상하, 좌우 운동
* 오브젝트를 특정 지점 주위로 회전시키거나 특정 지점 에서 상하, 좌우로 운동시킬 수 있다.

```csharp
// time 변수는 계속 갱신
float angle = time * speed;

// cos과 sin을 이용해 원형 궤도의 x, y 좌표를 계산
float x = center.x + Mathf.Cos(angle) * radius;
float y = center.y + Mathf.Sin(angle) * radius;

transform.position = new Vector3(x, y, 0);
```

### 방향 벡터 계산
* 특정 각도가 가리키는 방향의 단위 벡터를 구할 수 있다.

```csharp
float angleInRad = 45f * Mathf.Deg2Rad; // 45도 -> 라디안
Vector2 direction = new Vector2(Mathf.Cos(angleInRad), Mathf.Sin(angleInRad));
```

---
### 관련 문서
[[02.DevWiki/Sources/단위원 (Unit Circle)\|단위원 (Unit Circle)]]
[[02.DevWiki/Sources/벡터의 내적과 외적 (Dot and Cross Product)\|벡터의 내적과 외적 (Dot and Cross Product)]]
[[02.DevWiki/Sources/라디안(Radian)과 디그리(Degree)\|라디안(Radian)과 디그리(Degree)]]