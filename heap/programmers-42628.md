## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/42628
- **난이도** : Level 3
- **주제** : 힙
- **풀이 일자** : `2021/08/07`

## 2. 문제 접근

우선순위큐는 일반적인 큐와 _'순차적으로 값이 출력된다'_ 라는 특성은 같으나, 순차적인 기준이 입력된 순서가 아닌 각 값의 고유의 우선순위에 따른다는 점이 차이점이다. 본 문제에서 제시한 '이중우선순위큐' 는 마치 덱 (Deque) 처럼 우선순위가 가장 높은 값 혹은 낮은 값을 양쪽에서 출력할 수 있는 자료구조를 말한다.

힙 (Heap) 을 이용하여 우선순위 큐를 구현할 수 있다. 파이썬에서 제공하는 `heapq` 모듈은 기본적으로 최소힙 (Min Heap) 으로 구현되어 있다. 따라서 최소값을 출력함에는 문제가 없다. 최대값을 출력하는 작업은 조금 코드를 추가하면 쉽게 구현할 수 있다.

값이 들어올때마다 `heappush` 를 통해 힙 정렬이 진행되므로, 최대값은 리스트의 맨 뒤에 있거나 맨 뒤에서 두번째에 존재한다. 힙은 이진트리의 형태를 하고 있는데, 같은 부모의 자식 노드끼리는 정렬이 보장되지 않는 특성이 있기 때문이다. 즉 최소힙에서 최대값을 가져오기 위해서는 뒤에서 최대 2개의 값만 비교하면 된다. 이를 고려하여 `pop_max` 함수를 작성했다.

레벨이 3인데에 비해 쉽게 풀려, 첫 제출만에 바로 풀이에 성공하였다.

## 3. 소스코드

```python
import heapq

def pop_max(heap):
    if len(heap) == 1:
        return heap.pop()
    elif len(heap) >= 2:
        if (heap[-1] >= heap[-2]): return heap.pop(-1)
        elif (heap[-1] < heap[-2]): return heap.pop(-2)

def solution(operations):
    heap = []

    while len(operations) > 0:
        operation = operations.pop(0)
        opcode = operation.split(" ")[0]
        operand = int(operation.split(" ")[1])

        if opcode == "D" and len(heap) <= 0:
            continue

        if opcode == "I":
            heapq.heappush(heap, operand)
        elif opcode == "D":
            if operand == -1:
                heapq.heappop(heap)
            elif operand == 1:
                pop_max(heap)

    if len(heap) == 0: return [0, 0]
    else:
        min = heap[0]
        max = pop_max(heap)
        return [max, min]
```

## 4. 배운점

최소힙에서 최대값을 효율적으로 가져오는 방법에 대해 알게되었다.
