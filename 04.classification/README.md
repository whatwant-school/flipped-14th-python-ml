## Chapter04. Classification (분류)
2021.01.28
- `결정 트리`와 `앙상블`이 주로 사용됨



## 결정 트리
- graphviz 책에서는 설치해야하지만, sklearn에 있는 것을 사용할 수 있음

### 지니 (gini)
- 책마다 조금 다른 설명임
- 엔트로피와 비교됨
- 엔트로피가 조금 더 좋음

### 과적합
- max_depth 제한을 두지 않으면, 과적합이 될 수 있음
- min_samples_split, max_features에 의해서도 과적합이 될 수 있음


## 앙상블 (Ensemble)

여러 분류기(Classifier)의 예측 결과를 종합해서 결정하는 아이

- 결정트리의 앙상블 = 랜덤포레스트
- Voting / Bagging / Boosting 3가지 분류가 대표적
  - Voting : 다른 분류기
  - Bagging : 같은 분류기
  - Boosting : 여러 분류기를 순차적으로
  - Stacking : 분류기 결과를 다시 학습


### 보팅 (Voting)

- 하드보팅 = 다수결
- 소프트보팅 = 확률


### 배깅 (Bagging)

- 결과 처리는 보팅 방식


### 랜덤 포레스트

- 배깅의 특수한 형태


## GBM (Gradient Boosting Machine)

잘못 예측한 결과에 가중치 부여

### 경사하강법
- 가중치 부여할 때 경사하강법 사용

### 에이다부스트
- 잘못 예측한 결과에 가중치 부여하는 대표적인 알고리즘


## XGBoost (eXtra Gradient Boost)

트리 기반 앙상블 학습의 일종. GBM 기반.

- 파이썬 래퍼 XGBoost
- 사이킷런 래퍼 XGBoost


### 파이썬 래퍼 XGBoost
GBM과 유사하지만, 조기 중단(early stopping) & 과적합 규제를 위한 하이퍼 파라미터 등이 추가됨
