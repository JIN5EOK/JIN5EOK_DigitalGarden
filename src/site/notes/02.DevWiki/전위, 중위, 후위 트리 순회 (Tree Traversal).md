---
{"dg-publish":true,"permalink":"/02.DevWiki/전위, 중위, 후위 트리 순회 (Tree Traversal)/","noteIcon":""}
---

# 트리 순회 (Tree Traversal)

> **트리 순회**는 [[02.DevWiki/Sources/트리 (Tree)\|트리]] 자료구조의 **모든 노드를 한 번씩 방문하는 과정**을 말한다. 
> 순회 방식은 크게 [[02.DevWiki/Sources/DFS (깊이 우선 탐색, Depth-First Search)\|DFS (깊이 우선 탐색, Depth-First Search)]]과 [[02.DevWiki/Sources/BFS (너비 우선 탐색, Breadth-First Search)\|BFS (너비 우선 탐색, Breadth-First Search)]]으로 나뉘는데, 그 중 **깊이 우선 탐색**은 노드를 방문하는 순서에 따라 **전위, 중위, 후위 순회**로 세분화 시킬 수 있다.

# 전위, 중위, 후위 순회!

* 다음과 같은 특징을 가지고 있다는 사실을 염두에 두면 쉽게 기억할 수 있다
* **전, 중, 후**는 **Root의 위치**이다.
	* 전위 : Root, Left, Right
	* 중위 : Left, Root, Right
	* 후위 : Left, Right, Root
* **깊이 우선 탐색 기반**
	* Root,Left,Right라 얼핏 보면 **세가지 노드를 하나씩 번갈아가며 방문하는걸로 잘못 이해하기 쉬움**
		* 그러나 Root->Left->Right->Root->Left->Right..를 무한 반복하는게 아님! 😁
	* **기본적으로 좌측노드를 우선으로 깊이 우선탐색**을 진행하되 **실질적으로 방문처리**하는 노드의 **우선순위**가 달라지는 것!

### 1. 전위 순회 (Pre-order Traversal)

> **Root -> left -> Right**
> **루트 → 왼쪽 서브트리 → 오른쪽 서브트리** 순서로 노드를 방문한다.

![Preorder-traversal.gif](/img/user/02.DevWiki/Files/Preorder-traversal.gif)

- **특징**
	- 통상적인 [[02.DevWiki/Sources/DFS (깊이 우선 탐색, Depth-First Search)\|DFS (깊이 우선 탐색, Depth-First Search)]] 과 별반 다를 바 없음
	- 그냥 좌측 자식 노드를 우선으로 **깊이 우선 탐색**을 진행하면서 **만나는 노드들을 모두 방문처리** 하면 됨!
	- **트리의 구조를 가장 잘 표현**하는 방식.

### 2. 중위 순회 (In-order Traversal)

> **Left -> Root -> Right**
> **왼쪽 서브트리 → 루트 → 오른쪽 서브트리** 순서로 노드를 방문한다.

![Inorder-traversal.gif](/img/user/02.DevWiki/Files/Inorder-traversal.gif)

* **기본적인 동작 방식**
	* **모든 노드를 방문할 때 까지** 좌측 자식 우선 **깊이 우선 탐색**을 진행한다,단 방문처리는 하지 않는다
	* 방문한 노드가 **단말 노드**라면 **방문처리**한다.
	* 방문한 노드의 **좌측 자식이 방문된 상태**라면 **방문처리**한다.

- **특징**
	- **이진 검색 트리(BST)** 를 중위 순회하면 노드의 키 값이 **오름차순으로 정렬**된 결과를 얻을 수 있다.
	- **수식 트리의 중위 표기법 (Infix Notation)**
		- 수식 트리에서 중위 순회를 수행하면 우리가 일반적으로 사용하는 **중위 표기법**(예: `A + B * C`)을 얻을 수 있다!

### 3. 후위 순회 (Post-order Traversal)

> **Left -> RIght -> Root**
> **왼쪽 서브트리 → 오른쪽 서브트리 → 루트** 순서로 노드를 방문한다.

![Postorder-traversal.gif](/img/user/02.DevWiki/Files/Postorder-traversal.gif)

* **기본적인 동작 방식**
	* **모든 노드를 방문할 때 까지** 좌측 자식 우선 **깊이 우선 탐색**을 진행한다, 단 방문처리는 하지 않는다
	* 방문한 노드가 **단말 노드**라면 **방문처리**한다.
	* 방문한 노드의 **좌측과 우측 자식이 방문된 상태**라면 **방문처리**한다.

- **특징**
	- **자식 노드를 모두 방문한 후**에 **부모 노드를 방문**하므로, 트리의 **메모리 해제(삭제)** 작업에 사용된다. (자식을 먼저 해제해야 부모를 안전하게 해제할 수 있기 때문)
	- **수식 트리의 후위 표기법 (Postfix Notation)**
		- 수식 트리에서 후위 순회를 수행하면 연산자가 피연산자 뒤에 오는 **후위 표기법**(예: `A B + C *`)을 얻을 수 있다. 
		- 후위 표기법은 스택을 사용하여 표현식을 효율적으로 계산하는 데 사용된다.

---

## 순회 예시

아래와 같은 이진 트리가 있다고 가정해보자.

```
      F
     / \
    B   G
   / \   \
  A   D   I
     / \
    C   E
```

-   **전위 순회 (Root-Left-Right)**: `F` → `B` → `A` → `D` → `C` → `E` → `G` → `I`
-   **중위 순회 (Left-Root-Right)**: `A` → `B` → `C` → `D` → `E` → `F` → `G` → `I`
-   **후위 순회 (Left-Right-Root)**: `A` → `C` → `E` → `D` → `B` → `G` → `I` → `F`

---

### 관련 문서
[[02.DevWiki/Sources/트리 (Tree)\|트리 (Tree)]]
[[02.DevWiki/Sources/DFS (깊이 우선 탐색, Depth-First Search)\|DFS (깊이 우선 탐색, Depth-First Search)]]
[[02.DevWiki/Sources/BFS (너비 우선 탐색, Breadth-First Search)\|BFS (너비 우선 탐색, Breadth-First Search)]]
