## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/42748
- **난이도** : Level 1
- **주제** : 정렬
- **풀이 일자** : `2021/08/04`

## 2. 문제 접근

파이썬으로 풀면 매우 쉬운 문제. 주어진 `commands` 파라미터에 따라 리스트를 슬라이스하고, `sorted` 를 사용하여 오름차순 정렬한 뒤 값을 가져오면 된다.

## 3. 소스코드

```python
def solution(array, commands):
    result = [
        sorted(array[cmd[0] - 1:cmd[1]])[cmd[2] - 1] for cmd in commands
    ]

    return result
```

## 4. 배운점

지인에게 `for` 문으로 리스트에 `append` 하는 것 보다 **리스트 컴프리헨션 (List Comprehension)** 을 사용하는 것이 실행 속도가 빠르다고 들어 파이써닉하게 코드를 작성해보았다.
