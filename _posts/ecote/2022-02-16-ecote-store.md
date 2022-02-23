---
layout: single
title: "[이코테] 실전문제: 부품 찾기"
categories: 
    - binary search
tag: [python,이진탐색,이분탐색]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true 
---

# 부품 찾기

## 문제

동빈이네 전자 매장에는 부품이 N개 있다. 각 부품은 정수 형태의 고유한 번호가 있다. 

어느 날 손님이 M개의 종류의 부품을 대량으로 구매하겠다며 당일 날 견적서를 요청했다. 

동빈이는 때를 놓치지 않고 손님이 문의한 부품 M개 종류를 모두 확인해서 견적서를 작성해야 한다. 

이때 가게 안에 부품이 모두 있는지 확인하는 프로그램을 작성해보자.

예를 들어 가게의 부품이 총 5개일 때 부품 번호가 다음과 같다고 하자.

```python
N = 5
[8, 3, 7, 9, 2]
```

손님은 총 3개의 부품이 있는지 확인 요청했는데 부품 번호는 다음과 같다.

```python
M=3
[5, 7, 9]
```

이때 손님이 요청한 부품 번호의 순서대로 부품을 확인해 부품이 있으면 yes를, 없으면 no를 출력한다. 

구분은 공백으로 한다.

## 입력조건

* 첫째 줄에 정수 N이 주어진다. (1<=N<=1,000,000)
* 둘째 줄에는 공백으로 구분하여 N개의 정수가 주어진다. 이때 정수는 1보다 크고 1,000,000 이하이다.
* 셋째 줄에는 정수 M이 주어진다. (1<=M<=100,000)
* 넷째 줄에는 공백으로 구분하여 M개의 정수가 주어진다. 이때 정수는 1보다 크고 1,000,000 이하이다.



## 출력조건

- 첫째 줄에 공백으로 구분하여 각 부품이 존재하면 yes를, 없으면 no를 출력한다.

## 입력예시

```python
5
8 3 7 9 2
3
5 7 9
```

## 출력예시

```python
no yes yes
```



## 나의 코드

```python
#동빈이 가게 물품
n = int(input())
store = list(map(int,input().split()))
store.sort()

#손님 요청 물품
m = int(input())
client = list(map(int,input().split()))

#가게를 탐색하여 target(요청 물품)이 있는지 검사하는 함수.
def bi_search(arr,target,start,end):
    if start > end:
        return False
    mid = (start + end) // 2
    if arr[mid] == target:
        return True
    if arr[mid] > target:
        return bi_search(arr,target,start,mid-1)
    else:
        return bi_search(arr,target,mid+1,end)
    
#요구물품이 있는지 탐색
result=[]
for i in client:
    if bi_search(store,i,0,n-1):        #이 부분의 n-1 인데 m-1이라고 해서 애 먹음. 가게를 뒤져야하는데
        result.append('yes')			#손님 물품을 뒤지고 있었다...........
    else:
        result.append('no')
        
print(*result,sep = ' ')
```

***>>input***

```python
5
8 3 7 9 2
3
5 7 9
```

***>>output***

```
no yes yes
```

### 🌝 Thinking

꼼꼼하게 코드짜는 연습을 하자!

---

## 답안 예시

```python
# 이진 탐색 소스코드 구현 (반복문)
def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        # 찾은 경우 중간점 인덱스 반환
        if array[mid] == target:
            return mid
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        elif array[mid] > target:
            end = mid - 1
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 오른쪽 확인
        else:
            start = mid + 1
    return None

# N(가게의 부품 개수) 입력
n = int(input())
# 가게에 있는 전체 부품 번호를 공백을 기준으로 구분하여 입력
array = list(map(int, input().split()))
array.sort() # 이진 탐색을 수행하기 위해 사전에 정렬 수행
# M(손님이 확인 요청한 부품 개수) 입력
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백을 기준으로 구분하여 입력
x = list(map(int, input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    result = binary_search(array, i, 0, n - 1)
    if result != None:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```

### 🌝 Thinking

**답안코드**의 솔루션이 3개정도 보여준다.

하는 위의 이진탐색, 나머지는 계수정렬법과 집합 자료형을 이용한 풀이였다.



## 💡 깨달은 점.

1. 리스트에서 데이터를 탐색할 때는 정말 다양한 방법들이 존재한다. DFS/BFS, 이진 탐색, 계수정렬법을 이용한 탐색, 집합 자료형(순차적 탐색)을 활용한 탐색 등등등... 정말 많은 방법론이 존재한다. 상황에 맞게 적절한 알고리즘을 대입 할 수 있어야 겠다.


---
**출처**

이것이 코딩 테스트다 - 나동빈 저
{: .notice--info} 
