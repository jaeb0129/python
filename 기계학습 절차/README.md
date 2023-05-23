## ## 기계 학습의 일반적인 절차

1. 훈련 자료와 테스트 자료로 분할: 비율, 난수 초기치
2. preprocessing: 정규화(normalization), 표준화(standardization) 등등
3. 후보 모형들을 선정, hyper-parameters
4. cross-validation: hyper-parameter의 검색범위를 지정
5. GridSearchCV ==> 최적 모형 탐색
6. 최적 모형의 성능을 테스트 자료로 평가
