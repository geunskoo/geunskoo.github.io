---
layout: single
title: "[코틀린] 자료형"
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

## 자료형

### 1. `숫자` `문자` `불리언` 자료형 선언하는 법

>1. Var 변수 명 : 자료형 = 값
>2. Val 변수 명 : 자료형 = 값

```kotlin
// 정수 자료형
var int1 : Byte = 1			// 1 byte
var int2 : Short = 1		// 2 bytes
var int3 : Int = 1			// 4 bytes
var int4 : Long = 1			// 8 bytes

// 실수 자료형
var float1 : Float = 1.0	// 4 Bytes
var float2 : Double = 1.0	// 8 Bytes

// 문자 자료형
var char1 : Char = 'a'		// 2 Bytes		

// 문자열 자료형
var str1 : String = "Hello Taegeun World!!"

// Boolean 자료형
var word : Boolean = true

//-------------------------------------------

//추론 가능한 경우 명시하지 않아도 가능함.
var num1 = 1				// int로 추론
var num2 = 1L				// Long로 추론 (명시적으로 'L')

var num2 = 1.0 				// double로 추론 (defalut)
var num3 = 1f				// float로 추론 (명시적으로 'f' or 'F')
var num4 = 1.0f				// float로 추론		"

var str5 = 'A'				// Char로 추론
var str6 = "A"				// String로 추론 

var word1 = true			// Boolean로 추론
//자료형이 알고싶다면 ?!
println(num1 :: class.java.simpleName)
println(str6 :: class.java.simpleName)
```

```kotlin
Int
String
```

---

<br/>

### 2. Var와 Val

* **Var**  :  

  - Read & Write Property.

  - mutable(가변성)

    

* **Val**  :  

  - Read Only Property.

  - immutable(불가변성)

  - 완전히 변경 불가인 것은 아님. _Val이 mutable 객체를 담고 있으면 내부적으로 변경가능._

    

**🚀Experiment 1** : Val 에 다른 값을 할당 시 __컴파일 에러__

```kotlin
Val a : Int = 1
a = 2

//Complie Error
```
<br/>

**🚀Experiment 1** : Val mutable 객체를 할당시키면 내부적으론 변경이 가능하다 !!!

```kotlin
var str1 : String = "Kim"
var str2 : String = "Chi"
val propVal
	get() = "$str1 $str2"

fun main(){
    println(propVal)
    str2 = "Taegeun"
    println(propVal)
}

//Complie Success
```

```kotlin
Kim Chi
Kim Taegeun
```

---

<br/>

### 3. Nullable 

코틀린은 **Nullabale 타입**과 **Non-Null 타입**이 있다.

default는 Non-Null이다.

**" ? "** 를 붙여 null을 할당 할 수 있는 변수를 만들 수 있다.

```kotlin
var str1 : String = null	// Complie Error
var str2 : String? = null	// Complie Success
```



❓. 널 안정성에 대해서 조금 더 공부한 후 정리 해야겠다.

---

