---
# Header
title: "Study Models!"
excerpt: "Study Models!"
name: J
writer: J
categories: [개념 정리] # [메인 카테고리, 서브 카테고리]
tags:
  - []

toc: true
toc_sticky: true

date: 2025-02-22
last_modified_at: 2024-02-22

# --- 아래 부터 content
---

# SGDClassifier

- 확률적 경사 하강법(Stochastic Gradient Decent:SGD)을 통해 SVM, logistic regression 등의 선형 분류기를 학습시킬 수 있는 분류기입니다.
- **결정 함수**를 이용하여 점수 계산 -> 점수가 임곗값보다 크면 샘플을 양성 클랫에 할당.

### 🔖SGD???

- Stochastic Gredient Decent: 확률적 경사 하강법의 약자로, 손실 함수의 기울기가 최소가 되게 하는 지점을 찾아내는 경사하강법의 한 방법이다.

### 🔖경사하강법?

- 비용 함수 f의 함숫값이 줄어드는 방향으로 함수의 계수를 일정 크기(학습량)만큼 더해나가며 f의 최솟값을 찾는 최적화 기법이다.

> 💡기울기 정의<br>
o 미분 가능한 N개의 다변수 함수 f를 각 축에 대하여 편미분한 값으로, 스칼라 함수의 모든 축에 대응하는 벡터장을 생성하는 역할을 한다

![alt text](/assets/img_20250311/image.png)

> 💡한계<br>
o 손실 함수가 조금만 복잡해져도 Global Minimum을 발견하지 못한 채 Local Minimum에 빠지기 쉽다.
o 학습 시간이 길다.

### ⭐확률적 경사하강법??

- 각 학습마다 모든 배치가 아닌 일부 샘플을 랜덤으로 선택하여 학습에 이용한다는 것이 '확률적'의 의미이다.
    - 학습 속도가 경사하강법에 비해 빠르지만 랜덤하게 선택된 데이터에 의해 노이즈가 발생할 수 있다.(why? 경사 하강법은 업데이트시 전체 Dataset 이용!)

### ⭐SGDClassifier?

확률적 경사하강법을 이용하는 선형 이진 분류기이다.

- loss=hinge, penalty='l2인 경우 규제가 있는 선형 SVM 분류기를 SGD 방식으로 학습시킨다.
- loss=log_loss인 경우 로지스틱 회귀 분류기가 선택된다.
- alpha는 규제의 강도를 설정한다.
- tol은 정밀도이며 None이 아닌 경우 loss>best_loss−tol일 때 학습을 종료한다.
- eta0은 초기 학습률이다.
- learning_rate는 학습 속도이다.

### 🔖규제?

> Ridge

- 모델의 손실 함수 최소화라는 목표에 추가로 가중치에 대한 목표를 만든다.
- 가중치의 절댓값을 최대한 작게 만드는 것을 목표로 한다. 이는 결국 기울기를 작게 만드는 것이다.
    - 각 가중치 제곱합에 규제 강도 α를 곱하여 오차에 더하는 것으로, l2 규제라고도 한다.

> Lasso

- Ridge 규제와 같이 가중치를 최소화하는 것을 목표로 한다.
- 가중치의 제곱합이 아닌 가중치의 합에 α를 곱하여 오차에 더하는 것으로 l1 규제라고도 한다.
    - l2 규제와는 다르게 어떤 가중치 w가 0이 될 수 있다. 즉 모델에서 완전히 제외되는 특성이 생길 수 있다.

> ElasticNet
- Lasso와 Ridge를 결합한 것으로, l1과 l2 규제의 비율을 설정해주어야 한다.