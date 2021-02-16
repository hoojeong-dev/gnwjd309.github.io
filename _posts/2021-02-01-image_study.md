---
title: "[Python] Computer Vision - Convolution Study"
layout: post
date: 2021-02-01 19:27
image: 
headerImage: false
tag:
- python
- convolution
- study
category: blog
author: Hoojeong Kim
description: python study
---
# Computer Vision 기초

- Computer Vision의 종류
- 이미지에서 특징 추출하기
- Keras에서 제공되는 모델
- imagenet model architecture
- 학습된 이미지를 이용하여 특징 추출하기
  - RESNET50
  - VGG16

<br>

## Neural Network  
이 과정에서, 가중치를 부여하고 그에 따른 결과를 저장하는 것을 학습이라고 한다.
가중치가 저장된 데이터를 모델이라고 한다.

<br>

## Convolution
이미지를 박스에 담아서 값의 특징을 잡고, 박스에 다시 담아줌..(?)  

<br>

## CNN이란?
  Convolution Neural Network의 약자로, 합성곱 신경망이라고 한다.  
   주로 이미지나 동영상을 분석하는데 사용된다.

<br>

### __기존 계층과 합성곱 계층 비교__
 - 기존 계층(완전 연결 계층)
   - 1차원
   - 데이터의 형상을 무시한다.  
      - 글자의 크기나 방향 등, 글자에 조금이라도 변형이 생기면 다른 글자로 인식하기 때문에, 새로운 학습 데이터가 필요하다.  
      - 따라서 본질적인 패턴을 읽지 못해, 인식을 위한 다양한 데이터가 많이 필요하다.
 - 합성곱 계층
   - 3차원
   - 원본 이미지를 가지고, 여러 개의 입출력 데이터인 Feature Map(특징맵)을 만들어 분류한다. 
      - 이미지의 특징을 추출하기 때문에, 이미지가 변형되더라도 잘 인식할 수 있다.
<br>
<p align="center">
  <img src="../assets/post_source/convolution.gif">
</p>