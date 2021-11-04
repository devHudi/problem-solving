## 1. 문제 개요

- **문제 링크** : programmers.co.kr/learn/courses/30/lessons/12906
- **난이도** : Level 1
- **주제** : 기타
- **풀이 일자** : `2021/11/04`

## 2. 문제 접근

커서 역할을 하는 `prev` 변수를 하나 두고, 현재 보고 있는 숫자와 같으면 결과 리스트에 넣지 않는다.

## 3. 소스코드

```python
def solution(arr):
    ret = []

    prev = None
    for n in arr:
        if n != prev: ret.append(n)
        prev = n

    return ret
```
