## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/86051
- **난이도** : Level 1
- **풀이 일자** : `2021/11/11`

## 2. 문제 접근

괜히 한줄로 풀고 싶었다.

## 3. 소스코드

```python
def solution(numbers):
  return sum(filter(lambda n: n not in numbers, list(range(10))))
```
