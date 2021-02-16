---
title: "[Python] Python Pandas(판다스)"
layout: post
date: 2021-01-18 19:13
image: 
headerImage: false
tag:
- python
- pandas
- study
category: blog
author: Hoojeong Kim
description: python study
---
# __Python Pandas 기초 정리__

* 수업을 들으며 배운 내용을 정리한 포스트 입니다.
* 해당 실습은 *Jupyter notebook*을 통해 진행되었습니다.

<br>

## __Pandas__
* ### 데이터 분석 및 조회를 쉽게 사용 하는 라이브러리, 표 형태로 이용한다.
    - Series : 1차원
    - DataFrame : 2차원
    - Panel : 3차원
<br>

```python
# pd라는 이름으로 사용한다(관례상)
import pandas as pd
```
<br>

### __1. series__

Serise 클래스는 넘파이에서 제공하는 1차원 배열과 비슷하지만, 각 데이터에 인덱스를 부여할 수 있다.
> Serise = 값(value) + 인덱스(index)

<br>

```python
# Series 생성
sr = pd.Series(['A', 'B+', 'A+', 'B'])
print(sr)
```

    >  0     A
       1    B+
       2    A+
       3     B
       dtype: object
    


```python
# Series의 값만 확인
print(sr.values)
```

    >  ['A' 'B+' 'A+' 'B']
    


```python
# Series의 자료형 확인
type(sr.values)
```

    >  numpy.ndarray




```python
# Series의 index 설정 가능
sr1 = pd.Series(['90','80','70','60'], index = ['국어','수학','영어','과학'])
print(sr1)
```

    >  국어    90
       수학    80
       영어    70
       과학    60
       dtype: object
    


```python
# index만 확인
print(sr1.index)
```

    Index(['국어', '수학', '영어', '과학'], dtype='object')
    
<br>

  * dictionary 자료형을 Series의 data로 만들 수 있음
  * dictionary의 key가 Series의 index가 됨

<br>

```python
sdata = {'Kim' : 10, 'Hoo' : 20, 'Jeong' : 30, '22' : 40}
sr3 = pd.Series(sdata)
sr3
```

    >  Kim      10
       Hoo      20
       Jeong    30
       22       40
       dtype: int64




```python
sr3.name = 'Name'
sr3.index.name = "Profile"
sr3
```

    >  Profile
       Kim      10
       Hoo      20
       Jeong    30
       22       40
       Name: Name, dtype: int64




```python
# index만 변경하기
sr3.index = ['A', 'B', 'C', 'D']
sr3
```

    >  A    10
       B    20
       C    30
       D    40
       Name: Name, dtype: int64


<br>

* ### __2. dataframe__
<br>

```python
# Data Frame 생성
# Data Frame에 들어갈 data를 정의할 때, dictionary나 array로 정의할 수 있음

data = [['1', 'a', 90.72], 
        ['2', 'b', 78.09], 
        ['3', 'c', 98.43], 
        ['4', 'd', 64.19], 
        ['5', 'e', 81.30],
        ['6', 'f', 99.14]]
df = pd.DataFrame(data)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>a</td>
      <td>90.72</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>b</td>
      <td>78.09</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>c</td>
      <td>98.43</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>d</td>
      <td>64.19</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>e</td>
      <td>81.30</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>f</td>
      <td>99.14</td>
    </tr>
  </tbody>
</table>
</div>


<br>

```python
# 행과 열의 구조를 가진 data가 생성 됨

# 행 방향의 index
print(df.index,'\n')

# 열 방향의 index
print(df.columns,'\n')

# data 얻기
print(df.values)
```

    >  RangeIndex(start=0, stop=6, step=1) 
    
    >  RangeIndex(start=0, stop=3, step=1) 
    
    >  [['1' 'a' 90.72]
        ['2' 'b' 78.09]
        ['3' 'c' 98.43]
        ['4' 'd' 64.19]
        ['5' 'e' 81.3]
        ['6' 'f' 99.14]]
    


```python
# Data Frame을 만들며, index와 columns를 설정할 수 있음

df = pd.DataFrame(data, columns=['학번', '이름', '점수'], index=['One', 'Two', 'Three', 'Four', 'Five', 'Six'])
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학번</th>
      <th>이름</th>
      <th>점수</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>One</th>
      <td>1</td>
      <td>a</td>
      <td>90.72</td>
    </tr>
    <tr>
      <th>Two</th>
      <td>2</td>
      <td>b</td>
      <td>78.09</td>
    </tr>
    <tr>
      <th>Three</th>
      <td>3</td>
      <td>c</td>
      <td>98.43</td>
    </tr>
    <tr>
      <th>Four</th>
      <td>4</td>
      <td>d</td>
      <td>64.19</td>
    </tr>
    <tr>
      <th>Five</th>
      <td>5</td>
      <td>e</td>
      <td>81.30</td>
    </tr>
    <tr>
      <th>Six</th>
      <td>6</td>
      <td>f</td>
      <td>99.14</td>
    </tr>
  </tbody>
</table>
</div>

<br>


```python
df.head(3)
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학번</th>
      <th>이름</th>
      <th>점수</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>One</th>
      <td>1</td>
      <td>a</td>
      <td>90.72</td>
    </tr>
    <tr>
      <th>Two</th>
      <td>2</td>
      <td>b</td>
      <td>78.09</td>
    </tr>
    <tr>
      <th>Three</th>
      <td>3</td>
      <td>c</td>
      <td>98.43</td>
    </tr>
  </tbody>
</table>
</div>


<br>

```python
df.tail(3)
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학번</th>
      <th>이름</th>
      <th>점수</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Four</th>
      <td>4</td>
      <td>d</td>
      <td>64.19</td>
    </tr>
    <tr>
      <th>Five</th>
      <td>5</td>
      <td>e</td>
      <td>81.30</td>
    </tr>
    <tr>
      <th>Six</th>
      <td>6</td>
      <td>f</td>
      <td>99.14</td>
    </tr>
  </tbody>
</table>
</div>


<br>

```python
df['이름']
```

    >  One      a
       Two      b
       Three    c
       Four     d
       Five     e
       Six      f
       Name: 이름, dtype: object
