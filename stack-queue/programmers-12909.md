## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12909
- **난이도** : Level 2
- **풀이 일자** : `2021/11/05`

## 2. 문제 접근

자료구조론에서 스택을 배울 때 가장 단골로 제시되는 예시가 괄호 오류 검사이다.

`(` 는 스택에 넣고, `)` 를 만나면 스택을 pop 한다. 모든 과정을 끝내고 스택이 빈 상태가 오류가 없는 문자열.

## 3. 소스코드

```python
def solution(s):
    stk = []

    for c in s:
        if c == "(": stk.append(c)
        elif c == ")":
            if len(stk) == 0: return False # 닫힌 괄호로 시작 되었을 경우 무조건 오류
            stk.pop()

    return len(stk) == 0
```
