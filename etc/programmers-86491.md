## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/86491
- **난이도** : Level 2
- **풀이 일자** : `2021/11/14`

## 2. 문제 접근

주어진 사이즈와 그 사이즈의 가로, 세로를 돌려 새로운 리스트를 만들어 최소의 사이즈를 구하도록 비교하였다.

## 3. 소스코드

```python
def solution(sizes):
    rotated_sizes = list(map(lambda t: [t[1], t[0]], sizes))

    lengths = set()
    for size in sizes:
        lengths.add(size[0])
        lengths.add(size[1])

    lengths = sorted(list(lengths))

    for length in lengths:
        o1 = [length >= size[0] for size in sizes]
        o2 = [length >= size[0] for size in rotated_sizes]
        o3 = [o1[i] or o2[i] for i in range(len(o1))]

        if all(o3):
            c1 = list(filter(lambda size: o1[sizes.index(size)], sizes))
            c2 = list(filter(lambda size: o2[rotated_sizes.index(size)], rotated_sizes))
            max_v_len = max([size[1] for size in c1 + c2 ])
            return max_v_len * length
```
