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

### 1️⃣ List

#### **◼ 불변형 헬퍼 함수  <span style = "color:red">(Read Only)</span>**

  > **listOf()**

  ```kotlin
  fun main(){
  	val list1 : List<Int> = listOf<Int>(1, 2, 3, 4)
      val list2 : List<String> = listOf<String>("Hello", "Taegeun", "World")
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


#### **◼ 가변형 헬퍼 함수 <span style = "color:red">(Read & Write)</span>**

  > **mutableListOf()**, **arrayListOf**()

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

---

<br/>
<br/>

<br/>
<br/>

<br/>
<br/>

<br/>
<br/>

### 2️⃣ Set

#### **◼ 불변형 헬퍼 함수  <span style = "color:red">(Read Only)</span>**

  > **setOf()**

  ```kotlin
fun main(){
	val set1 : Set<Int> = setOf<Int>(1, 2, 3, 4)
    val set2 : Set<String> = setOf<String>("Hello", "Taegeun", "World")
    val set3 = setOf("My", "Age", 26)
    
    println(set1)
    println(set2)
    println(set3)
}
  ```

  ```kotlin
[1, 2, 3, 4]
[Hello, Taegeun, World]
[My, Age, 26]
  ```

<br/>
<br/>


#### **◼ 가변형 헬퍼 함수 <span style = "color:red">(Read & Write)</span>**

  > **mutableSetOf()**

  ```kotlin
fun main(){
    val set1 : MutableSet<Int> = mutableSetOf<Int>(1, 2, 3, 4)
    val set2 : MutableSet<String> = mutableSetOf<String>("Hi", "Nice", "To", "Meet", "You")
    val set3 = mutableSetOf("My", "Age", 26)
    
    set3.add("Old")
    
    println(set1)
    println(set2)
    println(set3)
}
  ```

  ```kotlin
[1, 2, 3, 4]
[Hi, Nice, To, Meet, You]
[My, Age, 26, Old]
  ```

---

<br/>
<br/>

<br/>
<br/>

<br/>
<br/>

<br/>
<br/>

### 3️⃣ Map

#### **◼ 불변형 헬퍼 함수  <span style = "color:red">(Read Only)</span>**

  > **mapOf()**

  ```kotlin
fun main(){
	val map1 : Map<String, Int> = mapOf("태근" to 1, "철수" to 2, "짱구" to 3) 
    
    println(map1)
}
  ```

  ```kotlin
{태근=1, 철수=2, 짱구=3}
  ```

<br/>
<br/>


#### **◼ 가변형 헬퍼 함수 <span style = "color:red">(Read & Write)</span>**

  > **mutableSetOf()**

  ```kotlin
fun main(){
	val map1 : MutableMap<String, Int> = mutableMapOf("태근" to 1, "철수" to 2, "짱구" to 3)
    
    //add method2
    map1.put("유리",4)
    
    //add method2
    map1["훈이"] = 5
    
    println(map1)
}
  ```

  ```kotlin
{태근=1, 철수=2, 짱구=3, 유리=4, 훈이=5}
  ```

