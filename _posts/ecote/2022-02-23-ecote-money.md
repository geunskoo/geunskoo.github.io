---
layout: single
title: "[이코테] 실전문제: 효율적인 화폐 구성"
categories: 
    - dynamic programming
tag: [python,다이나믹 프로그래밍]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true
---

# 효율적인 화폐 구성

## 문제

N가지 종류의 화폐가 있다. 

이 화폐들의 개수를 최소한으로 이용해서 그 가치의 합이 M원이 되도록 하려고 한다. 

이때 각 화폐는 몇 개라도 사용할 수 있으며, 사용한 화폐의 구성은 같지만 순서만 다른 것은 같은 경우로 구분한다. 

예를 들어 2원, 3원 단위의 화폐가 있을 때는 15원을 만들기 위해 3원을 5개 사용하는 것이 가장 최소한의 화폐 개수이다.
<br/>

## 입력조건

* 첫째 줄에 N,M이 주어진다(1<= N <= 100, 1<= M <= 10,000)
* 이후의 N개의 줄에는 각 화폐의 가치가 주어진다. 화폐의 가치는 10,000보다 작거나 같은 자연수이다.

<br/>

## 출력조건

* 첫째 줄에 경우의 수 X를 출력한다.
* 불가능할 때는 -1을 출력한다.

<br/>

## 입력예시

```python
2 15
2
3
```

## 출력예시

```python
5
```

<br/>

## 나의 코드

```python
n,m = map(int,input().split())
money = [int(input()) for i in range(n)]

d = [10001]*(m+1)

#화폐 종류
d[0]=0
for i in money:
    #고른 화폐부터 끝까지 인덱스
    for j in range(i,m+1):
        if d[j-i] != 10001: 
            d[j] = min(d[j],d[j-i]+1)

if d[m] == 10001:
    print(-1)
else:
    print(d[m])
```

***>>input***

```python
2 15
2
3
```

***>>output***

```python
5
```

## 🌝 Thinking

점화식이 $A_i$ = min($A_{i-money}+1, A_i $ ) 이라는 것은 쉽게 떠올릴 수 있었지만

 이것을 구현하기란 쉽지 않았다.

1. 점화식이 min으로 구성됨으로 DP 테이블을 초기화 할때 m+1인 10,001로 세팅한다.

2. 제일 큰루프에서 화폐단위를 순회시키며, $A_{i-money} 값이 존재한다면 해당 화폐만큼만 있으면

   $A_i$금액을 만들 수 있으므로 $A_{i-money}+1$ 값이 $A_i$ 금액을 만들기위한 화폐 개수 일것이다.

   금액별로 순회하면서 min함수를 이용하여 가장 최적의 값을 할당 시켜주면 된다.

**화폐종류가 여러개임으로 화폐별 가장 최적의 값을 업데이트 해주는 방식**

---

## 답안 코드

```python
n,m = map(int, input().split())
arr=[]
for i in range(n):
    arr.append(int(input()))

d = [10001]*(m+1)
d[0]=0

for i in range(n):
    for j in range(arr[i],m+1):
        if d[j-arr[i]] != 10001:
            d[j] = min(d[j], d[j-arr[i]]+1)

if d[m] == 10001:
    print(-1)
else:
    print(d[m])
```

## 🌝  Thinking

**답안 코드** 와 **나의 코드**의 큰 로직은 일치하는 것으로 보인다.

<br/>

## 💡 깨달은 점.

1. 이중 for  구문을 이용하여 DP를 구현할 수 있다는 것을 알았다.


---
**출처**

이것이 코딩 테스트다 - 나동빈 저
{: .notice--info} 
