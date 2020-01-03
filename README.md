# 인공지능 경진대회

## 기상데이터와 LSTM을 활용한 서울시 PM10 예측
미세먼지 심각성을 인지하고 바람데이터와 미세먼지 데이터를 LSTM을 활용해 미세먼지를 예측한다.

## 데이터 수집
17개 지역의 풍향, 풍속 데이터와 서울시 미세먼지 데이터를 수집

## 기상데이터와 미세먼지 상관관계
![image](https://user-images.githubusercontent.com/58103846/71713785-88764300-2e4e-11ea-8e85-d2648a1b6b91.png)

<17개의 지역의 기상데이터와 미세먼지간의 피어슨 상관관계분석>

분석 결과로 평균 풍속과 PM10농도는 평균 0.1이며, 최다풍향과 PM10농도는 0.13으로 양적 선형관계를 이루고 있음

## LSTM 모델
LSTM모델을 Tensorflow를 사용하여 설계
설계된 학습 모델은 Window 크기의 기상데이터와 미세먼지 농도를 입력으로 받고 Window 크기 다음 날의 미세먼지를 예측하는 2층으로 구성된 LSTM 사용

- 노드의 수 : 256로 구성
- 활성화 함수 : hyperbolic tangent 함수
- OVerfitting 방지하기 위해 Dropout 사용
- Xavier 방법으로 초기화
- 손실함수 : MAE 사용
- 최적화 알고리즘 : Adam 알고리즘
- Learning rate : 0.1

## 결과
![image](https://user-images.githubusercontent.com/58103846/71714180-23bbe800-2e50-11ea-9cae-68dc0093f120.png)

<전체 테스트 집합에 대한 미세먼지 예측 결과>

- MAE = 14.3
- MSE = 472.48
- RMSE = 21.73

![image](https://user-images.githubusercontent.com/58103846/71714187-333b3100-2e50-11ea-94a6-7cc8f1c9505f.png)

<Window 크기에 따른 학습 결과>

Window 크기를 2일로 했을 때 MAE가 14.34로 가장 좋은 성능을 기록, 학습 수렴 속도도 가장 빠름
