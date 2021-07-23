---
title: "[Swift] 1. 스위프트 기초 : 데이터 타입 2"
layout: post
date: 2021-07-15 18:02
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

# 데이터 타입 고급
기본적인 데이터 타입에 대해 알아봤으니, 더 복잡한 내용을 다뤄보고자 한다.

(이전 내용은 <a href="https://hoojeong.dev/swift-4/" target="_blank">데이터 타입 1</a>에서 확인할 수 있습니다.)

이제 프로젝트에서 유용하게 사용할 수 있는 튜플이나 컬렉션형 등의 확장된 내용에 대해 배워보자.

## 타입 추론
스위프트에서는 변수나 상수를 선언할 때 특정 타입을 명시하지 않아도 컴파일러가 할당된 값을 기준으로 변수나 상수의 타입을 결정한다.

```swift
var name = "Hoojeong"  //  타입을 지정하지 않았으나 타입 추론을 통해 String 타입으로 선언

name = 100  // String 변수로 지정되었기 때문에 정수를 할당하려고 하면 오류가 발생한다.
```

## 티입 별칭
스위프트에서 기본으로 제공하는 데이터 타입이든, 사용자가 임의로 만든 데이터 타입이든 이미 존재하는 데이터 타입에 임의로 다른 이름을 부여할 수 있다.

```swift
typealias MyInt = Int

let x : MyInt = 100
```

## 튜플(Tuple)
튜플은 타입의 이름이 따로 지정되어 있지 않은, 프로그래머 마음대로 만드는 타입이다.

스위프트의 튜플은 파이썬의 튜플과 유사하다.

튜플은 타입 이름이 따로 없으므로 일정 타입의 나열만으로 튜플 타입을 생성해줄 수 있다.

튜플에 포함될 데이터의 새구는 자유롭게 정할 수 있다.

```swift
// String, Int, Double 타입을 갖는 튜플
var Person : (String, Int, Double) = ("Hoojeong", 22, 160.0)

// 인덱스를 사용해 값을 출력할 수 있다.
print("이름 : \(Person.0), 나이 : \(Person.1), 키 : \(Person.2)")

// 인덱스를 사용해 값을 바꿀 수 있다.
Person.1 = 20
Person.2 = 165.0

print("이름 : \(Person.0), 나이 : \(Person.1), 키 : \(Person.2)")
```

```
이름 : Hoojeong, 나이 : 22, 키 : 160.0
이름 : Hoojeong, 나이 : 20, 키 : 165.0
```

튜플 요소의 이름이나 별칭을 정하는 것도 가능하다.
```swift
var Person : (name : String, age : Int, height : Double) = ("Hoojeong", 22, 160.0)

// 요소 이름을 통해 값을 출력할 수 있다.
print("이름 : \(Person.name), 나이 : \(Person.age), 키 : \(Person.height)")

// 요소 이름이나 인덱스를 통해 값을 바꿀 수 있다.
Person.age = 20
Person.2 = 165.0

print("이름 : \(Person.0), 나이 : \(Person.1), 키 : \(Person.2)")

print("\n")

// 튜플의 별칭을 정할수 있다.
typealias DogTuple = (name : String, age : Int, weight : Double)

let happy : DogTuple = ("happy", 2, 4.2)

print("이름 : \(happy.name), 나이 : \(happy.age), 무게 : \(happy.weight)")
```

```
이름 : Hoojeong, 나이 : 22, 키 : 160.0
이름 : Hoojeong, 나이 : 20, 키 : 165.0


이름 : happy, 나이 : 2, 무게 : 4.2
```

## 배열(Array)
배열은 같은 타입의 데이터를 일렬로 나열한 후 순서대로 저장하는 형태의 컬렉션 타입이다.

```swift
// 배열 선언하기
var names : Array<String> = ["abc", "def", "ghi"]

// Array<String>의 축약 표현
var names : [String] = ["abc", "def", "ghi"]

// Any 데이터를 요소로 하는 빈 배열 생성
var empty : [Any] = [Any]()
var empty : [Any] = Array<Any>()

// 배열의 타입을 명시했다면, []로 빈 배열 생성 가능
var emptyArray : [Any] = []
```

배열은 각 요소에 인덱스를 통해 접근할 수 있다.

인덱스는 0부터 시작하며, 잘못된 인덱스로 접근할 경우, Exception 오류가 발생한다.

```swift
var alphabet = ["A", "B", "C", "D"]

print(alphabet.count)  // 배열의 요소 개수
print(alphabet[1])

alphabet[1] = "H"

print(alphabet[1])
print(alphabet[4])  // 배열의 범위를 벗어났기 때문에 오류 발생

print(alphabet)
```

```
4
B
H
["A", "H", "C", "D"]
```

배열의 맨 뒤에 요소를 추가하고 싶다면 __append(_:)__ 메서드를 사용한다.

중간에 요소를 추가하고 싶다면 __insert(_:at:)__ 메서드를 사용한다. 

```swift
// 배열에 요소 추가
alphatbet[4] = "E"  // 범위를 벗어났기 때문에 오류 발생
alphabet.append("E")   // 배열의 맨 뒤에 요소 추가
print(alphabet)

alphabet.append(contentsOf : ["F", "G"]) // 한 번에 여러 개 추가
print(alphabet)

alphabet.insert("B", at : 1)  // 인덱스 1에 B 추가
print(alphabet)

alphabet.insert(contentsOf : ["X", "Y"], at : 3)  // 인덱스 3에 한 번에 여러 개 추기
print(alphabet)
```

```
["A", "H", "C", "D", "E"]
["A", "H", "C", "D", "E", "F", "G"]
["A", "B", "H", "C", "D", "E", "F", "G"]
["A", "B", "H", "X", "Y", "C", "D", "E", "F", "G"]
```

맨 처음과 마지막 요소는 __first__, __last__ 프로퍼티를 통해 가져올 수 있으며, __firstIndex(of:)__ 메서드를 사용해 해당 요소의 인덱스를 알아낼 수 있다.

만약 중복된 요소가 있다면, 제일 먼저 발견된 요소의 인덱스를 반환한다.

```swift
// 특정 요소의 인덱스 알아내기
print(alphabet.firstIndex(of : "H"))
print(alphabet.firstIndex(of : "K"))

// 맨 처음과 맨 마지막 요소 알아내기
print(alphabet.first)
print(alphabet.last)
```

```
Optional(2)
nil
Optional("A")
Optional("G")
```

만약 요소를 삭제하고 싶다면 __remove(_:)__ 메서드를 사용하는데, 메서드를 사용하면 해당 요소가 삭제된 후 반환된다.

```swift
// 특정 요소 삭제하기
let firstItem : String = alphabet.removeFirst()  // 첫 번째 요소 삭제
let lastItem : String = alphabet.removeLast()  // 마지막 요소 삭제
let indexOneItem : String = alphabet.remove(at: 1)  // 인덱스 1 요소 삭제

print(firstItem)
print(lastItem)
print(indexOneItem)
print(alphabet)
```

```
A
G
H
["B", "X", "Y", "C", "D", "E", "F"]
```

특정 인덱스 범위의 요소들만 출력하는 것도 가능하다.

```swift
// 요소 출력하기
print(alphabet)  // 전체 요소 출력하기
print(alphabet[2 ... 4])// 인덱스가 2 ~ 4에 해당하는 요소 출력하기
```

```
["B", "X", "Y", "C", "D", "E", "F"]
["Y", "C", "D"]
```
