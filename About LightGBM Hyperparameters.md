# About LightBGM Hyperparameters

Reference: https://nurilee.com/lightgbm-definition-parameter-tuning/

## 1. Parameters

* `max_depth`: Tree의 최대 깊이. default는 -1이다.
모델이 overfitting되었다고 느낀다면 max-depth 값을 줄이자.

* `min_data_in_leaf`: Leaf가 가지고 있는 최소한의 레코드 수. default는 20으로 최적값이다.
과적합을 해결할 때 사용되는 파라미터.

* `feature fraction`: Boosting이 Random Forest일 경우 사용.
0.8 feature fraction이란 LGBM이 Tree를 만들 때 매번 각각의 iteration 반복에서 파라미터 중 80%를 랜덤하게 
