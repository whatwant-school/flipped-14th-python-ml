# Chapter.06 차원 축소 (Dimension Reduction)
매우 많은 피처로 구성된 다차원 데이터 세트의 차원을 축소해 새로운 차원의 데이터 세트를 생성하는 것

- 차원 증가 → 데이터 포인트 間 거리가 기하급수적으로 멀어짐 & 희소(Sparse)한 구조
- 수백 개 이상의 피처로 구성된 데이터 세트 → 상대적으로 적은 차원에서 학습된 모델보다 예측 신뢰도 낮음
- 피처 多 → 개별 피처 間 상관 관계가 높을 가능성 大 → 선형 모델에서 이로 인한 `다중 공선성 문제`로 모델 예측 성능 저하


## 차원 축소

- `피처 선택(feature selection, 특성 선택)` : 특정 피처에 종속성이 강한 불필요한 피처 제거 (= 데이터의 특징을 잘 나타내는 주요 피처만 선택)
- `피처 추출(feature extraction, 특성 추출)` : 기존 피처를 저차원의 중요 피처로 압축해서 추출 (= 이렇게 새롭게 추출된 중요 특성은 기존의 피처와는 완전히 다른 값)


## 대표적인 차원 축소 알고리즘

- PCA (Principal Component Analysis) : 가장 대표적인 차원 축소 기법
- LDA (Linear Discriminant Analysis) : 선형 판별 분석법. PCA와 매우 유사
- SVD (Singular Value Decomposition) : 행렬 분해 기법 이용. 정방행렬만 분해할 수 있는 PCA와 달리 행과 열이 다른 행렬에도 적용 가능
- NMF (Non-Negative Matrix Factorization) : Truncated SVD와 같이 낮은 랭크를 통한 행렬 근사 방식의 변형


---

## PCA (Principal Component Analysis)
여러 변수 간에 존재하는 상관관계를 이용해 이를 대표하는 주성분(Principal Component)을 추출해 차원을 축소하는 기법

- PCA로 차원을 축소할 때 기존 데이터의 정보 유실이 최소화 되도록...
- 이를 위해서 PCA는 가장 높은 분산을 갖는 데이터의 축을 찾아 이 축으로 차원을 축소 ← 이것이 PCA의 주성분
