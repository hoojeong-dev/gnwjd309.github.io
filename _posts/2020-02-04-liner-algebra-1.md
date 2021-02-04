---
title: "[Linear Algebra] 넘파이(Numpy) - 데이터와 행렬"
layout: post
date: 2020-02-04 07:19
image: 
headerImage: false
tag:
- python
- linear algebra
- numpy
- study
category: blog
author: Hoojeong Kim
description: linear algebra study
---
- [데이터 사이언스 스쿨](https://datascienceschool.net/intro.html){:target="_blank"} 을 통해 공부한 내용을 정리한 글입니다.
- 모든 코드는 **jupyter notebook**으로 작성되었습니다.
- 넘파이와 관련된 기본적인 코드는 해당 게시글을 참고해주세요.
    - [[Python] Python Numpy(넘파이)](https://hoojeong.dev/python-study-2/){:target="_blank"}

---

# 선형대수란?
선형대수(Linear algebra)는 데이터 분석에 필요한 각종 계산을 돕는 학문이다. 선형대수를 사용해 대량의 데이터를 포함하는 복잡한 계산 과정을 간단한 수식으로 표현할 수 있다.

선형대수는 덧셈과 상수곱 구조를 갖는 벡터공간이 존재한다. 이차, 삼차함수같은 곡선이나 포물선이 존재하지 않고, 오직 직선(linear)으로만 이루어져 있다.

먼저, 넘파이로 코드를 작성하기 위해 넘파이 패키지를 import 한다.

```python
import numoy as np
import matplotlib.pylab as plt
```
## __matplot__ 란?  
파이썬에서 그래프를 그릴 때 주로 사용하는 패키지이다.  
matplot 패키지 안에는 pyplot와 pylab라는 모듈이 존재한다.

### __pyplot__
pyplot는 사용환경 인터페이스(state-machine interface)를 제공한다.  
해당 인터페이스는 겉으로는 드러나지 않으면서, 자동으로 figure와 axes를 생성하여 정의된 plot을 얻을 수 있도록 한다.  
 * axes : figure 내에서 축을 갖는 하나의 좌표평면과 같은 개념. 실제로 데이터는 axes에 그려진다.

### __pylab__
pylab는 대부분의 matplotlib.pyplot와 numpy를 하나의 네임스페이스에 import 한다.
 - 이는 편리하기는 하지만, 네임스페이스가 더러워진다는 단점이 존재.

추가적으로 pylab는 앞으로 사라질 것으로 전망된다.  
실습에서는 pylab를 사용했지만, 나는 pyplot를 사용하려고 한다.

---

# 데이터의 유형
선형대수에서 다루는 데이터는 개수나 형태에 따라 다음과 같이 나뉜다.
 - 스칼라(scalar)
 - 벡터(vector)
 - 행렬(matrix)
 - 텐서(tensor)

## __스칼라__
스칼라는 하나의 숫자로 이루어진 것을 말한다. (상수 = 스칼라)
```
                                    x ∈ R
```

## __벡터__
고등학교 때 배웠다면, 쉽게(?) 이해할 수 있는 개념이다. 벡터는 여러 개의 숫자가 특정한 순서대로 모여있는 것을 말한다.  
쉽게 말해서 크기(값)만을 가지는 스칼라와 달리, 크기와 방향을 모두 갖는 것을 벡터라고 한다.  

예를 들어, "원점에서 동쪽으로 40m"를 수학적으로 표현하고자 한다면, 크기와 방향 성분 모두가 필요하기 때문에 벡터로 표현해야 한다.

이때 벡터는 가로가 행(row), 세로가 열(column)의 형태를 갖는다.
```
                                x = ⎡ a, b ⎤
                                    ⎣ c, d ⎦
```
하나의 벡터를 이루는 데이터의 개수가 n개이면, 이 벡터를 n차원 벡터라고 한다.
```
                                x = ⎡ x1 ⎤
                                    ⎢ x2 ⎥
                                    ⎢ .. ⎥
                                    ⎣ xN ⎦
```
* __특징 벡터__
    * 데이터 벡터가 예측 문제에서 입력 데이터로 사용되면, 이를 __특징 벡터(feature vector)__ 라고 한다.


## 연습문제 2.1.1
