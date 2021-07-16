# Dacon_NorthPole Project (Google Colab 써봄)
위성 영상을 활용한 북극 해빙 예측 AI 경진대회 \
Dacon BaseLine Code 가져옴

# 전처리
## Embedding
* ConvLSTM모델의 메모리를 고려하여 가로세로 32px씩 128x128 size로 crop
* 5년 단위로 Train Data 나눔
## 시각화
* 특정 월(Month)에서의 5년간의 변화와 그 다음 해의 모습을 보여주자
* Embedding하기 위해 crop한 Data에 대해서도 위와 같이 보여주자

# Data
## X_Data
* 해빙 농도(0~250), 북극점(위성 관측 불가 영역), 해안선 마스크, 육지 마스크, 결측값
## Y_Data
* 해빙 농도 예측 -> 1978년부터 관측된 북극 해빙의 변화를 이용하여 해빙 면적 변화 예측

# 학습 모델
## ConvLSTM(Conv3D, ConvLSTM2D, BatchNormalization, Optimizer=Adam)
* Keras.layers에 있음
* Conv3D에 대해 좀 알아봐야겠음

## Ensemble(TTS)
* 추론 결과 중복된 영역의 경우 평균을 이용해 앙상블
* Stride가 작을 수록 앙상블에 의해 결과가 좋아지나 일정값 이상으로 작아지면 추론시간이 급격히 우상향

# Acknowledgements

https://www.dacon.io/competitions/official/235706/overview/description
