# Kaggle competition을 통한 시계열 데이터 분류 모델 연구


## :fire: 프로젝트 목표 

시계열 데이터에 대한 전반적 특징을 이해하고, 
캐글 실습을 통해 시계열 분류에 사용되는 다양한 알고리즘을 비교하여
시계열 데이터에 가장 적합한 모델을 탐색.

## :memo: 시계열 데이터란 
: 어떤 현상에 대하여 *시간의 흐름에 따라 기록* 되어 미래의 변화에 대한 추세를 나타내는 데이터를 총칭.
시간의 흐름에 따라 *순차적으로 발생한 관측치의 집합*이며, 이때 발생한 연속적인 관측치는 서로 관련이 있다.


## :mag: Kaggle Introduction 

### Tabular Playground Series Apr 22

<aside>
📌 Welcome to the April edition of the 2022 Tabular Playground Series! This month's challenge is a *time series classification* problem.
You've been provided with thousands of sixty-second sequences of biological sensor data recorded from several hundred participants who could have been in either of two possible activity states. Can you determine what state a participant was in from the sensor data?

</aside>

**Descriptions**

- ***train.csv*** - the training set, comprising ~26,000 60-second recordings of thirteen biological sensors for almost one thousand experimental participants
    - `sequence` - a unique id for each sequence
    - `subject` - a unique id for the subject in the experiment
    - `step` - time step of the recording, in one second intervals
    - `sensor_00` - `sensor_12` - the value for each of the thirteen sensors at that time step
- ***train_labels.csv*** - the class label for each sequence.
    - `sequence` - the unique id for each sequence.
    - `state` - the state associated to each sequence. This is the target which you are trying to predict.
- ***test.csv*** - the test set. For each of the ~12,000 sequences, you should predict a value for that sequence's `state`.
- ***sample_submission.csv*** - a sample submission file in the correct format.

## :page_facing_up: Score List 

- Submit 0 (22.04.19) : score = ***0.500***
    - URL : [https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93447534](https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93447534) (ver 7)
    - 데이터 전처리나 FE 없이 LGBM 모델링 수행
- Submit 1 (22.04.19) : score = ***0.783***
    - URL : [https://www.kaggle.com/code/taehyeon0915/tpsapr22-eda?scriptVersionId=93416220](https://www.kaggle.com/code/taehyeon0915/tpsapr22-eda?scriptVersionId=93416220) (ver 16)
    - 각 sequence에 대한 센서별 통계치를 변수로 만들고 LGBM 모델링 수행
- Submit 2 (22.04.20) : score = ***0.799***
    - URL : [https://www.kaggle.com/code/seungeun5/tabular-apr-2022-ohse/edit/run/93460916](https://www.kaggle.com/code/seungeun5/tabular-apr-2022-ohse/edit/run/93460916) (ver 7)
    - 센서별 통계치에 diff 변수 추가하고 LGBM 모델링 수행
- Submit 3 (22.04.21) : score = ***0.760***
    - URL : [https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93645073](https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93645073) (ver 12)
    - 센서별 통계치에 diff 변수 추가하고 IQR이상치를 모두 **0으로 대체** 후 LGBM 모델링 수행
- Submit 4 (22.04.22) : score = ***0.755***
    - URL : [https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93688310](https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93688310) (ver 14)
    - 센서별 통계치에 diff 변수 추가하고 IQR이상치를 **상한값 또는 하한값으로 대체** 후 LGBM 모델링 수행
- Submit 5 (22.04.24) : score = ***0.79***
    - URL : [https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93811639](https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93811639)
    - submit 2에서 상관관계 높은 변수들 제거하고 이상치 처리 없이 LGBM 모델링 수행
- Submit 6 (22.04.25) : score = ***0.823***
    - URL : [https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93954569](https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22?scriptVersionId=93954569)
    - submit 5에서 `num_sequences` 변수 추가하고 LGBM 모델링 수행
- Submit 7 (22.04.25) : score = ***0.830***
    - URL : [https://www.kaggle.com/code/taehyeon0915/tabular-playground-apr-22-lstm](https://www.kaggle.com/code/taehyeon0915/tabular-playground-apr-22-lstm) (ver 21)
    - 앞의 모델에서 상관관계 높은 변수들 다시 살리고 LGBM모델링 수행
- Submit 8 (22.04.27) : score = ***0.934***
    - URL : [https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22-lstm?scriptVersionId=94115332](https://www.kaggle.com/code/jiwonkng/tabular-playground-apr-22-lstm?scriptVersionId=94115332) (ver 1)
    - submit 7에서 모델만 LSTM모델링 수행
- Submit 9 (22.04.28) :score = ***0.937***
    - URL: [https://www.kaggle.com/code/seungeun5/tabular-playground-apr-22-dd8159/edit/run/94058303](https://www.kaggle.com/code/seungeun5/tabular-playground-apr-22-dd8159/edit/run/94058303)
    - submit 8에서 lag 변수 추가
- Submit 10 (22.04.29) :score = *0.954*
    - URL: [https://www.kaggle.com/code/taehyeon0915/tabular-playground-apr-22-lstm](https://www.kaggle.com/code/taehyeon0915/tabular-playground-apr-22-lstm)
    - LSTM 모델 레이어 변경. raw feature 사용.


## Modeling :chart_with_upwards_trend:

다양한 머신러닝 / 딥러닝의 모델을 연구하고 시계열 데이터 예측에 맞는 모델을 선정.



## 📃 Reference  
- Permutation Feature Importance, 
: https://soohee410.github.io/iml_permutation_importance
- Sklearn Permutation Importance 를 사용한 Feature 중요도 파악
: https://wooono.tistory.com/328


