## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12941
- **난이도** : Level 2
- **풀이 일자** : `2021/11/05`

## 2. 문제 접근

A배열의 가장 작은 수와 B배열의 가장 큰 수를 곱해서 더하면 된다. 왜 레벨 2인지 이해가 안가는 문제...

## 3. 소스코드

```python
def solution(A,B):
    A = sorted(A)
    B = sorted(B, reverse=True)

    sum = 0
    for i in range(len(A)):
        sum = sum + (A[i] * B[i])

    return sum
```
