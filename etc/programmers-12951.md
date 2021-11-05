## 1. 문제 개요

- **문제 링크** : https://programmers.co.kr/learn/courses/30/lessons/12951
- **난이도** : Level 2
- **풀이 일자** : `2021/11/06`

## 2. 문제 접근

문자열을 `" "` 로 split 한 다음, 소문자로 만든 후, 맨 앞 글자가 알파벳이면 대문자로 만들면 된다.

예외가 있다면, 스페이스바가 하나만 온다는 것이 아니라는 것 이다. 테스트 케이스가 `I am hudi` 일수도 있지만, `I am hudi` 일 수도 있다는 점.

## 3. 소스코드

```python
def solution(s):
    new_s = []
    for word in s.split(" "):
        new_word = word.lower()

        # 연속 공백 처리
        if len(new_word) == 0:
            new_s.append("")
            continue

        # 앞글자 대문자 처리
        if new_word[0].isalpha():
            new_word = new_word[0].upper() + new_word[1:]

        new_s.append(new_word)

    return " ".join(new_s)
```
