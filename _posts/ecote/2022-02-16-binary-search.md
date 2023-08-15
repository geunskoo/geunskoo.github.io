---
layout: single
title:  "[개념]기초 이진 탐색"
categories: 
    - 알고리즘
tag: [python,이진탐색,이분탐색,개념]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true
---

# 이진 탐색 기초.

## ✍탐색(search)

* 많은 양의 데이터 중에서 원하는 데이터를 찾는 과정이다.
* 그래프, 트리등 자료 구조안에서 탐색을 하는 문제를 자주 다룬다.
* 대표적인 `탐색 알고리즘(DFS/BFS)`이 있다.
* ***순차 탐색 & 이진 탐색*** 이 있다.

<br/>

**1️⃣순차탐색과 2️⃣이진 탐색에 대해서 알아보자.**

<br/>

## 1️⃣ 순차탐색(Sequential Search)란?



데이터가 모인 데이터 배열이 있으면 이 데이터 배열의 처음부터 끝까지 차례대로 비교하여 원하는 데이터를 찾아내는 알고리즘이다.

순차탐색은 단방향으로 탐색을 진행하기 때문에 **선형탐색(Linear Search)**라고도 한다.

간단히 구현이 가능하다는 장점이 있지만, 효율성이 좋지 않다는 단점이 있다.

<br/>

**예시**

```python
#리스트 값(양의 정수)중 가장 큰값을 찾아보자.

num = [1,2,3,4,5,6,7,8,9]

large=0
#값하나 하나를 비교하여 순차적으로 탐색을 한다.
for i in num:
    if large < i:
        large = i
        
print(large)
```

***>>output***

```python
9
```

순차 탐색의 최악의 경우 시간 복잡도는 **O(N)** 이다.

<br/>

## 2️⃣이진 탐색(Binary Search)란?

컴퓨터과학, 수학등에서 오름차순으로 정렬된 정수의 리스트를 같은 크기의 두 부분 리스트로 나누고 필요한 부분에서만 탐색하도록 제한하여 원하는 원소를 찾는 알고리즘이다. 

<br/>

> 이진탐색의 알고리즘을 간단히 그림으로 예시를 들어보았다.

![이진탐색-태근]({{geunskoo.hithub.io}}/images/2022-02-16-binary-search/이진탐색-태근.jpg)

이를 코드로 만들어 보자.

**예시**

```python
#이진탐색 알고리즘 만들기.

#찾고자는 값이 몇번째에 있는지 알려주는 이진탐색 함수.
def binary_search(arr,target,first,end):
    if first > end:
        return None
    mid = (first + end) // 2
    if arr[mid] == target:
        return mid+1
    
    if arr[mid] > target:
        return binary_search(arr,target,first,mid-1)
    else:
        return binary_search(arr,target,mid+1,end)

#이진탐색을 하기전 데이터들은 정렬되어 있어야한다.
arr = [1,2,3,4,5,6,7,8,9,10]

#target=3, 시작과 끝 인덱스를 대입.
binary_search(arr,3,0,9)
```

***>>output***

```python
3 #찾고자는 target=3 이 몇번째에 있는지 출력
```

순차 탐색의 최악의 경우 시간 복잡도는 **O($log_2 N$)** 이다.

<br/>

## ⭐ bisect 모듈

* ***bisect_left***(array, value) - 왼쪽 인덱스를 구하기.

* ***bisect_right***(array, value) - 오른쪽 인덱스를 구하기.

이 모듈의 함수를 활용해서 푼 문제  👉[[백준][python]10816번: 숫자 카드2](https://geunskoo.github.io/알고리즘/boj-10816/)

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

 **출처/참고**

이것이 코딩 테스트다 - 나동빈 저

감사합니다🙇‍♂️

{: .notice--info} 

