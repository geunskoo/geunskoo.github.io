---
layout: single
title: "[이코테] 실전문제: 왕실의 나이트"
categories: 
    - 알고리즘
tag: [python,구현,이동]
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
---

# 왕실의 나이트

## 문제

행복 왕국의 왕실 정원은 체스판과 같은 8 × 8 좌표 평면이다. 왕실 정원의 특정한 한 칸에 나이트가 서있다.

나이트는 매우 충성스러운 신하로서 매일 무술을 연마한다.

나이트는 말을 타고 있기 때문에 이동을 할 때는 L자 형태로만 이동할 수 있으며 정원 밖으로는 나갈 수 없다.

나이트는 특정 위치에서 다음과 같은 2가지 경우로 이동할 수 있다.

1. 수평으로 두 칸 이동한 뒤에 수직으로 한 칸 이동하기.
2. 수직으로 두 칸 이동한 뒤에 수평으로 한 칸 이동하기.

![image-20220210204832228]({{geunskoo.github.io}}/images/2022-02-10-chess-travel/image-20220210204832228.png)

이 처럼 8  x  8 좌표 평면상에서 나이트의 위치가 주어졌을 때 나이트가 이동할 수 있는 경우의 수를 출력하는 프로그램을 작성하시오.

## 입력조건

* 첫째 줄에 8x8 좌표 평면상에서 현재 나이트가 위치한 곳의 좌표를 나타내는 두 문자로 구성된 문자열이 입력된다. 

  입력 문자는 a1 처럼 열과 행으로 이뤄진다.

## 출력조건

* 첫째 줄에 나이트가 이동할 수 있는 경우의 수를 출력하시오.



## 입력예시

```python
a1
```

## 출력예시

```python
2
```



## 나의 코드

> 첫 번째 시도.
>
> ```python
> location=input()
> 
> result=0
> chess_row=['a','b','c','d','e','f','g','h']
> move_types = [[1,2],[-1,2],[1,-2],[-1,-2]]
> #move_types가 총 8개 나오지만 4개만 나타낸 이유는 나머지 4개의 움직임은
> #위 움직임에서 순서만 바뀐것이기 때문이다. 
> 
> row = int(chess_row.index(location[0])+1)
> col = int(location[1])
> 
> #안쪽의 for 구문으로써 8개의 움직임 모두 다 계산이 되고 있다.
> for move in move_types:
>     for i in range(2): 
>         x = row+move[i]
>         y = col+move[1-i]
>         if x<1 or y<1 or x>8 or y>8:
>             continue
>         else:
>             result+=1
> 
> print(result)
> ```

### 🌝 Thinking

이 전 `[구현] (이코테) 연습문제: 상하좌우` 에서 움직임을 리스트에 담아서 구현 하는 것이 인상적이었다.

그래서 그때의 알고리즘과 비슷하게 구현을 해보았다.

---

## 답안 예시

```python
input_data = input()

row = int(input_data[1])
column = int(ord(input_data[0])) - int(ord('a')) + 1 
#ord()함수를 이용하여 아스키코드를 이용하여 아주 깔쌈하게 알파벳의 순서값을 계산...역시 대단하군

steps = [(-2,-1),(-1,-2),(1,-2),(2,-1),(2,1),(1,2),(-1,2),(-2,1)]

result = 0
for step in steps:
    next_row = row + step[0]
    next_column = column +step[1]
    
    if next_row >=1 and next_row <=8 and next_column >=1 and next_column<=8:
        result+=1
        
print(result)
```

### 🌝 Thinking

**나의 코드**는 답안코드와 알고리즘은 똑같아 보인다. 하지만 행값의 알파벳을 순서값으로 바꾸는데 반면,

**답안코드**는 아스키코드를 이용하여별도의 리스트의 사용없이 깔끔하게 나타내었다. 



***그래도 전체적인 흐름은 일치함으로 나름 잘 푼 풀이인듯하다😁😊***



## 💡 깨달은 점.

1. 알파벳의 순서값을 이용할때는 아스키코드 값을 이용하면 편안하게 구할 수 있다. 
1.  ord('a') = 97, ord('A') = 65 정도는 외우고 있자!


---
**출처**

이것이 코딩 테스트다 - 나동빈 저
{: .notice--info} 
