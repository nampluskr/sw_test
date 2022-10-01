# DFS / BFS

## [Graph] 방문한 노드 번호 순서대로 출력

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

### [Graph] DFS (Recursion)

```python
def dfs(graph, x, visited=[]):
    visited.append(x)
    for nx in graph[x]:
        if nx not in visited:
            visited = dfs(graph, nx)
    return visited
```
