AlexNet(ImageNet Classification with Deep Convolutional Neural Networks)
=== 
# Overall architecture

<img width="100%" src = "https://user-images.githubusercontent.com/98069142/245362459-aeed9b23-cb7a-45d9-a1f8-32001219e255.png"/>

* 6천만개의 parameters 65만개의 neurons를 가지며 5개의 Convolutional Layers와 3개의 Fully connected Layers로 총 8개의 레이어로 이루어져있음.
* 활성화 함수로 ReLu Function을 처음으로 사용한 architecture임.
* GPU 2대를 병렬로 사용함.
* Local response norm
* overlapping pooling
* data augmentation
* dropout

# Dataset
* 1000개의 이미지 카테고리.
* ILSVRC-2010 데이터를 주로 사용.
* 120만개의 train set, 5만개의 validation set, 15만개의 test set 사용.
* 이미지를 256x256 사이즈의 RGB 3채널 컬러 이미지로 통일 (256 x 256 x 3).
* 직사각형 사진의 경우, width와 height중 짧은 곳에 맞춰 256으로 rescale 후 가운데를 중심으로 256으로 자름.

 ### Reducing Overfitting_Data argumentaion
 * 좌우반전(horizontal reflection) 사용하여 이미지의 양을 2배로 증가
 * 256 x 256 이미지를 랜덤으로 잘라 224 x 224로 만들어 1024배 증가
 * (256 - 224) * (256 - 224) * 2 = 2048배 증가 1만장 -> 2천만장

 ### Reducing Overfitting_jittering
 * RGB 픽셀 값에 PCA를 통해 찾은 주요 성분들 만큼 랜덤하게 더해줌
 * 전체 이미지의 RGB 공분산에서 고유벡터, 고유값을 구함
 * 과대적합 되는 것을 방지

# The Architecture
1. ReLU Nonlinearity
2. Training on Multiple GPUs
3. Local Response Normalization
4. Overlapping Pooling

### ReLU Nonlinearity
<img height="50%" src="https://user-images.githubusercontent.com/98069142/245388186-0c8d2b67-2f8e-4e11-9b9f-8ce8aee47b52.png">

<img width="50%" src="https://user-images.githubusercontent.com/98069142/245394919-65974275-84b7-4b42-93ac-b64ffe6f791e.png">

더 빠르게 학습 됨

### Training on Multiple GPUs
* 1,2,4,5번째 convolution layer에서는 같은 GPU 내에서의 Kernel만 사용할 수 있음.
* 3번째 convolution layerdhk fc layer에서는 모든 Kernel을 사용할 수 있음.
### Local Response Normalization
<img width="50%" height="50%" src="https://user-images.githubusercontent.com/98069142/245368489-42db3f56-0f87-425f-b852-67c71b23fb0b.png">

* 실제 뇌세포의 증상으로, 강하 뉴런의 활성화가 근처 다른 뉴런의 활동을 억제시키는 현상으로 검은 사각형 사이에 회색 점이 보이는 현상에서 영감을 얻어 사용.
* 특정 값에 의해 과대적합 되는 것을 방지할 수 있음.

### Overlapping Pooling
* Pooling window의 크기 > stride의 크기
* 결국 Pooling window가 겹치게 됨.
* 과대적합 되는 것을 방지할 수 있음.
 
### DropOut
* 0.5의 확률로 hidden neuron의 값을 0으로 바꿔줌.
* 뉴런들 사이의 의존성을 낮추고, co-adaption을 피할 수 있음.
* 3개의 Fully-connected layer 중 앞의 2개에만 적용.