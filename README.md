# Kaggle competition을 통한 시계열 데이터 분류 모델 연구


## 프로젝트 목표 :fire:

시계열 데이터에 대한 전반적 특징을 이해하고, 
캐글 실습을 통해 시계열 분류에 사용되는 다양한 알고리즘을 비교하여
시계열 데이터에 가장 적합한 모델을 탐색.

## 시계열 데이터란 :memo:
: 어떤 현상에 대하여 *시간의 흐름에 따라 기록* 되어 미래의 변화에 대한 추세를 나타내는 데이터를 총칭.
시간의 흐름에 따라 *순차적으로 발생한 관측치의 집합*이며, 이때 발생한 연속적인 관측치는 서로 관련이 있다.


## Kaggle Introduction :mag:

<H1>Tabular Playground Series Apr 22</H1>

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


## Modeling :chart_with_upwards_trend:

다양한 머신러닝 / 딥러닝의 모델을 연구하고 시계열 데이터 예측에 맞는 모델을 선정.
