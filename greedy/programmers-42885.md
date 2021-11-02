## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/42885
- **난이도** : Level 2
- **주제** : 그리디 알고리즘
- **풀이 일자** : `2021/08/28`

## 2. 문제 접근

사람을 오름차순으로 정렬한다. 보트에는 맨 처음에는 대기하는 사람 중 가장 무거운 사람을 올리고, 그 다음부터는 가장 작은 사람부터 보트의 한계까지 태운다. 이 과정을 대기하는 사람이 0명이 될 때 까지 반복한다.

(수정)

아... 정말 바보였다. 문제를 제대로 읽지 않았다. 문제 맨 처음 문단에 아래와 같은 조건이 있었는데 읽지 않고 넘긴 것 같다.

> 구명보트는 작아서 한 번에 최대 2명씩 밖에 탈 수 없고, 무게 제한도 있습니다.

구명보트에 인원 수 제한이 있다는 사실을 전혀 염두하지 않고 코드를 작성하였다. 그래서 문제를 풀어도 끝까지 찝찝했던 것 이었다. 이 조건을 확인하고 다시 코드를 작성했다.

## 3. 소스코드

### 3-1. 첫번째로 작성한 코드

```python
from collections import deque

def solution(people, limit):
    remains = deque(sorted(people))
    count = 0

    while len(remains) > 0:
        boat = 0

        while True:
            if len(remains) == 1:
                count += 1
                remains.popleft()
                break

            if boat > 0: boat += remains.popleft()
            else: boat += remains.pop()

            if boat + remains[0] > limit:
                count += 1
                break

    return count
```

### 3-2. 문제를 제대로 읽고 다시 작성한 코드

```py
from collections import deque

def solution(people, limit):
    remains = deque(sorted(people))
    count = 0

    while len(remains) > 0:
        boat = remains.pop()

        if boat + remains[0] <= limit:
            boat += remains.popleft()

        count += 1

        if len(remains) == 1:
            count += 1
            remains.pop()

    return count
```

## 4. 배운점

'그리디' 하게 문제를 접근하는 것이 아직 너무 어렵게 다가온다. 정해져있는 유형이 있는 것도 아니고, 최적의 해를 보장하는 알고리즘도 아니라서 너무 모호하게 다가온다. 이 문제도 정말 많은 시행착오 끝에 성공하게 되었다.

이 방법도 처음에는 리스트로 작성하여, `pop()` 은 문제없었지만, `pop(0)` 을 실행할 때 시간 복잡도가 $O(N)$ 이 되어 효율성 테스트에서 문제를 겪었다. 이전에 지인에게 피드백을 받으면서, `collections.deque` 은 이중 링크드 리스트로 구현되어 `popleft()` 의 시간 복잡도가 $O(1)$ 이라는 사실을 알게 되어 바로 적용해보았고, 결과는 효율성 테스트까지 성공적으로 통과하게 되었다.

(수정) 문제를 똑바로 읽어야겠다.
