---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/삼각함수 (Trigonometric Functions)/","noteIcon":"","created":"2025-08-13T21:27:39.503+09:00","updated":"2025-08-13T21:27:39.503+09:00"}
---

# 삼각함수 (Trigonometric Functions)

게임 개발에서 각도, 회전, 원형 운동, 파동 등 주기적인 움직임을 다룰 때 필수적으로 사용되는 수학적 도구이다.

---

## 1. 기본 정의 (직각삼각형)

직각삼각형의 한 각(θ)에 대한 세 변(빗변, 높이, 밑변)의 비율을 나타낸다.

-   **Sin(θ)** = 높이 / 빗변
-   **Cos(θ)** = 밑변 / 빗변
-   **Tan(θ)** = 높이 / 밑변

![Pasted image 20250811164348.png](/_Files/Images/Pasted%20image%2020250811164348.png)

---

## 2. 단위 원 (The Unit Circle) - 핵심

프로그래밍에서는 직각삼각형보다 **반지름이 1인 원 (단위 원)**으로 삼각함수를 이해하는 것이 훨씬 유용하다. 단위 원을 사용하면 **각도를 좌표로 변환**할 수 있다.

-   원점(0,0)을 중심으로 반지름이 1인 원을 그린다.
-   이 원 위의 한 점 (x, y)까지의 각도를 θ라고 할 때, x, y 좌표는 다음과 같다.
    -   **`x = cos(θ)`**
    -   **`y = sin(θ)`**

이 관계는 각도를 이용해 원형 궤도를 따라 움직이는 위치를 계산하거나, 방향 벡터를 구하는 등 수많은 곳에 활용된다.

![Pasted image 20250811164400.png](/_Files/Images/Pasted%20image%2020250811164400.png)

---

## 3. 라디안(Radian)과 각도(Degree)

-   **각도 (Degree):** 우리가 일상적으로 사용하는 0° ~ 360° 단위. Unity 에디터 인스펙터에서는 주로 각도를 사용한다.
-   **라디안 (Radian):** 호의 길이를 반지름으로 나눈 값. 수학 공식이나 프로그래밍 언어의 삼각함수 라이브러리(`Mathf.Sin`, `Mathf.Cos` 등)는 대부분 라디안을 입력값으로 받는다.

> 😱 **주의!** Unity의 `Mathf` 함수들은 라디안을 사용하므로, 각도 값을 사용하려면 반드시 변환해야 한다. 이로 인해 버그가 자주 발생한다.

```csharp
// 각도(degree)를 라디안(radian)으로 변환
float angleInRad = angleInDeg * Mathf.Deg2Rad;

// 라디안(radian)을 각도(degree)로 변환
float angleInDeg = angleInRad * Mathf.Rad2Deg;
```

---

## 4. 주요 활용 사례

### 원형 운동
오브젝트를 특정 지점 주위로 회전시킬 때 사용한다.

```csharp
// time 변수가 계속 증가한다고 가정
float angle = Time.time * speed;

// cos과 sin을 이용해 원형 궤도의 x, y 좌표를 계산
float x = center.x + Mathf.Cos(angle) * radius;
float y = center.y + Mathf.Sin(angle) * radius;

transform.position = new Vector3(x, y, 0);
```

### 주기적인 움직임 (파동)
Sin 함수의 결과값(-1 ~ 1)을 이용하여 부드러운 상하 움직임이나 좌우 움직임을 만들 수 있다.

```csharp
// 오브젝트를 제자리에서 부드럽게 위아래로 움직이게 함
float yOffset = Mathf.Sin(Time.time * frequency) * amplitude;
transform.position = initialPosition + new Vector3(0, yOffset, 0);
```

### 방향 벡터 계산
특정 각도가 가리키는 방향의 단위 벡터를 구할 수 있다.

```csharp
float angleInRad = 45f * Mathf.Deg2Rad; // 45도
Vector2 direction = new Vector2(Mathf.Cos(angleInRad), Mathf.Sin(angleInRad));
// direction은 (0.707, 0.707) 근사값을 가짐
```

---

## 5. 역삼각함수와 Atan2

-   **`Asin`, `Acos`, `Atan`:** 변의 비율을 통해 각도를 역으로 계산할 때 사용한다.
-   **`Mathf.Atan2(y, x)`:** **가장 유용하고 중요한 역삼각함수.**
    -   벡터의 (x, y) 성분을 입력하면, 원점으로부터 해당 벡터까지의 각도를 라디안 단위로 정확하게 반환한다.
    -   `Atan(y/x)`와 달리 360도 전체 방향을 올바르게 계산하며, x가 0일 때의 오류도 없다.

```csharp
// (1, 1) 방향 벡터의 각도를 계산
Vector2 direction = new Vector2(1, 1);
float angleInRad = Mathf.Atan2(direction.y, direction.x);
float angleInDeg = angleInRad * Mathf.Rad2Deg; // 결과: 45도
```

---

### 관련 문서
[[02.DevWiki/Sources/벡터의 내적과 외적 (Dot and Cross Product)\|벡터의 내적과 외적 (Dot and Cross Product)]]
