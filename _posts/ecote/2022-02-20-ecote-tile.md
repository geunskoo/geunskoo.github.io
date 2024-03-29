---
layout: single
title: "[이코테] 실전문제: 바닥 공사"
categories: 
    - 알고리즘 
tag: [python,다이나믹 프로그래밍]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true
---

# 바닥 공사

## 문제

가로의 길이가 N, 세로의 길이가 2인 직사각형 형태의 얇은 바닥이 있다.

태일이는 이 얇은 바닥을 1 X 2의 덮개, 2 X 1의 덮개, 2 X 2의 덮개를 이용해 채우고자 한다.

이 때 바닥을 채우는 모든 경우의 수를 구하는 프로그램을 작성하시오.

예를 들어 2 X 3 크기의 바닥을 채우는 경우의 수는 5가지이다.

<br/>

## 입력조건

* 첫째 줄에 N이 주어진다. (1 ≤ N ≤ 1,000)

<br/>

## 출력조건

- 첫째 줄에 2 X N 크기의 바닥을 채우는 방법의 수를 796,796으로 나눈 나머지를 출력한다.

<br/>

## 입력예시

```python
3
```

## 출력예시

```python
5
```

<br/>

## 나의 코드

```python
n = int(input())

way = [0]*1001
way[0] = 1
way[1] = 3
for i in range(2,n):
    way[i] = way[i-2]*2 + way[i-1]

print(way[n-1] % 796796)
```

***>>input***

```python
3
```

***>>output***

```python
5
```

## 🌝 Thinking

책의 흐름에 따라 문제가 나오다 보니 다이나믹 프로그래밍을 활용하여 푸는 문제임은 사실 머릿속에 전제되어 있었다.

그래서 점화식을 세운다고 생각하고 접근을 하다보니 인접한 항들에서 새로운 항을 만들어내는 방법론으로 접근을 하니

**답안 코드** 와 유사한 코드를 쉽게 세울 수 있었다.

## 답안 코드

```python
#정수 N을 입력받기
n = int(input())

#앞서 계산된 결과를 저장하기 위한 DP 테이블 초기화
d = [0]*1001

#다이나믹 프로그래밍(Dynamic Programming) 진행(보텀업)
d[1] = 1
d[2] = 3
for i in range(3,n+1):
    d[i]=(d[i-1]+2*d[i-2])%796796

#계산된 결과 출력
print(d[n])
```

## 🌝  Thinking

**답안 코드** 는 점화식에서 그 결과값을 796796으로 나눈 나머지를 바로 대입하는데,,,

**나의 코드** 는 최종 결과값에 796796을 나누어 주었다.

당연히 답안 코드가 맞겠지만,,, 왜 결과값을 나누어주어야 하는 것이 아닌가?

<br/>

## 💡 깨달은 점.

1. 다이나믹 프로그래밍의 **Bottom Up** 식의 접근은 사람의 사고와 확실히 많이 닮아 있는 듯 하다.


---
**출처**

이것이 코딩 테스트다 - 나동빈 저
{: .notice--info} 
