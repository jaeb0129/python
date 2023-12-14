# Decision Tree

![decision tree](https://user-images.githubusercontent.com/63768509/229148789-4ff7f53f-107a-4837-b6da-329bfed51eb3.jpg)

- 타원: root node, 네모: leaf node
- 초기 14개의 데이터를  5, 4, 5로 나눔

## 노드를 어떤 기준으로 나눌까?
> Decision Tree는 분리를 거듭해 변수를 구분하는 영역을 만드는 모델

- 순수도: 목표변수가 특정 범주에 속해 있는 정도
- 불순도: 목표변수가 특정 범주에 속하지 않은 정도
- 위에서 연간 소득으로 나눌 경우 yes 2개, no 3개가 섞여있지만 leaf node는 yes 2개, no 3개로 구성-> leaf node가 순수도 더 높음

### 1. 엔트로피
> 엔트로피가 높다는 것은 불순도가 높다는 것 의미(엔트로피를 낮게 만드는 것이 목적)


![엔트로피](https://user-images.githubusercontent.com/63768509/229152612-4db993ab-5890-4c8d-9f7e-a53d02227d83.jpg)


![엔트로피2](https://user-images.githubusercontent.com/63768509/229152939-3a2b572d-d2e4-497a-937c-666545777f33.jpg)

<br>

- 정보획득


![정보획득량](https://user-images.githubusercontent.com/63768509/229155037-1d9adcb1-8c19-4ea5-a703-7d4ecd30b7d0.jpg)


### 2. 지니 인덱스

![지니 인덱스](https://user-images.githubusercontent.com/63768509/229156167-9fc5a66f-df00-49a5-9bce-176388898772.jpg)


### 3. 학습 방법

![학습 방법](https://user-images.githubusercontent.com/63768509/229156010-04f9c26a-ea9c-485e-ab6c-47f089d08133.jpg)


### 4. 모델의 장단점
![모델의 장단점](https://user-images.githubusercontent.com/63768509/229156017-5660f9a9-57df-4da2-a7dc-e7dd7a94ba02.jpg)






출처: https://m.blog.naver.com/winddori2002/221652285241

# 시각화
- train+test data 569개를 7:3으로 나누고(train=398개) decision tree 시각화

![graph](https://github.com/jaeb0129/baseball/assets/63768509/f147f82f-25be-47ef-b8bc-a534bef0eb2c)

