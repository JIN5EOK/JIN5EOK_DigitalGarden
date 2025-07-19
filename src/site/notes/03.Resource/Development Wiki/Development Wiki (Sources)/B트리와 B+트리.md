---
{"dg-publish":true,"permalink":"/03.Resource/Development Wiki/Development Wiki (Sources)/B트리와 B+트리/","noteIcon":"","created":"2025-06-10T13:17:17.043+09:00","updated":"2025-07-20T02:19:17.554+09:00"}
---

> 데이터베이스 및 파일 시스템에서 **대용량 데이터를 효율적 저장/검색** 하기 위해 사용되는 **균형 잡힌 트리구조**

* 특징
	* 여러개의 자식노드를 가질 수 있다
		* 최대 자식노드 갯수를 **M**이라고 할 떄
		* 최소 키 갯수 : **M / 2 -1**개
		* 최대 키 갯수 : **M - 1**개
		* 최소 자식 노드 갯수 **M / 2** 개
	* 한 노드에 여러개의 **키**와 **자식노드**가 들어갈 수 있음
	* 모든 리프 노드들은 같은 차수에 존재해야 한다
### B트리
![BTree.png](/img/user/03.Resource/Development%20Wiki/Development%20Wiki%20(Sources)/Files/BTree.png)
* 데이터가 **내부노드, 리프노드** 모두에 저장됨
* **리프노드간 연결** 없음
	* 때문에 **순차접근**에 **비효율**적임
### B+ 트리
![BPlusTree.png](/img/user/03.Resource/Development%20Wiki/Development%20Wiki%20(Sources)/Files/BPlusTree.png)
* **데이터**가 **리프노드**에만 저장됨
	* **내부노드**에는 데이터가 아닌 자식노드를 가리키는 **주소값**이 존재
* **리프노드간 연결** 존재
	* **순차접근** 성능이 **우수**함


