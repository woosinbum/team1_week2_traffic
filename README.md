# week2-traffic
## 순위
3등
<img width="642" alt="캡처" src="https://user-images.githubusercontent.com/82801470/156574834-2afe8f5b-d3f7-435a-883a-f8465b6a53ef.PNG">

## 특정기간의 도로 데이터를 바탕으로 7주일간의 도로교통량 예측
시계열 데이터에서 LSTM이 기존 RNN의 gradient vanishing 문제를 해결하고 교과서적인 모델이라고 배워서 
LSTM으로 해당 문제를 해결해보려고 노력해보았습니다. 처음 데이터를 받았을 때 결측값들이 있어서 그것을 해결해보고자
시간별이 아닌 하루치 데이터로도 학습시켜보고 도로의 특성을 모델이 모르고 있을 수도 있다는 카이스트 튜터님의 말에
도로별 특성을 kmeans cluastering으로 cluster도 하여 LSTM모델에 돌려보았지만 어떻게 하든 LSTM 모델은 성능이 나오지 않았습니다.
## 파일
clustering 파일은 도로별 데이터 분류를 위해 작성한 코드입니다 /n
traffic_per_day 파일은 시간별 교통량이 아닌 하루치 교통량을 예측해보기 위해 작성한 코드입니다 /n
traffic_baseline_cluster 파일은 클러스터를 적용한 데이터 학습을 위해 작성한 코드입니다 /n
darts_tft_model 은 darts라이브러리에서 tft모델을 사용해보기 위한 코드입니다. /n
team1_nbeats 파일은 최종적으로 팀이 제출한 코드입니다.
## 모델

팀원분들과 회의를 했을 때 공통적으로 LSTM모델은 성능이 잘 나오지 않는다는 의견이 있었고 prophet이나 darts의 다른모델을 썼을 때
성능이 증가한 다는 팀원분들의 의견을 듣고 darts 사이트에서 trasformer 기반의 모델인 tft모델을 사용해보려고 하였습니다.
트랜스포머 기반 모델을 선택한 이유는 트랜스포머가 비교적 최근에 나온 모델이라는 단순한 이유에서였습니다.
tft 모델을 사용하기 위해서는 future covariates라는 값을 넣어주어야 하는데 이 것은 미래의 예측하고자 하는 구간의 분산값을 가져와서 예측을 돕는데
사용하는 것 같았습니다. 하지만 futture covariates를 예측해주는 코드를 작성하지 못하여 test data를 예측하는데에는 쓰지 못했지만 학습과정에서 val_loss값이 상당히 낮게 나오는 것으로 보아 성능이 괜찮은 것 같다는 생각을 했습니다.
