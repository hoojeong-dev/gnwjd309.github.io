---
title: "[Swift] 1. 스위프트 기초 : 조건문"
layout: post
date: 2021-07-23 16:07
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

# 흐름 제어
프로그램을 작성하다보면 특정 조건에서 코드를 실행해야 하거나, 특정 명령어를 반복해야하는 일이 종종 발생한다.

이럴 때 사용하는 것이 바로 조건문과 반복문이다.

대부분의 프로그래밍 언어에서 조건문과 반복문을 다루지만 스위프트는 다른 언어와 차이가 있으니 유의해야 한다.

스위프트의 흐름 제어 구문에서는 소괄호()를 대부분 생략할 수 있으나, 중괄호{}는 생략할 수 없다.

이번에는 조건문과 반복문 중, 조건문에 대해 공부하고자 한다.

# 조건문
조건문으로는 if 구문과 swift 구문이 있다.

스위프트에는 guard 구문도 있으나, 이는 추후에 다루고자 한다.

## if 구문
if 구문은 대표적인 조건문으로 if, else 등의 키워드를 사용하여 구현할 수 있다.

정수, 실수 등 0이 아닌 모든 값을 참으로 취급하여 조건 값이 될 수 있었던 다른 언어와는 달리 ___스위프트의 if 문은 조건의 값이 꼭 Bool 타입__ 이어야 한다.

if 구문의 기본적인 사용은 다음과 같다.

```swift
if 조건 수식1 {
    실행 코드
}
else if 조건 수식2 {
    실행 코드
}
else if 조건 수식3 {
    실행 코드
}
else {
    실행 코드
}
```

else if는 몇 개가 이어져도 상관 없으며 else 블록은 없어도 상관이 없다.

if 문에서 여러 개의 조건을 순차적으로 대조하다가 특정 조건에 일치한다면 그에 해당하는 코드를 실행하고, 그 다음에 이어진 조건문은 조건에 충족하더라도 실행되지 않고 조건문을 빠져나온다.

이때 각 블록의 조건에는 소괄호()를 붙이지 않아도 상관이 없다.

다음은 if 구문을 사용해 두 변수의 값을 비교하는 코드이다.

```swift
let first: Int = 1
let second: Int = 2

if first > second {
    print("first > second")
} else if first < second {
    print("first < second")
} else {
    print("first == second")
}
```

```
first > second
```

## switch 구문
기본 문법이라 할 수 있는 switch 구문은 다른 언어와 비교했을 때 많이 달라진 문법 중 하나이다.

switch 구문도 if문 처럼 소괄호()를 생략할 수 있으며, break 키워드 또한 선택적으로 사용한다.

즉, case 내부의 코드를 실행하면 break 없이도 switch 구문이 종료된다는 뜻인데, 이 방식은 예상치 못한 실수를 중이는 데도 큰 도움이 된다.

스위프트에서 switch 구문의 case를 연속 실행하려면 fallthrough 키워드를 사용한다.

C 언어에서는 조건에 정수 타입만 들어갈 수 있었지만, 스위프트에서는 다양한 값이 들어갈 수 있다.

다만 각 case에 들어갈 비교 값은 입력 값과 데이터 타입이 같아야 한다.

또, 비교될 값이 명확히 한정적인 값(열거형 값 등)이 아닐 때는 default를 꼭 작성해야 한다.

또한 각 case에는 범위 연산자나 where 절을 사용해 조건을 확장할 수 있다.

swift 구문의 사용은 기본적으로 다음과 같다.

```swift
swift 입력 값 {
case 비교 값1 :
    살행 코드
case 비교 값2 :
    실행 코드
    // 이번 case를 마치고 switch 구문을 탈출하지 않음
    fallthrough
case 비교 값3, 비교 값4, 비교 값5 : // 한 번에 여러 값 비교 가능
    실행 코드
    break   // break 키워드의 사용은 선택 사항
default :
    실행 코드
}
```

다음은 간단한 switch 구문 활용이다.

```swift
let integerValue: Int = 5

switch integerValue {
case 0:
    print("Value == Zero")
case 1...10:
    print("Value == 1~10")
    fallthrough
case Int.min..<0, 101..<Int.max:
    print("Value < 0 or Value > 100")
    break
default:
    print("10 < Value <= 100")
}
```

```
Value == 1~10
Value < 0 or Value > 100
```

위의 코드처럼 case의 비교 값에 단 하나의 값 뿐만이 아니라 범위 연산자를 넣을 수도 있다.

결과에서 "Value < 0 or Value > 100"이 출력된 이유는, 두 번째 블록에서 fallthrough 키워드를 사용하여 세 번째 블록도 실행되도록 했기 때문이다.

만약 integerValue의 값이 0이었다면, "Value == zero"만 출력됐을 것이다.

범위 연산자는 정수 뿐만이 아니라 부동소수 타입에도 사용할 수 있으며, switch 구문의 입력 값으로는 숫자 뿐만이 아니라 문자, 문자열, 열거형, 튜플 등의 타입 값도 사용할 수 있다.

타 언어에서는 아래와 같은 방식으로 사용이 가능하다.

```java
int num = 3;

switch (num) {
    case 0:
    case 1:
    case 2:
    case 3:
        print("num >= 3");
    default:
        print("num < 3")
}
```
위 코드는 java를 사용해 작성한 switch 코드이다.

java나 C 등은 처럼 case 안의 실행 코드를 생략하며 사용할 수 있지만, 스위프트에서 이러한 방식을 사용하게 되면 오류가 발생한다.

따라서 위와 같은 코드를 작성하고 싶을 때는 fallthrough 키워드를 사용해야 한다.

```swift
let num: Int = 3

switch num {
case 0:
    fallthrough
case 1:
    fallthrough
case 2:
    fallthrough
case 3:
    print("num >= 3")
default:
    print("num < 4")
}
```