## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/42584
- **난이도** : Level 2
- **주제** : 스택/큐
- **풀이 일자** : `2021/07/27`

## 2. 문제 접근

각 주식 가격 이후의 가격을 탐색하여 현재 주식가격보다 작은 가격이 발견될 떄 까지의 탐색 횟수를 기록하여 반환한다. 문제 접근 아이디어 자체는 매우 간단한편 이었다. 꽤 빠르게 풀어낼 수 있는 문제였다. 다만, 시간 복잡도 이슈가 발생해서 아주 조금 시행착오를 겪었다.

첫번째 소스코드는 효율성 테스트 케이스를 모두 통과하지 못하였고, 두번째 소스코드는 시간 복잡도를 개선하여 모든 테스트 케이스에 통과하게 되었다.

## 3. 소스코드

### 3-1. 효율성 테스트 실패 코드

```python
def solution(prices):
    ret = []

    while len(prices) > 0:
        cur_price = prices.pop(0)

        s = 0
        for p in prices:
            s += 1
            if cur_price > p:
                break
        ret.append(s)

    return ret
```

### 3-1. 시간복잡도 개선 코드

```python
def solution(prices):
    ret = []

    for i, cur_price in enumerate(prices):
        s = 0
        for j in range(i + 1, len(prices)):
            s += 1
            if cur_price > prices[j]:
                break
        ret.append(s)

    return ret
```

## 4. 배운점

문제 주제가 스택/큐 여서 파이썬 리스트 메소드인 `pop` 을 사용하여, 큐와 같이 순서대로 리스트에서 데이터를 꺼내어 가격을 비교하려고 시도했다. 이런 방식으로 처음 작성한 소스코드는 왜인지 모든 효율성 테스트 케이스를 통과하지 못하였다. '_혹시 pop 의 시간 복잡도가 굉장히 큰 것 아닐까?_' 라는 생각이 들어 조금 검색해본 결과 다음과 같은 정보를 얻게 되었다.

- `l.pop()` : $O(1)$
- `l.pop(i)` : $O(N)$

잠깐만 생각해보면 너무나 당연하다. `pop` 메소드에 아무 파라미터도 전달하지 않으면, 가장 마지막의 원소를 제거하여 시간 복잡도는 $O(1)$ 이지만, 나의 경우처럼 `pop` 메소드로 가장 앞의 원소를 제거하면, 그 이후 원소의 인덱스를 모두 변경해야하니 $O(N)$ 으로 큰 시간적 낭비가 발생한다.

본 문제의 경우 굳이 기존 가격 리스트에서 원소를 제거할 필요 없이, 현재 가격의 인덱스를 가리키는 변수를 따로 두어 탐색하면 된다. 이런 방법으로 코드를 개선하니 모든 테스트 케이스를 통과했다! 내가 그동안 얼마나 최적화를 신경쓰지 않고 개발을 해왔는지 알 수 있던 좋은 경험이었다.