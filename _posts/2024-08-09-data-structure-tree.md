---
title: "트리 구조 (Tree)"
excerpt: "[C++]자료구조 - 트리"

categories:
  - Data Structure
tags:
  - [Data Structure]

permalink: /data-structure/tree/

toc: true
toc_sticky: true
use_math: true

date: 2024-08-09
last_modified_at: 2024-08-09
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

### 🌳 





