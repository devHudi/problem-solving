## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/43162
- **난이도** : Level 3
- **주제** : DFS/BFS
- **풀이 일자** : `2021/09/12`

## 2. 문제 접근

어렵지 않은 문제였다. 임의의 노드 한개에서 DFS 탐색한 이후 아직 방문하지 않은 임의의 노드에서 다시 DFS 탐색을 시작하는 것을 반복해서 모든 노드를 방문하면 된다. 이 때 DFS를 새롭게 탐색한 횟수가 네트워크의 횟수가 된다.

## 3. 소스코드

```python
def dfs(graph, v, visited):
    visited[v] = True
    for node, connected in enumerate(graph[v]):
        if node != v and connected == 1 and visited[node] == False:
            # 다음 노드가 자기자신이 아니며, 연결이 되어있고, 방문하지 않아야 탐색함.
            dfs(graph, node, visited)

    return visited

def solution(n, computers):
    visited = [False] * n
    count = 0
    while all(visited) == False:
        for n, v in enumerate(visited):
            if v == False:
                count += 1
                visited = dfs(computers, n, visited)

    return count
```

## 4. 배운점

파이썬에는 `all` 과 `any` 함수가 존재한다. `all` 은 iterable 객체의 모든 값이 True 면 True 를 반환하고, 그렇지 않으면 False 를 반환한다. `any` 는 하나라도 True 면 True 를 반환하고, 그렇지 않으면 False 를 반환한다. 이 두개의 함수를 익히게 되었다.
