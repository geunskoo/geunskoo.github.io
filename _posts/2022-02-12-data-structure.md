---
layout: single
title:  "[이코테] 자료구조"
categories: 
    - DFS/BFS
tag: [python,자료구조,개념]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
---

# 자료구조 기초.

## ✍탐색(search)

>* 많은 양의 데이터 중에서 원하는 데이터를 찾는 과정이다.
>
>* 그래프, 트리등 자료 구조안에서 탐색을 하는 문제를 자주 다룬다.
>
>* 대표적인 `탐색 알고리즘(DFS/BFS)`이 있다.



**탐색 알고리즘(DFS/BFS)를 알아보기전 기초 자료구조에 대해서 알아보자.**



### 📚 자료구조란 ?

> ***데이터를 표현하고 관리하고 처리하기 위한 구조*** 이다.
>
> 그 중 스택 & 큐는 자료구조의 기초 개념이다. 삽입(push)와 삭제( pop)라는 함수로 구성이 되어지고,
>
>  그 외 오버플로우(overflow), 언더플로우(underflow)에 대해서도 고민을 해야한다.



#### 스택(stack)

> 박스를 쌓고 빼는 법과 원리가 유사하다.
>
> 선입후출(Fist In Last Out) / 후입선출(Last In First Out)
>
> ```python
> stack = []
> 
> #삽입(5) - 삽입(2) - 삽입(3) - 삽입(7) - 삭제 - 삽입(1) - 삽입(4) - 삭제()
> stack.append(5)
> stack.append(2)
> stack.append(3)
> stack.append(7)
> stack.pop()
> stack.append(1)
> stack.append(4)
> stack.pop()
> 
> print(stack)
> print(stack[::-1])
> ```
>
> ***output***
>
> ```python
> [5, 2, 3, 1]
> [1, 3, 2, 5]
> ```



⭐ 파이썬에서 스택(stack)을 구현할 때 별도의 라이브러리를 사용할 필요가 없다.

기본 리스트의 함수 append와 pop이 스택 자료구조와 동일하게 동작하기 때문이다.



#### 큐(queue)

> 대기줄의 원리가 유사.
>
> 선입선출(First In First Out)
>
> ```python
> from collection import deque
> 
> #큐(Queue) 구현을 위해 deque 라이브러리 사용
> queue = deque()
> 
> #삽입(5) - 삽입(2) - 삽입(3) - 삽입(7) - 삭제() - 삽입(1) - 삽입(4) - 삭제()
> queue.append(5)
> queue.append(2)
> queue.append(3)
> queue.append(7)
> queue.popleft()
> queue.append(1)
> queue.append(4)
> queue.popleft()
> 
> print(queue)
> queue.reverse()
> print(queue)
> ```
>
> ***output***
>
> ```python
> deque([3, 7, 1, 4])
> deque([4, 1, 3, 7])
> ```



⭐ 파이썬에 큐(queue)를 구현할 때 collection 모듈에서 제공하는 deque 자료구조를 활용하면 좋다.

deque는 스택과 큐의 장점을 모두 채택한 것, 

데이터를 넣고 빼는 속도가 리스트 자료형에 비해 효율적이고, queue 라이브러리를 이용하는 것보다 더 간단하다.



#### 재귀함수(recursive function)

재귀함수는 스택 자료구조를 이용하여 데이터를 처리한다.



>  나무위키를 보다 갑자기 생각 난 비유,
>
> 꿈에서 꾸는 꿈에서 꾸는 꿈에서 꾸는 꿈에서 꾸는 꿈에서 꾸는 꿈.....을 깨어나려면
>
> 가장 depth가 깊은 꿈에서 부터 차례로 깨어나야 한다 ! ! 재귀함수 원리라 비슷한 듯? ㅎㅎ



## DFS/BFS

### DFS(Depth-Fist-Search)
![Depth-First-Search]({{geunskoo.github.io}}/images/2022-02-12-data-structure/Depth-First-Search.gif)

깊이 우선 탐색 알고리즘


 **출처**

이것이 코딩 테스트다 - 나동빈 저
{: .notice--info} 
