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

<center>[출처-WIKIMEDIACOMMONS](https://commons.wikimedia.org/wiki/File:Depth-First-Search.gif)</center>



#### DFS란?

---

>  `깊이 우선 탐색` 알고리즘이다.
>
> 위의 gif와 같이 방문하지 않은 노드가 있으면 계속 연결되어 있는 곳으로 깊어지며 탐색하는 알고리즘이다.
>
> 원리는 스택(stack)을 이용하여 동작을 한다. 이를 구현하는데 도움을 주는 것은 재귀함수이다.
>
> 
>
> ***< 예시 >***
>
> ```python
> #위의 gif의 노드들의 연결상태를 리스트로 표현.
> graph = [[],[2,5,9],[1,3],[2,4],[3],[1,6,8],[5,7],[6],[5],[1,10],[9]]
> visited = [False]*11 
> 
> def dfs(graph,v,visited):
>     visited[v]=True
>     print(v,end=' ')
>     
>     for i in graph[v]:
>         if not visited[i]:
>             dfs(graph,i,visited)
>             
> dfs(graph,1,visited)
> ```
>
> ***output***
>
> ```python
> 1 2 3 4 5 6 7 8 9 10
> ```
>
>  
>
> 다음과 같이 노드들이 아래쪽부터 탐색 되어짐을 확인할 수 있다.

---

#### 원리

1. dfs 함수는 제일 첫 노드를 읽어드리고 탐색을 한다. 그리고 자신과 인접한(순서상 제일 빠른) 노드를 방문처리한다.
2. 재귀함수를 이용하여 인접한 노드중 탐색이 되지 않은 곳은 끝없이 탐색을 하며 방문처리를 한다.
3. 노드 탐색은 정점에 도달하였을 때 제일 깊은 곳의 재귀함수가 빠져나온다.
4. 3과정을 반복하다 for순회 과정중 아직 탐색을 하지 않은 곳이 있다면 다시 재귀함수가 호출되어 탐색이 되어진다.

따라서 동작의 원리가 **`스택(stack)`**이다.  

---

#### 👍장점

+ 단지 현 경로상의 노드들만을 기억하면 되므로 저장공간의 수요가 비교적 적다.

+ 목표노드가 깊은 단계에 있을 경우 해를 빨리 구할 수 있다.

#### 👎단점  

+ 해가 없는 경로에 깊이 빠질 가능성이 있다.

---

---



### BFS(Breadth-Fist-Search)

![Breadth-First-Search-Algorithm]({{geunskoo.github.io}}/images/2022-02-12-data-structure/Breadth-First-Search-Algorithm.gif)

<center>[출처-WIKIMEDIACOMMONS](https://commons.wikimedia.org/wiki/File:Breadth-First-Search.gif)</center>

#### BFS란?

---

>  `너비 우선 탐색` 알고리즘이다.
>
> 위의 gif와 같이 가까운 노드들 부터 탐색하는 알고리즘이다.
>
> 원리는 __큐(Queue)__를 이용하여 동작을 한다. 이를 구현하는데 도움을 주는 것은 큐(Queue)이다.
>
> 
>
> ***< 예시 >***
>
> ```python
> from collections import deque
> 
> graph = [[],[2,3,4],[1,5],[1,6,7],[1,8],[2,9],[3,10],[3],[4],[5],[6]]
> visited = [False]*11 
> 
> def bfs(graph,start,visited):
>     queue = deque([start])
>     visited[start] = True
>     
>     while queue:
>         v = queue.popleft()
>         print(v, end=' ')
>         
>         for i in graph[v]:
>             if not visited[i]:
>                 queue.append(i)
>                 visited[i] = True
> 
> bfs(graph,1,visited)
> ```
>
> ***output***
>
> ```python
> 1 2 3 4 5 6 7 8 9 10
> ```
>
>  
>
> 다음과 같이 가까이 인접한 노드들부터 탐색 되어진다. 

---

#### 원리

1. bfs 함수는 제일 첫 노드를 방문처리한다. 
2. 첫 노드를 queue에서 꺼냄과 동시에 (방문하지 않은)인접한 노드를 queue에 삽입한다.
3. queue에서 노드를 하나씩 꺼내며 2.의 과정을 반복한다.

---

#### 👍장점

+ 너비를 우선으로 탐색하기 때문에 답이 되는 경로가 여러 개인 경우에도 최단 경로임을 보장할 수 있다. 
+ 노드 수가 적고 깊이가 얕은 해가 존재 할 때 유리하다.

#### 👎단점  

+ 큐를 이용해 다음에 탐색 할 노드들을 저장하기 때문에 노드의 수가 많을 수록 필요없는 노드들까지 저장해야 하기 때문에 더 큰 저장공간 필요하다.
+ 노드의 수가 늘어나면 탐색해야하는 노드가 많아지기 때문에 비효율적이다.

---

---



 **출처/참고**

이것이 코딩 테스트다 - 나동빈 저

https://velog.io/@vagabondms/DFS-vs-BFS

{: .notice--info} 

