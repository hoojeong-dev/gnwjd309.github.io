---
title: "[Swift] 1. 스위프트 기초 : 반복문"
layout: post
date: 2021-07-23 16:46
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

이번에는 조건문과 반복문 중, 반복문에 대해 공부하고자 한다.

# 반복문
조건에 따라 실행되어야 하는 명령어를 조건문을 통해 분기하거나, 같거나 비슷한 명령을 반복할 때 반복문을 사용할 수 있다.

특히나 배열과 같은 시퀀스, 순서가 있는 데이터는 반복문으로 더욱 편리하게 처리할 수 있다.

스위프트의 반복문은 기존 프로그래밍 언어의 반복문과 크게 다르지 않다.

전통적인 C 스타일의 for 구문이 사라졌다는 점과 조건에 소괄호()를 생략할 수 있다는 점을 제외하고 말이다.

또한 do-while 구문은 스위프트에서 repeat-while 구문으로 구현되어 있다.

## for-in 구문
for-in 반복 구문은 반복적인 데이터나 시퀀스를 다룰 때 많이 사용한다.

다른 언어에서의 for-each 구문과 유사하다.

```swift
for 임시 상수 in 시퀸스 아이템 {
    실행 코드
}
```
다음은 for-in 구문의 간단한 예시이다.

```swift
for i in 0...2 {
    print(i)
}
```
```
0
1
2
```

```swift
for i in 0...5 {
    if i.isMultiple(of: 2) {
        print(i)
        continue   // continue 키워드를 사용하면 바로 다음 시퀸스로
    }

    print("\(i) == 홀수")
}
```
```
0
1 == 홀수
2
3 == 홀수
4
5 == 홀수
```

```swift
let helloSwift: String = "Hello Swift!"

for char in helloSwift {
    print(char)
}
```
```
H
e
l
l
o
 
S
w
i
f
t
!
```

```swift
var result: Int = 1

// 시퀀스에 해당하는 값이 필요 없다면 와일드카드 식별자(_)를 사용
for _ in 1...3 {
    result *= 10
}

print("10의 3제곱은 \(result) 입니다.")
```
```
10의 3제곱은 1000 입니다.
```

for-in 구문은 스위프트의 기본 컬렉션 타입에서도 유용하게 사용할 수 있다.

```swift
// Dictionary
let friends: [String: Int] = ["Kim": 20, "Lee": 22, "Park": 21]

for tuple in friends {
    print(tuple)
}
```
```
(key: "Kim", value: 20)
(key: "Park", value: 21)
(key: "Lee", value: 22)
```

```swift
let address: [String: String] = ["도": "경기도", "시군구": "성남시 성남구", "동읍면": "성남동"]

for (key, value) in address {
    print("\(key) : \(value)")
}
```
```
동읍면 : 성남동
도 : 경기도
시군구 : 성남시 성남구
```

```swift
// Set
let areaCode: Set<String> = ["02", "031", "032", "033", "041", "042"]

for code in areaCode {
    print(code)
}
```
```
041
042
033
02
031
032
```

for-in 구문을 사용하여 반복 처리를 쉽게 할 수 있다.

하지만 스위프트에 더 익숙해지면 for-in 구문보다 map, filter, flatMap등을 더 많이 사용하게 될 것이다.

## while 구문
while 반복 구문도 다른 프로그래밍 언어의 while 구문과 크게 다르지 않는다.

특정 조건(__Bool 타입으로 지정되어야 한다.__)이 성립하는 한 블록 내부의 코드를 반복해서 실행한다.

for-in 구문과 마찬가지로 continue, break 등의 키워드를 사용할 수 있다.

```swift
var names: [String] = ["Kim", "Lee", "Park"]

while names.isEmpty == false {
    print("Good bye \(names.removeFirst())")
}
```
```
Good bye Kim
Good bye Lee
Good bye Park
```

## repeat-while 구문
repeat-while 반복 구문은 다른 프로그래밍 언어의 do-while 구문과 크게 다르지 않다.

repeat 블록의 코드를 먼저 실행한 후, while 다음의 조건이 성립하면 블록 내부의 코드를 반복 실행한다.

```swift
var names: [String] = ["Kim", "Lee", "Park"]

repeat {
    print("Good bye \(names.removeFirst())")
} while names.isEmpty == false
```
```
Good bye Kim
Good bye Lee
Good bye Park
```

## 구문 이름표
반복문을 작성하다 보면 종종 반복문을 중첩으로 작성하게 된다.

이때 반복문을 제어하는 키워드가 어떤 범위에 적용되어야 하는 지 애매하거나 큰 범위의 반복문을 종료하고 싶은데 작은 범위의 반복문만 종료되는 등 예상치 못한 실수를 할 수도 있다.

이러한 경우에는 반복문 앞에 이름과 함께 콜론을 붙여 구문의 이름을 지정해주면 좋다.

이름이 지정된 구문을 제어하고자 할 때는 제어 키워드와 구문 이름을 함께 써주면 된다.

```swift
var numbers: [Int] = [3, 2342, 6, 3252]

numbersLoop: for num in numbers {
    if num > 5 || num < 1 {
        continue numbersLoop
    }

    var count: Int = 0

    printLoop: while true {
        print(num)
        count += 1

        if count == num {
            break printLoop
        }
    }

    removeLoop : while true {
        if numbers.first != num {
            break numbersLoop
        }
        numbers.removeFirst()
    }
}

print(numbers)
```
```
3
3
3
[2342, 6, 3252]
```