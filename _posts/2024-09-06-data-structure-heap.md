---
title: "힙 (Heap)"
excerpt: "[C++]자료구조 - Heap"

categories:
  - 자료구조
tags:
  - [Data Structure]

permalink: /data-structure/heap/

toc: true
toc_sticky: true
use_math: true

date: 2024-09-06
last_modified_at: 2024-09-06
published: true
---

# 👑 힙 (Heap)

`힙 (Heap)`은 `완전 이진 트리`의 일종으로, 최댓값 또는 최솟값을 빠르게 찾는 연산을 <br>

하기 위해 고안된 자료구조이다. 각 노드가 따르는 규칙에 따라 다음의 두 가지로 나눌 수 있다. <br>

- `최대 힙 (Max Heap)` : 부모 노드의 값이 자식 노드의 값보다 항상 크거나 같다.

- `최소 힙 (Min Heap)` : 부모 노드의 값이 자식 노드의 값보다 항상 작거나 같다.

힙은 `완전 이진 트리` 형태이므로, 마지막 레벨을 제외한 모든 레벨이 완전히 채워져 있으며, <br>

마지막 레벨의 노드도 왼쪽부터 채워지는 형태이다. 키 값의 대소관계는 `부모-자식` 관계에서만 <br>

성립하며, `형제` 관계에서는 성립하지 않는다. <br><br>

힙에서는 가장 높거나 가장 낮은 우선순위를 가지는 노드가 항상 루트 노드에 위치하는 특징을 <br>

가지고 있으며, `우선순위 큐`를 구현하는 데 사용된다.

<center><img src="https://github.com/user-attachments/assets/bcdd7da0-198e-482c-b201-c4868579f245" width="500"></center>

<center><img src="https://github.com/user-attachments/assets/b294d8db-4a59-42b4-a332-11c2680922ae" width="500"></center>

<br>

## 💡 구현

힙은 주로 `배열`을 사용하여 구현하며, 배열의 인덱스를 통해 부모-자식 간의 관계를 나타낸다. <br>

부모 노드의 인덱스가 `i`라고 할 때, 자식 노드의 인덱스는 왼쪽 자식부터 `2 * i`, `2 * i + 1`이다. <br>

( 완전 이진 트리의 형태이기 때문에 인덱스가 2배가 됨을 확인할 수 있다. ) <br>

또한 `i`의 부모 노드의 인덱스는 `i / 2`이다.

<br>

- `삽입`

트리의 가장 끝에 원소를 삽입하고, 추가한 원소와 해당 원소의 부모 노드의 크기를 비교하여 순서를 <br>

바꿔가며 위치를 찾는 방식으로 동작한다.

```c++


```
