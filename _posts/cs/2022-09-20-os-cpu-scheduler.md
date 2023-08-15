---
layout: single
title: "[Operating System] 단기 스케줄러 CPU 스케줄링!"
categories: 
    - 운영체제
tag: ['운영체제','OS','CPU','CPU스케줄러']
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true
---

# 🚀 CPU 스케줄링

## 1️⃣  사용자 프로그램이 CPU를 어떻게 사용할까 ?

<span style="font-size:120%"><span style = "color:#2D3748;background-color:#dcffe4;">프로그램의 수행 단계</span></span>

<span style = "color:blue">**CPU 버스트(burst)**</span> : 사용자 프로그램이 CPU를 직접 가지고 빠른 명령을 수행하는 단계. 

명령예시 -   Add, Load, Store...

<span style = "color:blue">**I/O 버스트(burst)**</span> : 사용자 프로그램이 I/O요청이 발생해 커널에 의해서 입출력 작업을 수행하는 단계.

<br/>

<span style="font-size:120%"><span style = "color:#2D3748;background-color:#dcffe4;">프로그램 수행 단계에 따른 프로세스 분류</span></span>

<span style = "color:blue">**CPU 바운드 프로세스 (CPU Bound Process)**</span> : I/O를 거의 하지 않아 CPU버스트가 매우 길게 나타나는 프로세스.

<span style = "color:blue">**I/O바운드 프로세스 (I/O Bound Process)**</span> : I/O가 빈번하여 CPU버스트가 매우 짧게 나타나는 프로세스. 사용자로부터 인터랙션(interaction)을 계속 받아가며 프로그램을 수행하는 **대화형 프로그램(interactive program)**이다.

<br/>

CPU버스트가 짧은 프로세스들에게 CPU를 먼저할당하는 것이 바람직하다. CPU버스트가 짧은 프로세스들은 대체로 I/O 바운드 프로세스들이다. 따라서 CPU를 빠르게 할당시켜주고 I/O작업을 보내는 것이 자원 관리 차원에서도 효율적이다. (놀고있는 CPU도 없고 놀고있는 I/O장치도 없고 !! )

<br/>

**즉, CPU스케줄링할 때 I/O바운드 프로세스들의 우선순위를 올려주는 것이 바람직하다**.

<br/>

> CPU 스케줄링은 CPU를 사용하는 패턴이 상이한 여러 프로그램들이 시분할 시스템의 원리로 작동되기에 필요하다.

<br/>

<br/>

## 2️⃣  CPU 스케줄러



<br/>

<br/>

## 4️⃣  CPU 스케줄러 성능 평가



<br/>

<br/>

## 5️⃣ CPU 스케줄링 알고리즘



<br/>

<br/>

## 6️⃣ 



<br/>

<br/>

## 7️⃣ 





<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

---

**[ REF ]**

* [운영체제와 정보기술의 원리(이화여자대학교출판문화원) - 개정판 : 반효경 지음]()
* [장장스님의 블로그](https://zangzangs.tistory.com/108)
