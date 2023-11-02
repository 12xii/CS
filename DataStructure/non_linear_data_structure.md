# Non-linear data structure 비선형 자료 구조

- 비선형 자료 구조 : 하나의 데이터 뒤에 N개의 데이터가 이어질 수 있는, 1:N / N:N 구조로 데이터가 나열

---

## 그래프 Graph

- 데이터를 포함하는 정점 vertex / node 과 정점을 잇는 간선 edge 로 구성된 자료구조
- 일반적인 그래프의 표현식은 각 용어의 앞 글자를 따 $ G = (V, E) $로 표현

### 용어
- 인접 adjacent : 두 정점이 간선으로 연결된 경우
- 차수 degree : 정점에 연결된 간선의 수
- 진입 차수 in-degree : 해당 정점으로 향하는 간선의 수를 의미
- 진출 차수 out-degree : 해당 정점에서 나가는 간선의 수
- 경로 path : 한 정점에서 다른 정점으로 이어지는 정점들의 리스트
- 경로 길이 path length : 경로를 구성하는 간선의 수
- 단순 경로 simple path : 모두 다른 정점으로 구성된 경로를 의미
- 사이클 cycle : 한 정점에서 시작해 같은 정점으로 돌아올 수 있는 경로를 의미

### 종류
- 무방향 그래프 undirected graph
    - 간선에 방향성 X
    - 두 정점 $A, B$가 인접할 때 간선 $(A, B)$와 $(B, A)$는 동일함
    - 정점의 개수가 $n$개일 때 최대 간선의 개수는 $n \times (n - 1) \div 2$ 개
- 방향 그래프 directed graph
    - 간선에 방향성 O
    - 두 정점이 인접할 때 $A$에서 $B$로 향하는 간선을 $\left\langle A , B\right\rangle $로 표시
        - $\left\langle A, B\right\rangle$과 $\left\langle B, A \right\rangle$은 다른 간선
    - 정점의 개수가 $n$개일 때 최대 간선의 개수는 $n \times (n - 1)$ 개
- 부분 그래프 sub graph 
    - 기존 그래프에서 일부 정점이나 간선을 제외
- 가중치 그래프 weighted graph
    - 간선에 비용이나 가중치가 할당됨
- 완전 그래프 complete graph / 연결 그래프 connected graph
    - 간선을 최대로 가짐
    - 정점의 개수가 $n$개일 때 무방향 그래프의 간선 수가 $n \times (n - 1) \div 2$이면 완전 그래프
    - 정점의 개수가 $n$개일 때 방향 그래프의 간선 수가 $n \times (n - 1)$이면 완전 그래프
- 유향 비순환 그래프 DAG, Directed Acyclic Graph
    - 방향 그래프이면서 사이클이 없는 그래프

### 경로 탐색
- 너비 우선 탐색 BFS, Breadth-First Search
    - 탐색을 시작하는 정점에서 가까운 정점을 먼저 탐색
    - 발견한 정점과 인접한 정점들을 탐색하며 이전에 방문했는지 확인 이후 큐에 삽입
    - 과정
        1. 시작 정점을 인큐, 인접한 정점들을 역시 인큐한 뒤 방문할 노드가 더이상 없으면 시작 정점을 디큐
        2. 큐의 프론트에 있는 정점에서 방문한 정점 제외 인접한 정점을 인큐하고 디큐
        3. 2의 과정을 큐가 빌 때까지 반복
    - 비가중치 그래프에서 시작 정점부터 특정 정점까지의 최단 거리를 알 수 있음
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99960F405BD01A8D18)

- 깊이 우선 탐색 DFS, Depth-First Search
    - 시작 정점에서 탐색 가능한 최대 깊이의 정점까지 탐색
    - 재귀 또는 스택으로 구현
    - 과정
        1. 시작 정점 A를 스택에 push, 인접한 탐색 가능한 정점 중 한 정점 B를 방문하고 푸시
        2. B에서 인접한 탐색 가능한 정점을 방문하고 스택에 푸시
        3. 더 이상 탐색 가능한 정점이 없을 때까지 2를 반복
        4. 더 이상 탐색 가능한 정점이 없다 = 탐색 가능한 최대 깊이에 도달했음이므로 스택에서 pop하여 역순으로 방문하며 탐색 가능한 정점이 있는지 확인
    - 특정 정점에서 다른 정점까지의 경로를 알 수 있음
        - 재귀 호출로 구현 시 방문해야 하는 정점을 저장할 필요가 없어 BFS 대비 저장 공간을 적게 사용
![](https://gmlwjd9405.github.io/images/algorithm-dfs-vs-bfs/dfs-example.png)