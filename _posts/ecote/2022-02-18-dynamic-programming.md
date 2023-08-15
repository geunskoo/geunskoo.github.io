---
layout: single
title:  "[개념]기초 다이나믹 프로그래밍"
categories: 
    - 알고리즘
tag: [python,다이나믹 프로그래밍,개념]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true
---

# 다이나믹 프로그래밍(Dynamic Programming) 기초.



## 📚 다이나믹 프로그래밍

<br/>

## 다이나믹 프로그래밍이란 ?

**큰 문제를 작은 문제로 나누어 해결하는 것이다.**

계산 했던 것은 계산하지 않겠다!!

<br/>

> 예) 사람은 피보나치 수열을 계산할 때 5번째 항을 구하기 위해
>
> 1 1 2 3 5 를 뚝딱 금방 생각 할 수 있다.. 물론 숫자가 작을때
>
> 우리는 효율적으로 5번째 항을 구하기 위해 3번과 4번 항만을 더하여 계산한다
>
> 하지만 컴퓨터는 5번째항을 구하기위해 3번과 4번항을 구하고, 3번을 구하기위해 1번과 2번항을
>
> 4번항을 위해 3번항과 2번항을, 4번항의 3번항을 구하기위해 2번항과 1번항을 4번항의 2번항.......

논리의 흐름에 맞춰 이미 했던 계산임에도 불구하고 반복해서 계산을 한다.

<br/>

<center>[피보나치 수열을 계산 과정]</center>

![피보나치]({{geunskoo.github.io}}/images/2022-02-18-dynamic-programming/피보나치.jpg)



컴퓨터에 재귀적으로 피보나치 코드를 짠다면 다음과 같은 그래프의 모양으로 연산이 이루어질 것이다.

하지만 **사람은 자연스럽게 우리가 이미 한 연산을 반복하지 않는다.**

**다이나믹 프로그래밍 프로그램이 빨간색선의 과정을 구현하는 것이라고 생각한다.**

<br/>

###  📌 다이나믹 프로그래밍 사용 조건

<br/>

1. 큰 문제를 작은 문제로 나눌 수 있다.

2. 작은 문제가 반복하여 일어나야한다.

3. 작은 문제의 답이 항상 동일하게 나와야한다.

<br/>

### 📌 다이나믹 프로그래밍 구현방식?

<br/>

1. **Top-Down방식** 큰 문제를 해결하기위해 작은 문제들을 호출하는 방식이다.

   위에서 아래로 연산해 나아가는 방식이다.(메모이제이션기법이 사용됌.)

2. **Bottom-Up방식** 우리가 머릿속으로 피보나치 수열을 계산하기 자연스럽게 첫항에서 부터 계산해 

   나아간다. 이와 같이 아래에서 위로 연산해 나아가는 방식이다.

<br/>

<br/>

## 메모이제이션 (memoization)

### 메모이제이션 이란?

동적 프로그래밍에서 작은 문제들이 반복이되고 이에 대한 결과값이 동일할 때,

그 값을 저장해놓는 기법을 의미한다. (**Top - Down 방식**에 사용)

<br/>

<br/>

## 예시(피보나치수열)

### 1. 재귀함수를 활용한 피보나치수열 구현

```python
def fibo(n):
    if n==1 or n==2:
        return 1
    else:
        return fibo(n-1)+fibo(n-2)
fibo(5)
```

***>>output***

```python
8
```

시간 복잡도(일반적으로): **O($2^N$)**

엄청난 속도로 복잡도가 상승하게 될것이다.

***

<br/>

### 2. Top-Down 방식의 피보나치수열 구현

```python
memo = [0]*10 #메모이제이션을 위해 DP테이블을 만듬.

def fibo(n):
    if n==1 or n==2:
        return 1
    
    if memo[n]!=0:     #메모이제이션값에 기록이 되어 있다면 ? 그냥 바로 그걸 꺼내줌.
        return memo[n]
    
    memo[n] = fibo(n-1) + fibo(n-2)
    return memo[n]
fibo(5)
```

***>>output***

```python
8
```

시간 복잡도: **O(N)**

#### 원리

1. 피보나치가 수열의 형태임으로 각각의 값을 저장할 수 있는 list를 만든다.(메모이제이션을 위한 DP테이블 생성)
2. 모든 결과값을 DP테이블에 저장을 한다.
3. 만약 DP테이블 원하는 결과값이 있으면 재귀함수를 호출하는 것이 아닌 DP에 저장된 값을 return 해준다.

***

<br/>

### 3. Bottom-Up 방식의 피보나치수열 구현

```python
d = [0]*10

d[1] = 1
d[2] = 2

n=5

for i in range(3,n+1):
    d[i] = d[i-1]+d[i-2]
    
print(d[i])
```

***>>output***

```python
8
```

시간 복잡도: **O(N)**

#### 원리

1. 점화식의 초기값을 DP테이블에 할당시켜놓는다.
2. 점화식을 만들고 반복구문으로 실행시켜준다.

***

<br/>



---

---

### 🔥동적 프로그래밍 연습문제

>  DP식을 세우는 고민을 하게 해 줄 문제들 모음

1. [[백준] 11722번: 가장 ~~ 수열](https://www.acmicpc.net/problem/11722) 
2.  [[백준] 15486번: 퇴사 2  ](https://www.acmicpc.net/problem/15486)
3. [[백준] 1520번: 내리막길](https://www.acmicpc.net/problem/1520)
4. [[백준] 11066번: 파일 합치기](https://www.acmicpc.net/problem/11066)
5. [[백준] 11049번: 행렬 곱셈 순서](https://www.acmicpc.net/problem/11049)
6. [[백준] 9252번: LCS 2 ](https://www.acmicpc.net/problem/9252)           

>  DP에 대해서 어느정도 익숙해진 사람들을 위한 많은 사람들이 푼 검증된 좋은 문제들 모음

1. [[백준] 1562번: 계단수](https://www.acmicpc.net/problem/1562)
2. [[백준] 11570번: 환상의 듀엣](https://www.acmicpc.net/problem/11570)
3. [[백준] 2618번: 경찰차](https://www.acmicpc.net/problem/2618)
4. [[백준] 6989번: 채점](https://www.acmicpc.net/problem/6989)
5. [[백준] 2315번: 가로등 끄기](https://www.acmicpc.net/problem/2315)
6. [[백준] 1126번: 같은 탑](https://www.acmicpc.net/problem/1126)
7. [[백준] 1315번: RPG ](https://www.acmicpc.net/problem/1315)
8. [[백준] 2419번: 사수아탕 ](https://www.acmicpc.net/problem/2419)
9. [[백준] 12766번: 지사배정](https://www.acmicpc.net/problem/12766)
10. [[백준] 5466번: 상인](https://www.acmicpc.net/problem/5466)

>  수학적인 활용도가 높은 DP문제들

1. [[백준] 2749번: 피보나치수 3](https://www.acmicpc.net/problem/2749)
2. [[백준] 14578번: 영훈이의 색칠공부](https://www.acmicpc.net/problem/14578)
3. [[백준] 15588번: stamp painting ](https://www.acmicpc.net/problem/15588)
4. [[백준] 2392번: 다각형의 분할](https://www.acmicpc.net/problem/2392)
5. [[백준] 2862번: 수학 게임 ](https://www.acmicpc.net/problem/2862)
6. [[백준] 15902번: split and merge](https://www.acmicpc.net/problem/15902) 



`돌이 코딩하는 방`님의 추천목록을 참고하여 만들었습니다.(출처 아래)

 **출처/참고**

이것이 코딩 테스트다 - 나동빈 저

[돌이 코딩하는 방](https://stonejjun.tistory.com/24)

감사합니다🙇‍♂️

{: .notice--info} 

