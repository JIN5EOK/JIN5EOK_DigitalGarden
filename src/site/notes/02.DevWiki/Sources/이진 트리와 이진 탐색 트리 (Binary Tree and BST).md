---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/이진 트리와 이진 탐색 트리 (Binary Tree and BST)/"}
---

# 이진 트리와 이진 탐색 트리

## 이진 트리 (Binary Tree)

> 각 노드가 **최대 두 개의 자식 노드**를 가질 수 있는 트리.
> 트리에 대해선 [[02.DevWiki/Sources/트리 (Tree)\|트리 (Tree)]] 참고
 
![Binary Tree.png](/img/user/02.DevWiki/Sources/Files/Binary%20Tree.png)

* **특징**
	- 각 노드는 자식으로 **왼쪽 자식(Left Child)** 과 **오른쪽 자식(Right Child)** 을 가질 수 있다.
	- 그 외에 적용되는 규칙은 없다, 다만 이진 트리에 기반하되 규칙을 추가하여 **파생된 다른 트리 구조**들이 많다.

### 이진 트리의 종류

- **포화 이진 트리 (Perfect Binary Tree)**: 모든 레벨이 노드로 꽉 차 있는 이진 트리.
- **완전 이진 트리 (Complete Binary Tree)**: 마지막 레벨을 제외한 모든 레벨이 완전히 채워져 있고, 마지막 레벨의 노드들은 왼쪽부터 채워져 있는 트리. **힙**은 완전 이진 트리를 기반으로 한다.
	- [[02.DevWiki/Sources/힙 (Heap)\|힙 (Heap)]]
- **정 이진 트리 (Full Binary Tree)**: 모든 노드가 0개 또는 2개의 자식 노드만을 갖는 트리.

## 이진 탐색 트리 (Binary Search Tree, BST)

> **효율적인 탐색 작업을 위해** 이진 트리에 규칙을 추가한 자료구조

* 이진 탐색에 대해선 [[02.DevWiki/Sources/이진 탐색 (Binary Search)\|이진 탐색 (Binary Search)]] 참고

![Binary Search Tree.png](/img/user/02.DevWiki/Sources/Files/Binary%20Search%20Tree.png)

-   **규칙**
    1.  노드의 **왼쪽 서브트리**에는 해당 노드보다 **작은 값**을 갖는 노드들만 존재한다.
    2.  노드의 **오른쪽 서브트리**에는 해당 노드보다 **큰 값**을 갖는 노드들만 존재한다.


### 장점과 단점

-   **장점**
    - 데이터가 균형 있게 분포되어 있을 경우, 탐색, 삽입, 삭제 연산이 평균적으로 **O(log n)** 의 시간 복잡도를 가져 매우 빠르다.
    - 중위 순회 시 노드를 정렬된 순서로 방문할 수 있다.
	    - [[02.DevWiki/Sources/전위, 중위, 후위 트리 순회 (Tree Traversal)\|전위, 중위, 후위 트리 순회 (Tree Traversal)]] 

-   **단점**
    - 데이터가 정렬된 순서로 삽입되는 등 트리가 **불균형(unbalanced)** 해지면 한쪽으로 치우친 **편향 트리(skewed tree)** 가 되어 성능이 저하된다!
    - 최악의 경우, 연결 리스트와 같은 구조가 되어 탐색, 삽입, 삭제가 **O(n)** 의 시간 복잡도를 갖게 된다 🥹
    - 이러한 단점을 보완하기 위해 **자가 균형(Self-Balancing)** 기능을 갖춘 **AVL 트리, 레드-블랙 트리(Red-Black Tree)** 등이 고안되었다.

* 이진 탐색 트리를 일반화한 자료구조로 M원 탐색트리가 존재한다, 이진 탐색 트리는 2원 탐색 트리라고 볼 수 있다.
	* [[02.DevWiki/Sources/M원 탐색 트리 (M-way Search Tree)\|M원 탐색 트리 (M-way Search Tree)]]


