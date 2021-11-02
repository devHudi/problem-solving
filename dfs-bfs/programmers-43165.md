## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/43165
- **난이도** : Level 2
- **주제** : DFS/BFS
- **풀이 일자** : `2021/09/08`

## 2. 문제 접근

재귀를 통해 0부터 시작하여 각 숫자마다 음수, 양수로 구분하여 더하는 2개의 분기를 만든다. 그렇게 모든 숫자를 다 더하면 모든 경우의 수를 알 수 있고 `target` 과 일치한 결과가 나왔을 때의 경우만 세면 된다.

이전에 DFS/BFS 를 모를 때 이 문제를 접근했다가 포기했었는데, 개념을 알고 접근하니 20분만에 금방 풀 수 있었다.

## 3. 소스코드

```python
def dfs(numbers, current, target, hit_count):
    if len(numbers) == 0:
        return hit_count + (current == target)

    n = numbers[-1]

    negative_case = dfs(numbers[:-1], current - n, target, hit_count)
    positive_case = dfs(numbers[:-1], current + n, target, hit_count)

    return negative_case + positive_case

def solution(numbers, target):
    return dfs(numbers, 0, target, 0)
```

## 4. 배운점

DFS/BFS 문제는 이미 존재하는 그래프에서 탐색하는 것 뿐만이 아니라 현재 노드에서 뻗어나갈 노드를 재귀적으로 생성해서 탐색하는 것도 범주안에 들게 되는 것을 알게 되었다.
