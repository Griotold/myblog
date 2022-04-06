---
title: "혼동행렬"
author: "HS"
date: '2022-04-06'
categories: 'Python'
---
# 혼동행렬(Confusion matrix) 
<!-- more-->
- 모델의 성능을 평가할 때 사용되는 지표
- 지도학습에서 알고리즘의 성능을 시각화 할 수 있는 표를 말한다.
- 분류 모델을 학습하는 것의 목적은 주어진 데이터를 의도에 맞게 잘 분류해내기 위한 것이다.
- 그렇다면 이러한 모델을 평가하는 기준이 필요할 것이다. 
- 모델을 평가할 때는 모델이 얼마나 정밀한지, 얼마나 실용적인 분류를 했는지, 얼마나 정확한 분류를 했는지를 평가해야 한다.
- 이러한 내용들을 모두 포함하고 있는 것이 혼동행렬이다.

## 네 가지 상황
- TP(True Positive) : 맞는 것을 올바르게 맞다고 예측한 것
- TN(True Negative) : 아닌 것을 틀리다고 예측한 것
- FP(False Positive) : 아닌 것을 맞다고 예측한 것
- FN(False Negative) : 맞는 것을 틀리다고 예측한 것

## 정밀도(Precision) 
- 정밀도란 모델이 True라고 분류한 것 중에서 실제 True인 것의 비율이다. 
- Precision = TP / (TP + FP)
- PPV(Positive Predictive Value)
- Positive 정답률

## 재현율(Recall)
- 실제 True인 것 중에서 모델이 True라고 예측한 것의 비율이다.
- Recall = TP / (TP + FN) 
- 통계학에서는 sensitivity
- 다른 분야에서는 hit rate

## 정확도(Accuracy)
- True를 True라고 옳게 예측한 경우와 False를 False라고 옳게 예측한 것의 비율이다.
- Accuracy = (TP + TN) / (TP + FN + FP + TN)  

## 특이도 (Specificity)
- TNR(True Negative Rate)
- 실제로는 False일때 , False라고 예측한 것의 비율이다.
Specificity = TN / (TN + FP) 

## F1 score
- Precision과 Recall의 조화평균이다.
- 2 * (Precision X Recall) / (Precision + Recall)
- F1 스코어는 데이터 레이블이 불균형 구조일 때, 모델의 성능을 정확하게 평가할 수 있으며, 성능을 하나의 숫자로 표현할 수 있다.

## Fall-out
- FPR(False Positive Rate)로 불린다.
- 실제 False인 data 중에서 모델이 True라고 예측한 비율이다.
- Fall-out(FPR) = FP / (TN + FP)

출처 : 
- 혼동 행렬, 분류성능평가지표
https://data-alpha.tistory.com/22
- 나무위키
https://namu.wiki/w/%ED%98%BC%EB%8F%99%ED%96%89%EB%A0%AC
