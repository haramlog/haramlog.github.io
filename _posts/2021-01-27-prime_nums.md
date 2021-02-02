---
layout: post
title: 백준 1978 / 소수 찾기
tags: [algorithm, BOJ]
color: rgb(132, 205, 186)
---

## 소수의 개념
2, 3, 5, 7, 11, 13 ...약수가 1과 자기 자신밖에 없는 수를 소수, Prime number라고 한다. 그렇다면 소수를 구하는 방법은 간단하다. 시간복잡도가 별로이긴 하지만, **제시된 수보다 작은 수를 몽땅 나눠보는 것이다.** 제시된 수가 5라면 나눠지는 수가 없을 것이고 제시되는 수가 6이라면 2와 3에서 나눠질 것이다. 이 말을 정리하면, **n을 1을 제외한 n보다 작은 수들로 나누었을때 하나라도 int형이 나오는지 알아보는 것이다.**

 * `if values is int:` : values가 정수일 때 실행하기

## 에라토스테네스의 체
 ```
1. 2부터 N까지 모든 정수를 적는다.
2. 아직 지우지 않은 수 중 가장 작은 수를 찾는다. 이것을 P라고 하고, 이 수는 소수이다.
3. P를 지우고, 아직 지우지 않은 P의 배수를 크기 순서대로 지운다.
4. 아직 모든 수를 지우지 않았다면, 다시 2번 단계로 간다.
```
N을 입력받은 뒤 이 과정을 거치면 소수를 구할 수 있다.

## 백준 1978
```Python
import sys

N = int(sys.stdin.readline())
Ns = list(map(int, sys.stdin.readline().split()))
Ns.sort()
prime = []

try:
    Ns.remove(1)
    Ns.remove(N)
except ValueError:
    pass

while True:
    delete_Num = Ns[0]
    check = Ns[0]

    prime.append(check)

    for i in range(len(Ns)):
        try:
            Ns.remove(delete_Num)
        except ValueError:
            pass

        delete_Num += check

        if delete_Num >= N:
            break
            # 완성

    if len(Ns) == 0:
        break

print(len(prime))
```
에라토스테네스의 체를 이용해 주어진 수 중 소수의 개수를 출력하는 코드다.

```python
try:
    Ns.remove(1)
    Ns.remove(N)
except ValueError:
    pass
```
일단 시작 전 1과 N을 리스트에서 제거해주고, 만약 그 수가 리스트에 포함되어 있지 않다면 ValueError를 일으킬테니 그런 경우는 그냥 pass하도록 만든다. **그런데 시간복잡도가... 시간이 말도 안되게 많이 나와서 통과는 되지 않는다.** 반례를 포함한 모든 값이 통과되니 일단은 반쯤 푼 셈 치자.

나중에 시간 안에 풀게 되면 다시 수정하겠다.









 

