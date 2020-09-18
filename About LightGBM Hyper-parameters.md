# About LightBGM Hyper-parameters

Reference: https://nurilee.com/lightgbm-definition-parameter-tuning/

## 1. Learning Control Parameters

* `max_depth`: Tree의 최대 깊이. default는 -1(no limit)이다.
모델이 overfitting되었다고 느낀다면 max-depth 값을 줄이자.

* `min_data_in_leaf`: Leaf가 가지고 있는 최소한의 레코드 수. default는 20으로 최적값이다.
overfitting을 해결할 때 사용되는 파라미터.

* `feature_fraction`: Boosting이 Random Forest일 경우 사용.
0.8 feature fraction이란 LGBM이 Tree를 만들 때 매번 각각의 iteration 반복에서 파라미터 중 80%를 랜덤하게 선택하는 것을 의미한다.

* `bagging_fraction`: 매번 iteration을 돌 때 사용되는 데이터의 일부를 선택.
training 속도를 높이고 overfitting을 방지할 때 사용.

* `early_stopping_round`: validation loss가 early_stopping_round 가 지난 후에도 향상되지 않았다면 학습을 중단. 
지나친 iteration을 줄이는데 도움을 준다.

* `lambda`: regularization parameter. 일반적으로 0 에서 1 사이이다.

* `min_gain_to_split`: 분기하기 위해 필요한 최소한의 gain을 의미.
Tree에서 유용한 분기의 수를 컨트롤하는데 사용된다.

* `max_cat_group`: 카테고리 수가 클 때, 과적합을 방지하는 분기 포인트를 찾는다.
카테고리 그룹을 max_cat_group으로 합치고 그룹 경계선에서 분기 포인트를 찾는다.
default는 64 (?)

<br/>

## 2. Core Parameters

* `Task` : 데이터에 대해서 수행하고자 하는 임무를 구체화한다.
  - `train`: 훈련 \<default\>
  - `predict`: 예측

* `application`: 가장 중요한 파라미터로, 모델의 application을 정한다.
  - `regression`: 회귀분석 \<default\>
  - `binary`: 이진 분류
  - `multiclass`: 다중 분류

* `boosting`: 실행하고자 하는 알고리즘 타입을 정의.
  - `gdbt`: Traditional Gradient Boosting Decision Tree \<default\>
  - `rf`: Random Forest
  - `dart`: Dropouts meet Multiple Additive Regression Trees
  - `goss`: Gradient-based One-Side Sampling

*  `num_boost_round` : boosting iteration 수로 일반적으로 100 이상

* `learning_rate`: learning rate

* `num_leaves`: 전체 Tree의 leave 수. default는 31이다.

* `device`: default는 cpu이며, gpu로 변경 가능

<br/>

## 3. IO Parameters

* `max_bin`: feature 값의 최대 bin 수 (?)

* `categorical_feature`: 범주형 feature의 인덱스를 의미. 만약 categorical_features 가 0, 1, 2 이면 column 0, column 1, column 2 가 범주형 변수이다.

* `ignore_column`: 해당 변수들을 무시함

<br/>

## 4. Parameter Tuning

### 4.1 For Model Accuracy

* `num_leaves`: Tree 모델의 복잡성을 컨트롤하는 주요 파라미터. 이상적으로 num_leaves 값은 (max_depth)^2 값보다 적거나 같아야 한다. 이것보다 큰 값은 overfitting을 유발할 것이다.

* `min_data_in_leaf`: 큰 값으로 세팅하는 것은 Tree가 너무 깊게 확장되는 것을 막을 수 있지만 under-fitting이 발생할 수도 있다. 관행적으로 수백 또는 수천 개로 정하는 것이 큰 데이터 세트에 충분하다.

* `max_depth` : Tree 깊이를 명확하게 제한하기 위해 max_depth 값을 설정할 수도 있다.

<br/>

### 4.2 For Better Accuracy

* 큰 `max_bin` 값을 사용
* 작은 `learning_rate` 값을 큰 `num_iterations` 값과 함께 사용
* 큰 `num_leaves` 값을 사용
* `dart` 사용

<br/>

### 4.3 Deal with Over-fitting



