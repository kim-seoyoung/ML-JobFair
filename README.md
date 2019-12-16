# ML-JobFair
### Programmers' Machine Learning Job Fair Task
#### trials

1. 2019-12-04
	- VGGNet + SGD : 87.75점
		- training epoch 수를 늘려도 과적합 될 뿐, val accuracy 높아지지 않음 
		- adam optimization 사용시 accuracy 40%대의 local minimum에서 벗어나지 못함 

2. 2019-12-06
	- VGG + SGD + dropout 
		- 과적합을 방지하는 방법으로 Dropout 사용
		- 모든 Dense layer에 dropout 적용시 잘 학습이 되지 않아  dropout 수와 비율을 줄임
	- VGG+SGD+dropout+BNorm : 87.75 점 
		- CNN layer에 BatchNormalization 적용해 봄 
	- face_detect+SGD

3. 2019-12-09
	- face_detect+Adam : 87점
		- VGG와 유사한 과적합 형태를 보임
	- augmentation (1)
		- train data를 10배로 augmentation
		- zoom, brightness 사용
	- face_detect+Adam+aug10 : 87.75점
		-  validation loss 및 accuracy가 train보다 높게 나옴
		- dropout을 많이 하면 이런 현상이 나타날 수 있다고 함(구글링이라 근거는 잘 모르겠다...)

4. 2019-12-10
	- face_detect+SGD+aug10
		-  validation loss 및 accuracy가 train보다 높게 나옴
	- VGG+SGD+aug10: 86.5 점
		- 초반엔 val accuracy가 높지만 점점 train보다 낮아
		-  정확도는 trai, validation 모두 90이상으로 올라가지만 test data 넣으면 높은 점수가 나오지 않음
	- augmentation (2)
		- 9,10일의 모델들이 전반적으로 accuracy가 높고 validation accuracy가 높은 것이 augmentation을 하면서 유사한 data가 많아졌기 때문이라고 생각해 augmentation 개수를 줄임 

5. 2019-12-11
	- VGG+SGD+dropout+aug3: 86.5 점
		-  학습을 많이 시켜서 매우 높은 train accuracy를 얻었지만 validation accuracy와 차이 매우 과적합되었음을 알 수 있음
		- 많은 epoch 수가 필요하진 않은 것 같음 
		- validation accuracy가 train accuracy보다 낮음
	- face_detect+adam+aug3: 86.5점
		-  이전만큼은 아니지만 90%정도의 높은 accuracy 나옴
		- validation loss가 train loss보다 낮음
	- VGG+adam+aug3: 85.5점

	- arrun+SGD+dropout: 86.75점
		-  validation accuracy와 train accuracy사이의 차이가 작고, 90%정도 이지만 점수는 낮게 나
	- arrun+adam: 87점
		- augmentation이 학습에 큰 영향을 미치지 않는다고 생각해 하지 않기로 함
		- validation accuracy의 fluctuation이 커짐
		- regularization이 부족한 것이 이유라고 함
	- arrun+adam+0.5
		- Dense layer 크기 반으로 줄임
		- fluctuation 심해짐

6. 2019-12-13
	- data_preprocessing: data에 분류가 잘 되지 않은 부분이 있어 train_vision.csv 수정함

7. 2019-12-15
	- ResNet50+SGD: adma, SGD 모두 해보았지만 0.85 이상의 정확도 얻지 못함
	
8.2019-12-16
	- ResNet18+SGD: adma, SGD 모두 해보았지만 너무 train과 validation의 차이가 큼(과적합), ResNet18의 세부적인 구조는 그냥 output크기를 보고 적당히 맞춤.......
	
