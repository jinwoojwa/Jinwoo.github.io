---
title: "BFS 알고리즘"
excerpt: "[C++]BFS : Breadth-First Search"

categories:
  - 알고리즘
tags:
  - [algorithm]

permalink: /algorithm/algorithm-bfs/

toc: true
toc_sticky: true

date: 2024-05-28
last_modified_at: 2024-05-28
---

# 👑 BFS (Breadth First Search)

`너비 우선 탐색 (BFS)` 이란 시작 정점을 방문한 후 시작 정점에 인접한 모든 정점들을 <br>

우선 방문하는 검색 알고리즘이다. `BFS`는 출발노드에서 목표노드까지의 `최단 길이 경로`를 <br>

보장한다는 장점을 가지고 있다.

<br>

# 💡 BFS 과정

- 시작 정점을 방문한 후 인접한 모든 정점들을 우선 방문한다.

- 아래 그림과 같이 노드들을 `넓게` 탐색한다.

<center><img src="https://github.com/jinwoojwa/jinwoo.github.io/assets/112393728/61f79482-b469-435a-bad6-bf14be3a05f0" width="500"></center>

<br>

# 🧩 구현 (C++)

- 일반적으로 `큐 (queue)`와 특정 노드의 방문 여부를 검사하기 위한 `배열`을 사용하여 구현한다.

- 2차원 배열에서 `dx, dy` 배열을 사용하면 편하게 상하좌우 확인이 가능하다.

```c++
#include <iostream>
#include <queue>

using namespace std;

int board[row][col] = {0, };    // 2차원 배열을 예시로 들었다.
bool visit[row][col];           // 방문 여부 검사를 위한 배열
int r = 10, c = 10;             // r = 행의 수, c = 열의 수

int dx[4] = {1, 0, -1, 0};      // dx, dy를 사용하여
int dy[4] = {0, 1, 0, -1};      // 상,하,좌,우 4칸을 확인

int main() {
    queue<pair<int, int>> Q;    // 2차원 좌표를 넣기 위해 pair 사용

    // 출발 노드에 방문했다는 것을 표시 (문제에 따라 출발 노드는 달라질 수 있음)
    visit[0][0] = 1;

    // 큐에 출발 노드 push (C++11 이상부터는 make_pair 대신 중괄호 {} 사용 가능)
    Q.push(make_pair(0, 0));

    while(!Q.empty()) {         // 큐에 원소가 있는 경우 반복
        pair<int, int> cur = Q.front();   //  큐에서 좌표를 꺼내고, pop
        Q.pop();

        // 2차원 배열에서 cur 좌표의 상하좌우 좌표를 검사해야 한다.
        // 이때, dx, dy 배열과 for문을 사용하여 편하게 검사한다.
        for (int dir = 0; dir < 4; ++dir) {
            int x = cur.first + dx[dir];
            int y = cur.second + dy[dir];

            // 먼저 x, y 좌표가 범위를 넘는지 확인 (런타임 에러 방지)
            if (x < 0 || x >= r || y < 0 || y >= c) continue;
            
            // 이미 방문했다면 or 해당 좌표가 0이라면(이어져 있지 않은 노드) -> continue
            if (visit[x][y] || board[x][y] != 1) continue;

            visit[x][y] = 1;  // 방문하지 않았고, 인접한 노드이므로, 방문 표시
            Q.push({x, y});   // 큐에 해당 좌표 넣어줌 -> 해당 좌표에서 다시 상하좌우 검사 
        }
    }
    return 0;
}
```


