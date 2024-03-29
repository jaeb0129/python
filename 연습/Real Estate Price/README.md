**💡 분석 목표**

- 평당 부동산 가격(단위: 100,000 대만 달러)을 예상
- 다형선형회귀모형의 성능 향상

| 목차                                                    | 내용                                                         |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [1. EDA](#1.-EDA)                                       | 대만 New Taipei시 Sindian 지역에서 수집한 주택 가격 자료             |
| [2. Linear regression](#2.-Market-Basket-Analysis) |     다중선형회귀모델                 |
| [3. 모델 성능 향상](#3.-Regression)                         | Ridge, Lasso 회귀 / GridSearchCV(Cross Validation) |

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

- 선형 모델(Linear model)의 예측력(accuracy) 혹은 설명력(interpretability)을 높이기 위해 여러 정규화(regularization) 방법들을 사용
- 모델 과적합 현상을 방지해 주는 방법 중 하나
- 과적합된 다중 선형 회귀 모델은 하나의 특이값에도 회귀선의 기울기가 급격하게 변할 수 있다
- 대표적인 shrinkage 방법에는 ridge regression과 lasso가 있음

![Regularization1](https://user-images.githubusercontent.com/63768509/226539662-66776568-81dd-455b-83fd-2431b1fa72c3.jpg)
![Regularization2](https://user-images.githubusercontent.com/63768509/226539716-d67e4923-500f-414b-a1de-efb6e0e3a4b7.jpg)
#### 출처: https://sanghyu.tistory.com/13

# Ridge regression
> 불가피하게 독립 변수들 사이에 높은 상관 관계가 있는 경우라면 리지 회귀가 더 적합한 접근방식이다.

> 다중 회귀라고도 불리는 리지 회귀는 정규화 또는 규제화(regularization) 기법으로 알려져 있으며 모델의 복잡성을 줄이는 데 사용된다.

> 또한 ‘리지 회귀 페널티’로 알려진 약간의 편향, 즉 바이어스(bias)를 사용하여 모델이 과대적합(overfitting)에 덜 취약하게 만든다.

<br>

![Ridge_regression](https://user-images.githubusercontent.com/63768509/226517935-f2a377bd-a4a1-4fa8-b80d-e518ddb85096.jpg)
#### 출처: https://modern-manual.tistory.com/21

# Lasso regression

> 라쏘 회귀는 리지 회귀와 같이 모델의 복잡성을 줄여주는 또 다른 정규화 기법이다.

> 회귀 계수의 절대 사이즈를 금지함으로써 복잡성을 줄인다. 리지 회귀와는 다르게 아예 계수 값을 0에 가깝게 만든다.

> 그 장점은 기능 선택을 사용할 수 있다는 것이다. 데이터 집합에서 기능 세트를 선택하여 모델을 구축할 수 있다.

> 라쏘 회귀는 필요한 요소들만 사용하고 나머지를 0으로 설정함으로써 과대적합을 방지할 수 있다.

## cross validation
Ridge regression 모형의 hyperparameter인 $\alpha$의 최적값을 선택하려면 cross-validation을 이용한다.
- 평가에 모든 데이터 이용 가능(편중 막음)
- ex) cv = 10, 10개의 평가 지표(data를 9train, 1test로 나눠 모델의 성능을 평가한 값)들을 평균내서 최종적으로 모델의 성능 평가
- 기존에 테스트셋을 하나로 고정했을 때보다 훨씬 더 안정적인 검증 방법

## GridSearchCV
- 사용자가 직접 모델의 하이퍼 파라미터의 값을 리스트로 입력하면 값에 대한 경우의 수마다 예측 성능을 측정 평가해 최적의 하이퍼 파라미터 값을 찾는 과정을 진행 
- 예측 성능 평가 시 교차 검증도 진행(CV)
- 튜닝하고 싶은 파라미터를 집어넣어 튜닝과 교차검증을 함께 진행할 수 있게 도와줍니다. 
- gridsearch는 확인하고 싶은 다양한 파라미터값을 넣어주면 그것들을 하나씩 확인하면서 스코어를 내고 가장 좋은 성능의 모델에 대한 결과를 확인하고 사용할 수 있습니다.

## GridSearchCV를 이용하여 Lasso에 대한 CV를 실시하고 최적의 Lasso 모형과 최적의 Ridge 모형을 비교
