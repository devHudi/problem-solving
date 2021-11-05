## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12911
- **난이도** : Level 2
- **풀이 일자** : `2021/11/05`

## 2. 문제 접근

주어진 정수로 이진수를 구하고, 1을 센다. 그 뒤 주어진 수를 1씩 증가시키고, 증가된 수를 이진수로 변환한 뒤, 1의 개수 구하고 최초와 비교하는 것을 반복한다.

최초로 1의 개수가 일치하는 수를 반환한다.

## 3. 소스코드

```python
def binary(dec):
    r = []
    q = dec
    while q > 1:
        r.append(q % 2)
        q = q // 2

    b = str(q) + "".join(list(map(str, r)))

    return b

def solution(n):
    cnt = binary(n).count("1")

    next_n = n + 1
    while True:
        if cnt == binary(next_n).count("1"):
            return next_n
        next_n = next_n + 1

    return next_n
```
