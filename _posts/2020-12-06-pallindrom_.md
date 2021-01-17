---
layout: post
title: 팰린드롬 문자열
tags: [팰린드롬, algorithm]
color: rgb(132, 205, 186)
---

## 1. 팰린드롬 - 정의
팰린드롬이란 앞뒤가 똑같은 단어나 문장을 의미한다. 우리 말로는 회문이라고 부르며, '소주 만 병만 주소' 나 'level' 같은 경우가 해당된다. 이 문장은 뒤집어도 '소주 만 병만 주소' 와 'level' 이다.

밑 문단들은 임의의 입력이 주어졌을 때 그 입력이 팰린드롬인지 아닌지 구분하여 False 또는 True로 리턴하는 `solution` 함수이다.

## 2. 팰린드롬 - list로 풀기
```
def solution():
    ins = input()
    str_list = []

    for repeat in range(0, len(ins)):
        if ins[repeat].isalnum():
            str_list.append(ins[repeat].lower())

    while len(str_list) > 1:
        if str_list.pop(0) != str_list.pop():
            return False

    return True
```

* `a.isalnum()` : a가 알파벳(al), 영어(num)가 아니라면

입력을 받은 만큼 반복문을 실행한다. 숫자와 영어가 아닌 입력값은 `append` 해주지 않는다. 추가할 때는 모두 소문자로 바꿔서 추가한다. `str_list`가 1보다 크면 리스트의 시작부분, 리스트의 끝부분부터 차례차례 `pop`을 해줘서 양쪽의 값이 같으면 `True`를 리턴하고, 하나라도 다른 결과가 나오면 `False`를 리턴한다.

## 3. 팰린드롬 - Deque로 풀기
```
import collections

def solution():
    deque = collections.deque()

    for char in input():
        if char.isalnum():
            deque.append(char.lower())

    while len(deque) > 1:
        if deque.popleft() != deque.pop():
            return False

    return True
```

* `deque = collections.deque()` : deque 선언
* `a.pop()` : a를 pop함
* `deque.popleft()` : 반대쪽에서 pop 해주기

리스트로 변환하는 것보다 약 5배 빠르게 실행 할 수 있다. list의 경우는 `pop`을 하는데만 `O(n)`인데 비해 deque의 경우는 `O(1)` 안에 실행이 가능하기 때문이다. 특히 수가 커질수록 속도에서는 두각을 나타내는데 구현은 리스트는 `O(n^2)`, 데크는 `O(n)`이다.

## 4. 팰린드롬 - slicing으로 풀기
추가하기

## 5. 가장 긴 팰린드롬 문자열 구하기
추가하기