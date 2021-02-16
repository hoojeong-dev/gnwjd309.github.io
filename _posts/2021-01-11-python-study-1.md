---
title: "[Python] Python 기초"
layout: post
date: 2021-01-11 16:31
image: 
headerImage: false
tag:
- python
- list
- study
category: blog
author: Hoojeong Kim
description: python study
---
# __Python 기초 정리__

* 수업을 들으며 배운 내용을 정리한 포스트 입니다.
* 해당 실습은 *Jupyter notebook*을 통해 진행되었습니다.

<br>

## __python version__


```python
# python system 기능을 사용하기 위해 사용하는 라이브러리
import sys

# "Python version" 이라는 문자열을 출력
print("Python version")

# sys.version에 저장되어있는 값을 출력
print (sys.version)
 
# "Version info." 이라는 문자열을 출력
print("Version info.")

# sys.version_info에 저장되어있는 값을 출력
print (sys.version_info)
```
    >  Python version  
    >  3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]  
    >  Version info.  
    >  sys.version_info(major=3, minor=8, micro=5, releaselevel='final', serial=0)

<br>

---

<br>

## __변수__

* ### __문자열 출력__
<br>

```python
print('딥러닝 활용')
print('셀 실행은 shift + Enter')
```
 
    >  딥러닝 활용  
    >  셀 실행은 shift + Enter
    
<br>

* ### __문자열 변수 할당__

<br>

```python
title ='딥러닝 활용'
command_string='셀 실행은 shift + Enter'
print(title)
print(command_string)
```

    >  딥러닝 활용
    >  셀 실행은 shift + Enter
    
<br>

* ### __변수이름 명명 법__
    - class 이름 : pascal case(파스칼 표기법)

      `Title, CommandString`
    - 상수 : 대문자

      `TITLE, COMMAND_STRING`
    - 변수 or 함수 : snake case or pothole case

      `title, title_string`

<br>

---
<br>

## __List (배열)__

* ### __배열의 선언__
<br>

```python
sample_array = ['a', 'b', 'c', 'd', 'e', 'f']
```


```python
print(sample_array)
```
        
    >  ['a', 'b', 'c', 'd', 'e', 'f']
    


```python
#배열의 선언 & 원소 추가

sample_array2 = []
sample_array2.append('a')
sample_array2.append('b')
sample_array2.append('c')
sample_array2.append('d')
sample_array2.append('e')
sample_array2.append('f')
```


```python
print(sample_array2)
```

    > ['a', 'b', 'c', 'd', 'e', 'f']
    


```python
# 배열의 길이

len(sample_array2)
```
    >  6


```python
# 배열의 정렬
# 배열.sort() -> 오름차순 (Default)
# 배열.sort(reverse=True) -> 내림차순 (False = 오름차순)

sample_array2.sort(reverse=True)
```


```python
print(sample_array2)
```

    >  ['f', 'e', 'd', 'c', 'b', 'a']
    
<br>

* ### __배열의 색인__
<br>

```python
# [0:3] : 0 <= 색인 < 3
print(sample_array[0:3])

# [3:] : 3<= 색인 <= 끝
print(sample_array[3:])

# [:3] : 시작 <= 색인 < 3
print(sample_array[:3])
```

    >  ['a', 'b', 'c']
    >  ['d', 'e', 'f']
    >  ['a', 'b', 'c']
    
<br>

* ### __배열 정보__
<br>

```python
# 형변환(type cast)
# 문자열과 다른 유형의 변수의 연산은 다른 유형의 변수를 문자열로 변경한다.

array_length = len(sample_array)
array_type = type(sample_array)

# 배열의 길이
print('length : ' + str(array_length))

# 변수의 타입
print('type: ' + str(array_type))

print('type: ' + str(type(command_string)))
```

    >  length : 6
    >  type: <class 'list'>
    >  type: <class 'str'>
    
<br>

* ### __range(start,end)__

    - start, end까지 값을 가지는 range

    - list(range(start,end)) 값을 통해서 array값을 생성
<br>

```python
# 0~20의 숫자릴 리스트에 삽입

simple_array = list(range(0,20))
```


```python
print(simple_array)
```

    >  [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
    
