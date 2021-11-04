## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12899
- **난이도** : Level 2
- **풀이 일자** : `2021/11/05`

## 2. 문제 접근

3진법으로 접근하였다. 주어진 10진수를 0, 1, 2 로 구성된 3진수로 변경한 다음. 1, 2, 3으로 구성된 3진수로 변경했다. 그 다음 3을 4로 치환하였다.

## 3. 소스코드

```python
def solution(n):
    q = n # 몫

    r_list = []

    while q > 0:
        r = q % 3
        q = q // 3

        r_list.insert(0, r)

    trinary = []
    if q > 0: trinary = [q]

    trinary.extend(r_list)
    # 3진법으로 변환

    for i in range(len(trinary) - 1):
        cursor = - (i + 1)
        if trinary[cursor] <= 0:
            trinary[cursor - 1] = trinary[cursor - 1] - 1
            trinary[cursor] = trinary[cursor] + 3
    # 0, 1, 2 3진법을 1, 2, 3 3진법으로 변환

    return (str(int("".join(map(str, trinary)).replace("3", "4"))))
    # 3을 4로 치환
```
