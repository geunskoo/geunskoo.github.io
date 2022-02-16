---
layout: single
title: "[이코테] 실전문제: 떡볶이 떡 만들기"
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

# 떡볶이 떡 만들기

## 문제

오늘은 떡볶이 떡을 만드는 날이다. 떡볶이 떡의 길이가 일정하지 않지만 한 봉지 안에 들어가는 떡의 총 길이는 절단기로 잘라 맞춰준다.

절단기에 높이(H)를 지정하면 줄지어진 떡을 한 번에 절단한다. 

높이가 H보다 긴 떡은 H 위의 부분이 잘릴 것이고, 낮은 떡은 잘리지 않는다.

예를 들어 높이가 19, 14, 10, 17cm인 떡이 나란히 있고 절단기 높이를 15cm로 지정하면 자른 뒤 떡의 높이는 15, 14, 10, 15cm가 될 것이다.

잘린 떡의 길이는 차례대로 4, 0, 0, 2cm이다. 손님은 6cm만큼의 길이를 가져간다.

손님이 왔을 때 요청한 총 길이가 M일 때 적어도 M만큼의 떡을 얻기 위해 절단기에 설정할 수 있는 높이의 최댓값을 구하는 프로그램을 작성하시오.

## 입력조건

1. 첫째 줄에 떡의 개수 N과 요청한 떡의 길이 M이 주어집니다. (1 <= N <= 1,000,000, 1 <= M <= 2,000,000,000)

2. 둘째 줄에는 떡의 개별 높이가 주어집니다. 떡 높이의 총합은 항상 M 이상이므로, 손님은 필요한 양만큼 떡을 사갈 수 있습니다. 

   높이는 10억보다 작거나 같은 양의 정수 또는 0 입니다.

## 출력조건

- 적어도 M만큼의 떡을 집에 가져가기 위해 절단기에 설정할 수 있는 높이의 최댓값을 출력한다.

## 입력예시

```python
4 6
19 15 10 17
```

## 출력예시

```python
15
```



## 나의 코드

```python
n,m = map(int,input().split())
dduk = list(map(int,input().split()))

vinyl = []
for cut_cm in range(1,max(dduk)):
    for dduk_cm in dduk:
        if dduk_cm - (max(dduk)- cut_cm) > 0:
            vinyl.append(dduk_cm - (max(dduk)- cut_cm))
    if sum(vinyl)==m:
        print(max(dduk)- cut_cm)
        break
    else:
        vinyl=[]
```

***>>input***

```python
4 6
19 15 10 17
```

***>>output***

```
15
```

### 🌝 Thinking

떡의 길이중의 제일 길이간 긴 것을 기준으로 커팅 범위를 키워주며 탐색을 하였다. (순차 탐색)

문제의 조건을 보면 알겠지만 떡의 길이가 무려 2억cm가 될 수도 있다....🤦‍♂️

따라서 순차탐색으로 커팅길이를 구하면 최악은 경우엔 떡의 갯수 100만 x 2억.. 번의 연산이 발생할수도 있다. (순차탐색 **O(N)**)

따라서 위의 코드는 150% 시간 초과가 날 것이다.

탐색의 속도를 확연히 올려줄 이진탐색을 이용해야한다. N=2억 이지만 이진탐색 O($log_2 N$)을 이용하면 약 31번의 연산으로

목표값을 찾을 수 있다. 총 연산횟수 100만 * 31 = 3000만 정도!

---

## 나의 코드2

```python
n,m = map(int,input().split())
dduk = list(map(int,input().split()))

start = 0
end = max(dduk)

while True:
    cutting = (start + end) // 2
    sum=0
    for i in dduk:
        if i-cutting > 0:
            sum+= i-cutting
    if sum == m:
        print(cutting)
        break
    if sum > m:
        start = cutting + 1
    else:
        end = cutting - 1 
```

***>>input***

```python
4 6
19 15 10 17
```

***>>output***

```
15
```

### 🌝 Thinking

자르는 기준으로 이진 탐색이 가능했다. 

기준이 너무 작으면 많이 잘라서 양이 늘어나고, 너무 적게 자르면 양이 줄어드는 것을 원리로 이분탐색을 해주었다.



<br/>

## 답안 코드

```python
n, m = list(map(int, input().split()))

arr = list(map(int, input().split()))

start = 0
end = max(array)

#이진탐색을 수행
result = 0
while(start <= end) :
  total = 0
  mid = (start+end) // 2
  for x in arr :
    if x > mid :
      total += x - mid
  
  if total < m :
    end = mid - 1
  else :
    result = mid        #total 얻은 떡의 양이 요구한바 보다 같거나 클때의 mid값을 계속 갱신해서 result에 저장
    start = mid + 1

print(result)
```

***>>input***

```python
4 6
19 15 10 17
```

***>>output***

```
15
```



### 🌝 Thinking

**답안 코드**와 **나의 코드** 비교해보니,

나의 코드는 start가 end를 뛰어 넘을 때 break를 안 걸어 두어 만들 수 없는 떡의 길이가 있을 땐  error 나올 것 같다.

+다시 살펴보니 완전히 틀린 코드이다. 떡을 적어도 m이상 가져가고,  최대 높이를 구해야 하기 때문이다.

따라서 아래의 답안 코드 처럼 작성이 되어야 한다.

<br/>

위 문제와 같은 문제 👉 [[백준][python] 2164번: 카드2](https://www.acmicpc.net/problem/2805)



## 💡 깨달은 점.

1.  문제에 주어진 변수의 범위를 확인하면 어떤 효율을 가진 알고리즘을 채택해야 할지 힌트를 얻을 수 있는 것 같다.


---
<br/>

<br/>

<br/>

**출처**

이것이 코딩 테스트다 - 나동빈 저
{: .notice--info} 
