## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12985
- **난이도** : Level 2
- **풀이 일자** : `2021/07/22`

## 2. 문제 접근

돌이켜보면 굉장히 무식하게 풀었다. 문제 풀면서도 분명 _'수학적으로 풀 수 있는 문제일텐데'_ 라는 생각이 계속 들었지만, 고질적인 나의 성실성 이슈로...

짝수별로 끊어서 좌, 우로 대상을 나누고 그 중 a 혹은 b 에 속하지 않으면 무조건 좌측을 승자로 올렸고 (어차피 상관없으니) a, b 에 속한다면 그것을 승자로 올리게되었다. 그렇게 모든 매치가 끝날 때 마다 배열의 길이가 절반이 되도록 반복하였다. 좌, 우의 대상이 a와 b 라면 반복을 탈출하고, 그 반복의 횟수를 반환하게 구현하였다.

수학적으로 접근하는 방법에 대해 궁금해서 인터넷 검색을 조금 해봤는데, 이렇게 쉽게 접근해서 풀 문제인줄 몰랐다. 그냥 단순히 현재 a 와 b 의 위치를 2로 나눈 몫이 같아질 때 까지 계속 나누면 되는 것이었다. 각 라운드를 0번부터 순서대로 숫자를 부여한 다음 a 와 b 가 같은 라운드인지 검사하면 되는 것 이었다.

## 3. 소스코드

### 3-1. 최초 풀이

```python
def solution(n,a,b):
    arr = list(range(1, n + 1))

    count = 0
    while len(arr) >= 2:
        count += 1

        survive = []
        for i in range(1, len(arr), 2):
            left = arr[i - 1]
            right = arr[i]

            if (left == a and right == b) or (left == b and right == a):
                return count

            if left != a and left != b and right != a and right != b:
                survive.append(left)
            else:
                if left == a or left == b:
                    survive.append(left)
                elif right == a or right == b:
                    survive.append(right)

        arr = survive

    return count
```

### 3-2. 두번째 풀이

```python
def solution(n,a,b):
    count = 0
    a = a - 1
    b = b - 1
    while a != b:
        a = a // 2
        b = b // 2
        count += 1

    return count
```

## 4. 배운점

수학적 센스가 많이 부족하다는 생각도 들고, 깊이있는 고민에 대한 노력이 많이 부족하다는 생각이 많이 드는 문제풀이었다. 분명 더 좋은 방법이 있을것이고, 출제의도도 내 풀이와 맞지 않다는 걸 알았으면서 비효율적인 방법으로 메모리를 낭비해가며 문제를 풀었다. 부끄럽고, 반성할 점이다.
