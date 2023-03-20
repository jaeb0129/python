**💡 분석 목표**

- 평당 부동산 가격(단위: 100,000 대만 달러)을 예상
- 다형선형회귀모형의 성능 향상

| 목차                                                    | 내용                                                         |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [1. EDA](#1.-EDA)                                       | 대만 New Taipei시 Sindian 지역에서 수집한 주택 가격 자료             |
| [2. Linear regression](#2.-Market-Basket-Analysis) |     다중선형회귀모델                 |
| [3. 모델 성능 향상](#3.-Regression)                         | Ridge, Lasso 회귀 / cross-validation, GridSearchCV |

<br>

## 1. EDA

## Data 설명
---

대만 New Taipei시 Sindian 지역에서 수집한 주택 가격 자료이다.

- 총 414개의 관측치, 8개의 변수
- 결측치 없음

|칼럼명 | 설명|
|:---|:---|
| No | 일련 번호 |
| X1 transaction date | 거래 날짜(예: 2013.250 = 2013 March, 2013.500 = 2013 June, etc.) |
| X2 house age | 주택 연령(단위: 연) |
| X3 distance to the nearest MRT station | 가장 가까운 지하철 역까지의 거리(단위: 미터) |
| X4 number of convenience stores | 생활권 내에 위치한 편의점 수 |
| X5 latitude | 위도(부동산의 위치) |
| X6 longitude | 경도(부동산의 위치) |
| Y house price of unit area | 평당 부동산 가격(단위: 100,000 대만 달러) |


## 2. Linear Regression

평당 부동산 가격(단위: 100,000 대만 달러)을 예상하기 위해 다중선형회귀모델 사용

## 3. 모델 성능 향상

선형 모델(Linear model)의 예측력(accuracy) 혹은 설명력(interpretability)을 높이기 위해 여러 정규화(regularization) 방법들을 사용
대표적인 shrinkage 방법에는 ridge regression과 lasso가 있음

# Ridge regression
![1](README.assets/Ridge_regression.JPG)
### 출처: https://modern-manual.tistory.com/21

# Lasso

## cross validation
Ridge regression 모형의 hyperparameter인 $\alpha$의 최적값을 선택하려면 cross-validation을 이용한다.
RidgeCV는 지정된 여러 $\alpha$ 중에서 최적의 것을 CV로 찾아주는 일을 함.

LassoCV 역시 진행

## GridSearchCV란 머신러닝에서 모델의 성능향상을 위해 쓰이는 기법.
사용자가 직접 모델의 하이퍼 파라미터의 값을 리스트로 입력하면 값에 대한 경우의 수마다 예측 성능을 측정 평가하여 비교하면서 최적의 하이퍼 파라미터 값을 찾는 과정을 진행 

## GridSearchCV를 이용하여 Lasso에 대한 CV를 실시하고 최적의 Lasso 모형과 최적의 Ridge 모형을 비교
