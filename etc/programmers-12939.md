## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12939
- **난이도** : Level 2
- **풀이 일자** : `2021/11/06`

## 2. 문제 접근

왜 레벨 2지?...

## 3. 소스코드

```python
def solution(s):
    l = sorted(list(map(int, s.split(" "))))
    return f"{l[0]} {l[-1]}"
```
