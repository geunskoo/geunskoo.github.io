---
layout: single
title: "[코틀린] 컬랙션 자료형"
categories: 
    - kotlin
tag: ['kotlin']
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true
---
# 코틀린(Kotlin) 기초 문법

## Collection Data Type : List, Set, Map

### 1. List

#### **✍불변형 헬퍼 함수**

  > **listOf()**

  ```kotlin
  fun main(){
  	val list1 : List<Int> = listOf(1, 2, 3, 4)
      val list2 : List<String> = listOf("Hello", "Taegeun", "World")
      val list3 = listOf("My", "Age", 26)
      
      println(list1)
      println(list2)
      println(list3)
  }
  ```

  ```kotlin
  [1, 2, 3, 4]
  [Hello, Taegeun, World]
  [My, Age, 26]
  ```
  
<br/>
<br/>
  

#### **✍가변형 헬퍼 함수**

  > **mutableListOf()**

  ```kotlin
  fun main(){
      val list1 : MutableList<Int> = mutableListOf<Int>(1, 2, 3, 4)
      val list2 : MutableList<String> = mutableListOf<String>("Hi", "Nice", "To", "Meet", "You")
      val list3 = mutableListOf("My", "Age", 26)
      
      list3.add("Old")
      
      println(list1)
      println(list2)
      println(list3)
  }
  ```

  ```kotlin
  [1, 2, 3, 4]
  [Hi, Nice, To, Meet, You]
  [My, Age, 26, Old]
  ```



### 2. Set

