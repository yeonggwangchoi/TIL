# Image file
## Grayscale
* 0 ~ 255까지의 픽셀값으로 표현된 영상
## RGB
* Red, Green, Blue의 채널
* 각 채널마다 0 ~ 255까지의 픽셀값으로 표현된 영상

# Image Fliters and Convolution
## Image Fliters
* 여러 수식을 이용하여 이미지를 이루고 있는 펙셀 행렬을 다른 값으로 바꾸어 이미지를 변형
### Sharpen filter
* 영상에서 사물의 윤곽이 뚜렷하고 선명하게 하는 필터
### Blur filter
* 기존 영상을 흐리게 하는 필터

## Convolution
* 공간 영역 필터링을 위한 핵심 연산 방법
* 공간 영역 필터링은 연산 대상 픽셀과 그 주변 픽셀들을 활용하여 새로운 픽셀 값을 얻는 방법
* 연산범위와 연산 방법은 커널(kernel) 또는 윈도(window), 필터(filter), 마스크(mask)등으로 불리는 행렬을 사용하여 진행
* 일대일로 대응하는 위치에 있는 커널의 요소와 대응하는 입력 픽셀 값을 곱한 후, 모두 더해서 결과 픽셀 값을 결정 하고 이런 연산을 마지막 픽셀까지 반복하는 것을 Convolution 연산이라 함
### Padding
* 이미지 데이터가 컨벌루션 연산을 통해 축소되는 것을 막기 위해
* edge pixel data를 충분히 활용하기 위해
### Stride
* 컨벌루션 연산은 한 칸씩 옆으로 이동하는데 Stride를 지정하면 몇 칸씩 이동할지 지정할 수 있다.
