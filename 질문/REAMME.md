1. 로지스틱 회귀와 SVM의 차이를 얘기해달라

### SVM
- 2개 이상으로 나누어진 집단을 분류하는데 사용되는 머신러닝 기법
- 분류 알고리즘 중에서 가장 정확도가 높은 것 중 하나이다.
- 이상치의 영향도 적게 받는 것으로 알려져있다.
- 기본 방법은 데이터를 나누는 최적의 경계를 나누는 방식이다. 
 
2. strafitied data면 어떻게 대응할 것인가?

- strafitied data일 경우 strafitied k fold를 통해 불균형한 데이터 셋의 분포를 먼저 고려한 뒤 이 분포와 동일하게 학습과 검증 데이터 세트를 분배
 
3. 정규화가 무엇인가? 왜 하는가?

- 세단어 모두 정규화로 번역됨. 차이 알아두자.
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

5. MCMC가 무엇인가?

6. EDA가 무엇인가? 어떻게 했는지 경험을 알려달라

7. 딥러닝이 항상 좋은가? 언제 쓰고 언제 쓰지 말아야 할까?

8. 배깅과 부스팅의 차이?

9. Why is OLS the Best Linear Unbiased Estimator and when does it break down?

10. In what context do you prefer MLE?



머신러닝이 아니라 통계에 기반한 모델링을 하다보면 

OLS와 MLE를 써서 parameter들을 추정하는 경우가 많은데,

둘의 차이를 명확하게 알아야 할 듯.
