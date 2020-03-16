#GRAPH

<p align="center">
<img src = https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99E78F505BF9DB8B28 width = 40%>
</p>

- 여러개의 노드와 그 노드를 잇는 간선, 그리고 그 간선의 가중치로 이루어진 자료구조
- 무방향 그래프 / 가중치 그래프 / 방향 그래프
- 인접 행렬 / 인접 리스트

#### 유향 그래프 예
<p align="center">
  <img src = https://t1.daumcdn.net/cfile/tistory/21029250584C0F2413 width = 50%>
</p>

#### 무향 그래프 예
<p align="center">
  <img src = https://t1.daumcdn.net/cfile/tistory/2405384D584C11BC2E width = 50%>
</p>

#### 인접 행렬

- 그래프의 연결 관계를 이차원 배열로 나타내는 방식
  > adj[i][j] : 노드 i에서 노드 j로 가는 간선이 있으면 1, 아니면 0

  **인접 행렬 : 무방향 그래프**
  ```python
  class Graph:
    def __init__(self):
      graph = []

  graph = [[0 for _ in range(100)] for _ in range(100)]

  n = int(input())

  for _ in range(n):
    a, b = map(int, input().split())

    graph[a][b] = 1
    graph[b][a] = 1
  ```

  **인접 행렬 : 방향 그래프**
  ```python
  graph = [[0 for _ in range(100)] for _ in range(100)]

  n = int(input())

  for _ in range(n):
    src, des = map(int, input().split())

    graph[src][des] = 1
  ```

##

#### 인접 리스트

- 그래프의 연결 관계를 벡터로 나타내는 방식
**인접 리스트 : 무방향 그래프**
  ```python
  class Graph:
    def __init__(self):
      self.graph = {}

    def add(self, src, des):
      if src not in self.graph:
        self.graph[src] = {des}
      else:
        self.graph[src].add(des)

      if des not in self.graph:
        self.graph[des] = {src}
      else:
        self.graph[des].add(src)

    def show(self):
      for i in self.graph:
        print(i, '->', self.graph[i])
  ```
  **인접 리스트 : 방향 그래프**
  ```python
  class Graph:
    def __init__(self):
      self.graph = {}

    def add(self, src, des):
      if src not in self.graph:
        self.graph[src] = {des}
      else:
        self.graph[src].add(des)

    def show(self):
      for i in self.graph:
        print(i, '->', self.graph[i])
  ```


[참고1](https://cupjoo.tistory.com/49)
[참고2](https://kamang-it.tistory.com/entry/AlgorithmData-StructureGraph%EA%B7%B8%EB%9E%98%ED%94%84%EC%9D%B4%EB%A1%A0%EA%B3%BC-%EA%B7%B8%EB%9E%98%ED%94%84-%EA%B5%AC%ED%98%84)
[참고3](https://sarah950716.tistory.com/12)
