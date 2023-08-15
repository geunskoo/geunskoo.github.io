---
layout: single
title: "[이코테] 실전문제: 숫자 카드 게임"
categories: 
    - 알고리즘
tag: [python,greedy]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
---

# 숫자 카드 게임

## 문제
여러 개의 숫자 카드 중에서 가장 높은 숫자가 쓰인 카드 한 장을 뽑는 게임이다.

1. 숫자가 쓰인 카드들이 N x M 형태로 놓여 있다. 이때 N은 행의 개수를 의미하며, M은 열의 개수를 의미한다.
2. 먼저 뽑고자 하는 카드가 포함되어 있는 행을 선택한다.
3. 그 다음 선택된 행에 포함된 카드들 중 가장 숫자가 낮은 카드를 뽑아야 한다.
4. 따라서 처음에 카드를 골라낼 행을 선택할 때, 이후에 해당 행에서 가장 숫자가 낮은 카드를 뽑을 것을 고려하여 최종적으로 가장 높은 숫자의 카드를 뽑을 수 있도록 전략을 세워야 한다.



## 입력조건

* 첫째 줄에 숫자 카드들이 놓인 행의 개수 N과 열의 개수 M이 공백을 기준으로 하여 각각 자연수로 주어진다. (1 ≤ N, M ≤ 100)
* 둘째 줄부터 N개의 줄에 걸쳐 각 카드에 적힌 숫자가 주어진다. 각 숫자는 1 이상 10,000 이하의 자연수이다.



## 출력조건

* 첫째 줄에 게임의 룰에 맞게 선택한 카드에 적힌 숫자를 출력한다.



## 입력예시

```python
2 4
7 3 1 8
3 3 3 4
```

## 출력예시

```python
3
```



## 나의 코드

> 첫 번째 시도.
>
> ```python
> n,m = map(int,input().split())
> 
> card=[]
> for i in range(n):
>     row=list(map(int,input().split()))
>     pick_card = min(row)
>     
>     card.append(pick_card)
> 
> print(max(card))
> ```

### 🌝 Thinking

생각의 흐름...

for을 이용하여 행을 리스트로 input함.

행에서 제일 작은 값만 추출하여 새로운 `card`리스트에 넣음.

`card`리스트에서 제일 큰 값을 출력함.

---

## 답안 예시1

```python
n,m = map(int,input())

result = 0
for i in range(n):
    data=list(map(int,input().split()))
    
    min_value = min(data)
    
    result=max(min_value,result)
print(result)
```

### 🌝 Thinking

내가 생각했던 것과 큰 틀은 일치하는 듯 함.

**나의 코드**는 각 행들에서의 최소값들을 새로운 리스트에 추가를 시켜주었고, 마지막에 그 리스트에서 제일 큰 값을 구하는 원리이다.

**답안코드**는 for 구문의 순회마다 작은 값들을 추출 후 비교하여 가장 큰 값을 변수 result에 할당하는 방식을 이용하였다.



***과연 어떤 방식이 더 빠를 까?***



## 답안예시2

```python
n,m = map(int,input())

result = 0
for i in range(n):
    data=list(map(int,input().split()))
    
    min_value = 10001
    for a in data:
        min_value=min(min_value,a)
    
    result = max(result,min_value)
    
print(result)
```



## 💡 깨달은 점.

1.  파이썬의 리스트를 다루기에 정말 용이한 것 같다.

2.  for 구문에서 순회마다 특정 값들을 비교하여 최댓값, 최소값을 찾을 수 있다.


---
**출처**

이것이 코딩 테스트다 - 나동빈 저
{: .notice--info} 
