1. 로지스틱 회귀와 SVM의 차이를 얘기해달라

### SVM
- 2개 이상으로 나누어진 집단을 분류하는데 사용되는 머신러닝 기법
- 분류 알고리즘 중에서 가장 정확도가 높은 것 중 하나이다.
- 이상치의 영향도 적게 받는 것으로 알려져있다.
- 기본 방법은 데이터를 나누는 최적의 경계를 나누는 방식이다. 
 
2. strafitied data면 어떻게 대응할 것인가?

- strafitied data일 경우 strafitied k fold를 통해 불균형한 데이터 셋의 분포를 먼저 고려한 뒤 이 분포와 동일하게 학습과 검증 데이터 세트를 분배
 
3. 정규화가 무엇인가? 왜 하는가?

> 세단어 모두 정규화로 번역됨. 차이 알아두자.

### Normalization
- 값의 범위(scale)를 0~1 사이의 값으로 바꾸는 것
- 학습 전에 scaling하는 것
- 머신러닝에서 scale이 큰 feature의 영향이 비대해지는 것을 방지
- 딥러닝에서 Local Minima에 빠질 위험 감소(학습 속도 향상)
- scikit-learn에서 MinMaxScaler

### Standardization
- 값의 범위(scale)를 평균 0, 분산 1이 되도록 변환
- 학습 전에 scaling하는 것
- 머신러닝에서 scale이 큰 feature의 영향이 비대해지는 것을 방지
- 딥러닝에서 Local Minima에 빠질 위험 감소(학습 속도 향상)
- 정규분포를 표준정규분포로 변환하는 것과 같음
- Z-score(표준 점수)
- -1 ~ 1 사이에 68%가 있고, -2 ~ 2 사이에 95%가 있고, -3 ~ 3 사이에 99%가 있음
- -3 ~ 3의 범위를 벗어나면 outlier일 확률이 높음
- 표준화로 번역하기도 함
- scikit-learn에서 StandardScaler

### Regularization
- weight를 조정하는데 규제(제약)를 거는 기법
- Overfitting을 막기위해 사용함
- L1 regularization, L2 regularizaion 등의 종류가 있음
- L1: LASSO(라쏘)
- L2: Lidge(릿지)

4. 데이터 스케일링이 무엇인가? 왜 하는가?
- 데이터의 값의 범위를 조정하는 것으로 머신러닝에서 scale이 큰 feature의 영향이 비대해지는 것을 방지


5. EDA가 무엇인가? 어떻게 했는지 경험을 알려달라
### EDA(Exploratory Data Analysis, 탐색적 데이터 분석)
> 데이터의 특성과 패턴을 탐색해 이를 시각화 및 요약하는 과정
- EDA 수행을 통해 데이터 직관적인 이해를 얻을 수 있고, 데이터 분석에 대한 결정을 내리는데 도움
- EDA는 데이터의 특성 파악, 모델링 전략 결정, 결측값 처리, 이상치 탐지, 데이터 시각화, 문제 해결에 중요

6. 딥러닝이 항상 좋은가? 언제 쓰고 언제 쓰지 말아야 할까?
> 첫째, 데이터의 종류, 개수, 레이블링 등을 살펴봐야 한다.

> 둘째, 얼마나 많은 자원(GPU) 사용할 수 있는지?

> 셋째, 목표 달성을 위해서 고도화된 알고리즘이 굳이 필요한지?

- 패턴인식 기술, 고전적인 머신러닝 기술로 주자장 자동차번호인식, 백화점 등 점포 입구에서 코로나 발열 체크 기계에서 내 얼굴이 어디에 있는지 찾는 것 등 간단한 문제를 풀고자 할 때, 키와 몸무게로 BMI 계산하는 문제에는 굳이 사용할 필요 없음.
- 딥러닝의 특징은 엄청난 수의 데이터를 이용하여 학습하고, 모델의 성능을 극한치까지 끌어올리데 있다. 일상에서 손에 꼽는 적은 데이터, 적은 레이블을 가지고 있다면, 딥러닝 학습하는 것 자체가 이상하게 들릴 수 있다.

7. 배깅과 부스팅의 차이?
- 사진출처: https://bigdaheta.tistory.com/32
 > 앙상블 기법에는 투표(Voting), 배깅(Bagging), 부스팅(Boosting)이 있다.
 
 > 앙상블이란? 수많은 모델들을 만들고 이 모델들의 예측을 합쳐서 종합적인 예측하는 기법
 
- 배깅: 원 표본에서 중복을 허용하여 표본을 복원 추출하는 방법으로, 학습 데이터 셋을 여러개 만들 수 있고 각 셋은 다르다.
![2](https://github.com/jaeb0129/baseball/assets/63768509/47ddf85e-bcec-40a8-a92c-3802f4ff1de3)
- 부스팅: 전체 훈련 세트에서 랜덤하게 샘플을 추출하고 잘못 분류된 데이터에 가중치를 적용하는 방법. 즉 추출된 데이터로 하나의 트리를 만들고, 이때의 오차를 계산하여 그 오차가 적어지도록 가중치(중요도를 더주어 개선)를 주어 다음 모델을 만들 때 그것을 반영하는 방법. 이렇게 이전에 만들었던 트리의 오차를 개선해 다음 모델을 만들어 투표, 배깅 방법보다는 성능이 비교적 좋다는 특징이 있다.
- AdaBoost, Gradeint Boost, xgBoost, LightBoost 등 존재

![3](https://github.com/jaeb0129/baseball/assets/63768509/bda7955b-c6ec-4c77-92ca-f52febd3a950)

- 투표

![1](https://github.com/jaeb0129/baseball/assets/63768509/ef9c8bb7-e0c4-4089-bdff-95188c0c5472)

![1](https://github.com/jaeb0129/python/assets/63768509/71bcc09d-ea16-4314-bc8b-ea05395ba538)

- 보통 hard voting보다 soft voting이 성능이 좋아 soft voting 더 많이 사용
- 출처: https://blog.naver.com/fbfbf1/222484365132

![2](https://github.com/jaeb0129/python/assets/63768509/df4411f4-f352-4dfa-aebb-f3412dfe1648)

- 출처: https://tyami.github.io/machine%20learning/ensemble-1-basics/


8. Why is OLS the Best Linear Unbiased Estimator and when does it break down?

9. In what context do you prefer MLE?



머신러닝이 아니라 통계에 기반한 모델링을 하다보면 

OLS와 MLE를 써서 parameter들을 추정하는 경우가 많은데,

둘의 차이를 명확하게 알아야 할 듯.
