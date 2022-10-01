# DFS / BFS

## [Graph - List] 방문한 노드 번호 순서대로 출력

```
0 - 1 - 2
|   |   |
3 - 4 - 5
```

```python
graph_list = [
    [1, 3],     # node 0
    [0, 2, 4],  # node 1
    [1, 5],     # node 2
    [0, 4],     # node 3
    [1, 3, 5],  # node 4
    [3, 4],     # node 5
]
```

### [Graph - List] DFS (Recursion)

```python
def dfs(graph, x, visited=[]):
    visited.append(x)
    for nx in graph[x]:
        if nx not in visited:
            visited = dfs(graph, nx)
    return visited
```

### [Graph - List] DFS (Stack)

```python
def dfs(graph, x):
    visited = [x]
    stack = deque([x])
    while stack:
        x = stack.pop()
        if x not in visited:
            visited.append(x)
        for nx in reversed(graph[x]):
            if nx not in visited:
                stack.append(nx)
    return visited
```

### [Graph - List] BFS (Queue)

```python
def bfs(graph, x):
    visited = [x]
    queue = deque([x])
    while queue:
        x = queue.popleft()
        for nx in graph[x]:
            if nx not in visited:
                visited.append(nx)
                queue.append(nx)
    return visited
```

## [Graph - Matrix] 방문한 노드 번호 순서대로 출력

```
0 - 1 - 2
|   |   |
3 - 4 - 5
```

```python
graph_matrix = [
    [0, 1, 0, 1, 0, 0],     # node 0
    [0, 0, 1, 0, 1, 0],     # node 1
    [0, 1, 0, 0, 0, 1],     # node 2
    [1, 0, 0, 0, 1, 0],     # node 3
    [0, 1, 0, 1, 0, 1],     # node 4
    [0, 0, 0, 1, 1, 0],     # node 5
]
```

### [Graph - Matrix] DFS (Recursion)

```python
def dfs(matrix, x, visited=[]):
    visited.append(x)
    for nx in range(len(matrix[x])):
        if nx not in visited and matrix[x][nx] == 1:
            visited = dfs(matrix, nx)
    return visited
```

### [Graph - Matrix] DFS (Stack)

```python
def dfs(matrix, x):
    visited = [x]
    stack = deque([x])
    while stack:
        x = stack.pop()
        if x not in visited:
            visited.append(x)
        for nx in reversed(range(len(matrix[x]))):
            if nx not in visited and matrix[x][nx] == 1:
                stack.append(nx)
    return visited
```

### [Graph - Matrix] BFS (Queue)

```python
def bfs(matrix, x):
    visited = [x]
    queue = deque([x])

    while queue:
        x = queue.popleft()
        for nx in range(len(matrix[x])):
            if nx not in visited and matrix[x][nx] == 1:
                visited.append(nx)
                queue.append(nx)
    return visited
```

## [Grid] 방문한 노드 번호 순서대로 출력

```
(0, 0) - (0, 1) - (0, 2)
  |        |        |
(1, 0) - (1, 1) - (1, 2)
  |        |        |
(2, 0) - (2, 1) - (2, 2)
```

```python
grid = [[0, 0, 0], 
        [0, 0, 0], 
        [0, 0, 0]]

dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]
```

### [Grid] DFS (Recursion)

```python
def dfs(grid, x, y, visited=[]):
    n, m = len(grid), len(grid[0])
    
    visited.append((x, y))
    for k in range(4):
        nx, ny = x + dx[k], y + dy[k]
    
        if 0 <= nx < n and 0 <= ny < m:
            if (nx, ny) not in visited:
                visited = dfs(grid, nx, ny)
    return visited
```

### [Grid] DFS (Stack)

```python
def dfs(grid, x, y):
    n, m = len(grid), len(grid[0])
    
    visited = [(x, y)]
    queue = deque([(x, y)])
    while queue:
        x, y = queue.pop()
        if (x, y) not in visited:
            visited.append((x, y))
        for k in range(4):
            nx, ny = x + dx[k], y + dy[k]
            if 0 <= nx < n and 0 <= ny < m:
                if (nx, ny) not in visited:
                    queue.append((nx, ny))
    return visited
```

### [Grid] BFS (Queue)

def bfs(grid, x, y):
    n, m = len(grid), len(grid[0])
    
    visited = [(x, y)]
    queue = deque([(x, y)])
    while queue:
        x, y = queue.popleft()
        for k in range(4):
            nx, ny = x + dx[k], y + dy[k]
            if 0 <= nx < n and 0 <= ny < m:
                if (nx, ny) not in visited:
                    visited.append((nx, ny))
                    queue.append((nx, ny))
    return visited
```
