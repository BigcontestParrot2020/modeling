# modeling

## train_test_split대신 Cross Validation 이용

train_test_split을 이용할 경우 **train 데이터가 test 데이터에 포함되는 현상**을 우려
  - 예를 들어 상품 하나가 20분, 20분씩 총 40분 방영될 경우, train_test_split을 사용하여 전자를 train set, 후자를 validation set에 넣는다고 하면
  - 두 데이터는 앞타임에 방영되었는가 뒷타임에 방영되었는가를 제외하면 매우 유사한 특성을 갖게 되어버림

월별 Cross validation을 이용
  - 특히 예측하고자 하는 6월과 비슷한 시점인 5,7,8,9월을 주시 
