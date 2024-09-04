---
title: "트리 구조 (Tree)"
excerpt: "[C++]자료구조 - 트리"

categories:
  - 자료구조
tags:
  - [Data Structure]

permalink: /data-structure/tree/

toc: true
toc_sticky: true
use_math: true

date: 2024-08-09
last_modified_at: 2024-08-15
published: true
---

# 👑 트리 구조 (Tree)

`트리(Tree)`란 `그래프`의 일종으로, 사이클을 가지지 않으며, 계층적 구조를 가지는 <br>

노드들의 집합이다. 각 노드들은 수많은 자식 노드를 가질 수 있지만, `루트 노드`를 제외하면 <br>

`부모 노드`는 단 하나이다. 트리에서 두 노드 사이를 잇는 경로는 정확히 1개이며, 트리는 사이클이 <br>

없는 연결 그래프이기 때문에, `n`개의 노드가 있다면, `n-1`개의 간선이 필요하다.

<br>

## 💡 트리 기본 개념

<center><img src="https://github.com/user-attachments/assets/a40acc84-1f3e-4934-b20f-1b9821383e81"></center>

- `루트 노드(Root Node)` : 트리의 최상위 노드로, 유일하게 부모 노드가 없는 노드

- `부모 노드(Parent Node)` : 자식 노드를 가진 노드

- `자식 노드(Child Node)` : 부모 노드에 의해 연결된 하위 노드

- `형제 노드(Sibling Node)` : 같은 부모 노드를 공유하는 노드들

- `리프 노드(Leaf Node)` : 자식이 없는 노드로 트리의 말단을 이루는 노드

- `서브트리(Subtree)` : 하나의 노드와 그 노드의 모든 자식 노드들로 이루어진 트리 구조

- `레벨(Level)` : 루트 노드를 0레벨로 하고, 그 아래로 각 계층이 1씩 증가하는 구조 <br>
                 (루트 노드의 레벨에 따라 달라질 수 O)

<br>

## 💡 트리의 종류

트리의 종류에는 `이진 트리`, `이진 탐색 트리`, `AVL 트리`, `힙(Heap)`, `레드-블랙 트리` 등 <br>

다양한 트리가 존재하며, 각자의 특징들을 가지고 있어, 다양한 자료구조와 알고리즘에서 사용된다.

<br>

### 🌳 이진 트리

`각 노드가 최대 두 개의 자식 노드를 가질 수 있는 트리`를 `이진트리(Binary Tree)`라 한다. <br>

최대 2개의 자식 노드를 가지며, 자식이 없을 수도, 1개만 있을 수도 있다. 이진트리의 종류에는 <br>

`정 이진 트리(Full Binary Tree)`, `포화 이진 트리(Perfect Binary Tree)`, `완전 이진 트리` <br> 

`(Complete Binary Tree)` 등이 존재한다.

<br>

- `정 이진 트리(Full Binary Tree)`

    + 트리의 모든 노드가 0 or 2개의 자식 노드를 가지는 트리이다.

    + 자식을 하나만 가지는 노드가 없어야 한다.

- `완전 이진 트리(Complete Binary Tree)`

    + 트리에서 마지막 레벨을 제외한 모든 레벨이 완전히 채워져 있으며, 마지막 레벨의 노드가 <br>
      왼쪽으로 몰려 있는 트리

    + 마지막 레벨 `h`에서 $ 1 ~ 2^h - 1 $ 개의 노드를 가질 수 있다.

- `포화 이진 트리(Perfect Binary Tree)`

    + 모든 노드가 2개의 자식 노드를 가지며, 모든 리프 노드가 동일한 레벨을 가지는 트리이다.

    + 정 이진 트리이면서 완전 이진 트리인 이진트리이다.

<center><img src="https://github.com/user-attachments/assets/6db4eb23-51df-4fe5-be16-b4b4604751c6"></center>

<br>

### 🌳 이진 탐색 트리 (Binary Search Tree, BST)

`이진 탐색 트리 (BST)`란 이진 트리의 일종으로, 각 노드의 왼쪽 자식 노드는 해당 노드보다 작은 <br>

값을, 오른쪽 자식 노드는 큰 값을 가지는 특징을 가진다. 즉, 어떠한 노드의 왼쪽 서브트리의 값들은 <br>

모두 해당 노드보다 작으며, 오른쪽 서브트리의 값들은 모두 큰 값들을 가진다.

<center><img src="https://github.com/user-attachments/assets/fc914ea4-37a2-4871-99d2-3557973f356d" width="450"></center>

<br>

## 💡 트리의 순회 (Traversal)

트리의 순회란 트리 구조를 따라 모든 노드를 방문하는 과정을 의미한다. 트리의 순회 방법에는 다양한 <br>

방법들이 존재하며, `레벨 순회`, `전위 순회`, `중위 순회`, `후위 순회` 등이 대표적이다. <br><br>

트리를 코드로 구현하는 방법에도 다양한 방법들이 존재한다. 클래스나 구조체를 이용하여 구현할 수도 <br>

있지만 간단하게 배열을 통해서도 구현이 가능하다.

```c++
// class를 사용한 구현
class Node {
public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
      data = val;
      left = nullptr;
      right = nullptr;
    }
};

// 배열을 사용한 구현
// 왼쪽 자식, 오른쪽 자식, 부모를 저장할 배열을 만들어 구현
// 각 인덱스가 노드이며, 인덱스의 자식, 부모를 저장
int left_child[9] = {0, 2, 4, 0, 0, 7, 0, 0, 0};
int right_child[9] = {0, 3, 5, 6, 0, 8, 0, 0, 0};
int parent[9] = {0, 0, 1, 1, 2, 2, 3, 5, 5};
```

<center><img src="https://github.com/user-attachments/assets/327edf89-1809-4ce4-8f92-f0d3096ba456" width="450"></center>

<br>

### ✔ 레벨 순회(Level-order Traversal)

레벨 순회는 말 그대로 트리의 레벨 순으로 방문하는 순회이다. 간단하게 루트 노드에서 `BFS`를 돌리면 <br>

그것이 바로 레벨 순회이다.

<center><img src="https://github.com/user-attachments/assets/8aa14417-78cb-4bff-8f02-883c1836c973" width="450"></center>

<br>

### ✔ 전위 순회(Preorder Traversal)

전위 순회는 재귀적으로 다음과 같이 정의할 수 있다. <br>

    1. 현재 정점을 방문한다.
    2. 왼쪽 서브트리를 전위 순회한다.
    3. 오른쪽 서브트리를 전위 순회한다.

<center><img src="https://github.com/user-attachments/assets/1b3f791b-f8ea-4f53-9d34-15754a9ab173" width="450"></center>

```c++
void preorder(Node* node) const {
    if (node == nullptr) return;

    cout << node->data << " ";
    preorder(node->left);  // 왼쪽 서브트리 전위 순회
    preorder(node->right); // 오른쪽 서브트리 전위 순회
}
```

<br>

### ✔ 중위 순회(Inorder Traversal)

중위 순회도 재귀적으로 다음과 같이 정의가 가능하다. <br>

만약 트리가 `이진 탐색 트리`라면 **크기 순으로 방문**하게 된다.

    1. 왼쪽 서브트리를 중위 순회한다.
    2. 현재 정점을 방문한다.
    3. 오른쪽 서브트리를 중위 순회한다.

<center><img src="https://github.com/user-attachments/assets/20485c50-1d1b-43af-b00f-2b356d218c5e" width="450"></center>

```c++
void inorder(Node* node) const {
    if (node == nullptr) return;

    inorder(node->left);  // 왼쪽 서브트리 중위 순회
    cout << node->data << " ";
    inorder(node->right); // 오른쪽 서브트리 중위 순회
}
```

<br>

### ✔ 후위 순회(Postorder Traversal)

후위 순위 역시 재귀적으로 정의한다. <br>

    1. 왼쪽 서브 트리를 후위 순회한다.
    2. 오른쪽 서브 트리를 후위 순회한다.
    3. 현재 정점을 방문한다.

<center><img src="https://github.com/user-attachments/assets/78816049-a903-40a8-b733-19770acbaab5" width="450"></center>

```c++
void postorder(Node* node) const {
    if (node == nullptr) return;

    postorder(node->left);  // 왼쪽 서브트리 후위 순회
    postorder(node->right); // 오른쪽 서브트리 후위 순회
    cout << node->data << " ";
}
```



