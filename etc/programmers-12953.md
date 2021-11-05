## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12953
- **난이도** : Level 2
- **풀이 일자** : `2021/11/05`

## 2. 문제 접근

주어진 수 중 가장 큰 수에 1부터 N 까지 곱해가며, 그 때 마다 주어진 나머지 수를 곱한 수에 나눠 모두가 나머지가 0인 경우를 최소공배수로 리턴하였다.

단, 곱한 그 결과값이 주어진 모든 수를 곱한 것 보다 작을 동안으로 제한하였다.

다 풀고 알아보니 유클리드 호제법이라는 알고리즘으로 쉽게 풀 수 있는 것 같다. 나중에 다시 한번 풀어봐야겠다.

## 3. 소스코드

```python
from functools import reduce

def solution(arr):
    sorted_arr = sorted(list(set(arr)))

    max_mul = reduce(lambda acc, cur: cur * acc, sorted_arr, 1)
    # 최소공배수는 주어진 모든 수를 다 곱한 수 보다 클 수 없다.

    cur = sorted_arr.pop()
    mul = 1

    # 제일 큰 수에 1부터 N까지 곱해가며 (max_mul 보다 작을 동안), 그수에 주어진 나머지 수 를 나누어 나머지가 0인 최초의 수가 최소공배수
    while mul <= max_mul:
        tmp = cur * mul

        if all([tmp % divider == 0 for divider in sorted_arr ]):
            return tmp

        mul = mul + 1

```
