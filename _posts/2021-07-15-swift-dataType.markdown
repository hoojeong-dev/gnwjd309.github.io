---
title: "[Swift] 1. 스위프트 기초 : 데이터 타입 1"
layout: post
date: 2021-07-15 16:06
image: 
headerImage: false
tag:
- swift
- study
category: blog
author: Hoojeong Kim
description: 
---
<br/>

* swift에 대해 공부한 내용을 정리한 글입니다.
* 해당 글은 <a href="https://www.hanbit.co.kr/store/books/look.php?p_code=B9421379018" target="_blank">한빛미디어의 스위프트 프로그래밍 3판</a>을 참고하여 작성했습니다.

---

# 데이터 타입 기본
데이터 타입은 프로그램 내에서 다뤄지는 데이터의 종류를 뜻한다.

스위프트의 데이터 타입은 모두 구조체를 기반으로 구현되어 있다.

구조체에 대해서는 추후에 자세히 다룰 예정이다.

스위프트의 모든 데이터 타입은 첫 글자가 대문자로 시작하는 대문자 카멜케이스(Upper Camel Case)를 사용한다.

## 정수형(Int, UInt)
정수형 데이터 타입에는 __Int__, __UInt__ 가 있다.

Int는 모든 정수를 포함하지만, UInt는 양의 정수만을 포함한다.

```swift
// Int 사용하기
var x1 : Int = 100
var x2 : Int = -100  // Int는 모든 정수를 나타낼 수 있다.

// UInt 사용하기
var y1 : UInt = 100
var y2 : UInt = -100  // UInt는 음수로 나타낼 수 없기 때문에 오류가 발생한다.
```

Int와 UInt의 범위를 나타내면 다음과 같다.
```swift
print("Int의 최댓값 : \(Int.max), Int의 최솟값 : \(Int.min)")
print("UInt의 최댓값 : \(UInt.max), UInt의 최솟값 : \(UInt.min)")
```
위 코드의 결과는 다음과 같다.
```
Int의 최댓값 : 9223372036854775807, Int의 최솟값 : -9223372036854775808
UInt의 최댓값 : 18446744073709551615, UInt의 최솟값 : 0
```
각 진수에 따라 정수로 표현하기 위해서는 아래와 같이 접두어를 사용해야 한다.
* 2진수 : 접두어 0b를 사용한다.
* 8진수 : 접두어 0o를 사용한다.
* 16진수 : 접두어 0x를 사용한다.

코드로 표현하면 다음과 같다.
```swift
let binary : Int = 0b101100   // 10진수 44
let octal : Int = 0o73        // 10진수 59
let hexadecimal : Int = 0x9A  // 10진수 154
```

## 부울형(Bool)
부울형 데이터 타입은 참(True)이나 거짓(False)만을 값으로 갖는다.

```swift
var boolean : Bool = true
boolean.toggle()   // 변수 boolean의 값을 반전. true → false
```

## 실수형(Float, Double)
Float와 Double은 부동소수점을 사용하는 실수로, 부동소수 타입이라고 한다.

즉, 우리가 흔히 말하는 소수점이 있는 수를 나타낸다.

Float와 Double의 차이는 표현이 가능한 자릿수에 있다.

Float의 경우, 64비트 환경에서 6자리의 10진수를 표현할 수 있으나, Double는 15자리의 10진수를 표현할 수 있다.

```swift
// Float 사용하기
var float : Float = 123.4
var roundsFloat : Float = 123.123456  // 표현 가능한 6자리를 넘었기 때문에 7째 자리에서 반올림한다.

// Double 사용하기
var double : Double = 1.23456789
var roundsDouble : Double = 123456789.123456789  // 표현 가능한 15자리를 넘었기 때문에 16째 자리에서 반올림한다.
```
위의 변수를 출력해 보면 다음과 같다.
```swift
float : 123.4
roundsFloat : 123.12346

double : 1.23456789
roundsDouble : 123456789.12345679
```

## 문자(Character)
문장처럼 문자의 집합이 아닌 단 하나의 문자를 나타낸다.

스위프트는 유니코드 9 문자를 사용하기 때문에 지원하는 모든 언어와 특수문자를 사용할 수 있다.

심지어 다음과 같이 변수의 이름에도 사용할 수 있다.

<p align="center">
  <img src="../assets/post_source/0715_swift4_1.png">
</p>

굉장히 신기하지만, 실제 프로젝트 시에는 잘 사용하지 않는 방식이라고 한다.

Character 변수를 사용할 때는 다음과 같이 값의 앞 뒤에 큰따옴표(")를 붙여 사용한다.

```swift
var character : Character = "A"
```

## 문자열(String)
문자열은 Character과 유사하지만, 여러 문자가 나열되어 있는 형태이다.

Character와 동일하게 유니코드 9을 사용하고, 값의 앞 뒤에 큰따옴표(")를 붙여 사용한다.

```swift
var name : String = "Hoojeong"

// 이니셜라이즈를 사용하여 빈 문자열 생성하기
var string : String = String()

// 문자열에 값 추가하기(이어 붙이기)
name.appen(" Kim")

// + 연산자 사용하기
string = string + "Hello!" + " My name is " + name + "."
```

```
Hello! My name is Hoojeong Kim.
```

이 밖에도 문자열의 글자 수를 세거나 비어있는 지 등 다양한 것들을 수행할 수 있다.
```swift
// 글자 수 세기
print(name.count)

// 비어있는지 확인하기
print(name.isEmpty)

// 연산자로 문자열 비교하기
var name : String = "Hoojeong"
var boolean : Bool = Bool()

boolean = name == "Hoojeong"   // 결과 값 : true

// 대소문자 변환 : 모두 대문자로 변환
name.uppercased()

// 대소문자 변환 : 모두 소문자로 변환
name.lowercased()
```

## 특수문자
스위프트에는 문자열 내에서 일정 기능을 하는 특수문자(= 제어문자)가 있다.

모두 백슬래시(\\)에 특정 문자를 조합하여 사용한다.

|특수문자|설명|
|-------|-------|
|\n|줄바꿈 문자|
|\\\\\ |문자열 내에서 백슬래시를 표햔하고자 할 때|
|\"|문자열 내에서 큰따옴표를 표햔하고자 할 때|
|\t|탭 문자. 키보드의 탭 키를 눌렀을 때와 같은 효과|
|\0|문자열이 끝났음을 알리는 null 문자|

## Any, AnyObject와 nil
Any는 스위프트의 모든 데이터 타입을 사용할 수 있다는 뜻이다.

변수 또는 상수의 데이터 타입이 Any로 지정되어 있다면, 그 변수 또는 상수에는 어떤 종류의 데이터 타입이든지 상관없이 할당할 수 있다.

AnyObject는 Any보다는 조금 한정된 의미로, 클래스의 인스턴스만 할당할 수 있다.

클래스에 대한 내용은 추후에 더 자세히 다룰 예정이다.

```swift
// Any 타입의 변수에는 정수, 실수 등 어떤 타입의 값이라도 할당할 수 있다.
var test : Any = 1
test = 10.1
test = "Hello"
test = true
```

> 하지만, Any와 AnyObject는 될 수 있으면 사용하지 않는 편이 좋다. 타입에 엄격한 스위프트의 특성상 Any 또는 AnyObject로 선언된 변수의 값을 가져다 쓰려면 매번 타입 확인 및 변환을 해줘야 하는 불편함이 있을 뿐더러, 예기치 못한 오류의 위험을 증가시키기 때문이다. 타입은 되도록이면 명시하는 것이 좋다.

nil은 사실 특정 타입이 아니라 __'없음'__ 을 나타내는 스위프트의 키워드이다.

즉, 변수 또는 상수에 값이 들어있지 않고 비어있을을 나타내는 데 사용한다.

변수나 상수가 nil일 경우, 해당 변수나 상수에 접근했을 때 잘못된 메모리 접근으로 런타임 오류(Null Point Exception)이 발생한다.
