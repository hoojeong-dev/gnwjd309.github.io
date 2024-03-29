---
title: "[Swift] 1. 스위프트 기초 : 데이터 타입 3"
layout: post
date: 2021-07-23 15:13
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
* 이전 내용은 다음 링크를 참고해주세요.
    - <a href="https://hoojeong.dev/swift-4/" target="_blank">데이터 타입 1</a>
    - <a href="https://hoojeong.dev/swift-5/" target="_blank">데이터 타입 2</a>

---

# 데이터 타입 고급
기본적인 데이터 타입에 대해 알아봤으니, 더 복잡한 내용을 다뤄보고자 한다.

이제 프로젝트에서 유용하게 사용할 수 있는 튜플이나 컬렉션형 등의 확장된 내용에 대해 배워보자.

## 딕셔너리
딕셔너리는 요소들이 순서 없이 키와 값의 쌍으로 구성되는 컬렉션 타입이다.

딕셔너리에 저장되는 값은 항상 키와 쌍을 이루게 되는데, 딕셔너리 안에는 키가 하나이거나 여러 개일 수 있다.

이때 하나의 키는 값을 대변하는 유일한 식별자로서 같은 이름을 중복해서 사용할 수 없다.

```swift
// 딕셔너리 선언하기
var dictionary : Dictionary<String, Int> = Dictionary<String, Int>()
var dictionary : [String: Int] = [String : Int]()
var dictionary : StringIntDictionary = StringIntDictionary()

// 비어있는 딕셔너리 생성
var dict : [String: Int] = [:]
```

딕셔너리는 다음과 같이 사용할 수 있다.

```swift
var numberForName: [String: Int] = ["Kim": 100, "Lee": 200, "Choi": 300]

print(numberForName.isEmpty)   // 딕셔너리가 비어있는지 확인
print(numberForName.count)     // 딕셔너리의 개수 확인

// 키로 값 출력하기
print(numberForName["Kim"])
print(numberForName["Park"])   // 해당되는 키가 없으므로 nil 출력

// 값 추가하기
numberForName["Koh"] = 400
print(numberForName)

// 특정 키로 값 지우기
numberForName.removeValue(forKey: "Kim")
print(numberForName)
```

```
false
3
Optional(100)
nil
["Kim": 100, "Lee": 200, "Koh": 400, "Choi": 300]
["Lee": 200, "Koh": 400, "Choi": 300]
```