---
title: "[BOJ] 백준 알고리즘 : 큐, 덱"
layout: post
date: 2021-08-12 16:04
image:
headerImage: false
tag:
- baekjoon
- algorithm
- java
category: blog
author: Hoojeong Kim
description: 백준 알고리즘 문제 풀이
---
<br/>

* 모든 문제는 Python 언어를 사용했습니다.
* 해당 <a href="https://www.acmicpc.net/step/12" target="_blank">링크</a>에서 문제를 확인할 수 있습니다.

---

# 큐(Queue)
큐는 가장 먼저 넣은 데이터를 가장 먼저 꺼낼 수 있는 구조이다.  
줄을 서는 행위와 유사하다고 할 수 있다.
* FIFO(First-In, First-Out) 또는 LILO(Last-In, Last-Out) 방식을 갖는다.
* LIFO 또는 FILO 방식을 갖는 스택과 반대이다.

<p align="center">
  <img src="https://www.fun-coding.org/00_Images/queue.png">
</p>
</br>

파이썬 Queue 라이브러리에는 다양한 큐 구조를 제공한다.
* Queue() : 앞에서 설명한, 가장 일반적인 큐 자료 구조
* LifoQueue() : 나중에 입력된 데이터가 먼저 출력되는 구조 (스택과 동일)
* PriorityQueue() : 데이터마다 우선순위를 넣어, 우선순위가 높은 순으로 출력
</br>

## 10845번 : 큐

일반적인 큐를 구현하는 문제로, 개념만 이해했다면 쉽게 풀 수 있다.

```python
import sys

n=int(sys.stdin.readline())
data_queue=list()

for index in range(n):
    data=sys.stdin.readline().split()
    
    if data[0]=='push':
        data_queue.append(data[1])
        
    elif data[0]=='pop':
      print(data_queue.pop(0) if len(data_queue) else -1)
            
    elif data[0]=='size':
        print(len(data_queue))
        
    elif data[0]=='empty':
      print(0 if len(data_queue) else 1)
            
    elif data[0]=='front':
      print(data_queue[0] if len(data_queue) else -1)
            
    elif data[0]=='back':
      print(data_queue[len(data_queue)-1] if len(data_queue) else -1)
```

## 18258번 : 큐2

앞의 문제와 동일하지만, 범위가 크게 증가했기 때문에 소요 시간을 생각해야 한다.  

pop 동작을 수행하게 되면 맨 앞의 요소를 제거한 뒤, 그 뒤에 있는 모든 요소들을 앞으로 옮긴다.  
이 과정에서 시간이 생각보다 많이 걸리는 것 같다.

새로운 변수를 추가하여 첫번째가 될 요소의 위치를 기억하게 한다.  
그렇게 하면 pop을 할 때마다 일일히 요소를 삭제할 필요가 없으며, 전체 큐의 크기와 위치 변수의 값이 동일할 때 큐를 초기화 하면 된다.

```python
import sys

n=int(sys.stdin.readline())
data_queue=list()
index = 0   # 맨 앞의 위치를 기억하는 변수

for i in range(n):
    data=sys.stdin.readline().split()

    if data[0]=='push':
        data_queue.append(data[1])

    # 첫번째가 될 요소의 위치를 기억하는 변수를 두어, 계속 뒤에 추가함
    elif data[0]=='pop':
        if len(data_queue) > index:
            print(data_queue[index])  
			# pop을 하게 된다면 맨 앞의 요소가 지워지므로 index가 1만큼 증가
			index += 1 
        else: print(-1)

    elif data[0]=='size':
        print(len(data_queue)-index)

    elif data[0]=='empty':
        # 큐의 크기와 index의 크기가 같아질 때 큐를 비움
        if len(data_queue) == index:
            print(1)
            index, data_queue = 0, []
        else: print(0)

    elif data[0]=='front':
        print(data_queue[index] if len(data_queue) > index else -1)

    elif data[0]=='back':
        print(data_queue[-1] if len(data_queue) > index else -1) 
```

