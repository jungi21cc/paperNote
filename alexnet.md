### ImageNet Classification with Deep Convolutional Neural Networks (2012)

- 해당 논문은 ImageNet에서 획기적인 성적을 기록함으로써 딥러닝에 확신과 convolutional neural network가 이미지 처리에 대표주자가 되었다.
- ImageNet의 경우 약 120만개의 1000개의 자연 이미지분류 컨테스트로 인간과 기계간의 이미지 분류의 기준을 비교해볼수 있는 대회였다.
- 당시 37.5% 의 분류오차로 최고기록을 갱신하면서 data augmentation, dropout등의 overfitting을 방지하는 기법등이 소개되었다.
- 2012년을 기준으로 GPU를 사용하여 연산속도를 개선할수 있었고, 딥러닝 연구에 큰 영향을 주게된 논문이다.

1 Introduction & 2 The Dataset

- 앞서 소개한 바와 같이 ImageNet 대회는 약 120만개의 training data, 5만개의 validation data, 15만개의 test image로 분류된다. 
- 분류종류는 새, 자동차와 같은 자연이미지 1000개의 class를 분류한다.(1개의 class당 1000장의 이미지로 학습하고, 150개의 이미지로 평가한다)
- 이미지는 대략 469x387x3의 이미지로 구성되어 있다.
- 해당 논문에서는 neural network에 고정된 규격인 256x256x3의 down-sampled image로 사용하였다.

3 The Architecture

- 해당논문에서는 non-linearlity상태를 만들기 위한 Rectified Linear Units(ReLUs)을 채택하였다.
- 기존의 tahn units대비 gradient descent연산시 속도, epoch에 따른 training error rate의 감소의 효과를 볼수 있었다.
- 2012년당시 단일 GTX 580 3G GPU로 메모리 부족현상 때문에 병렬처리된 2개의 GPU를 사용하였다.
- 속도면에서는 단일 GPU대비 2개의 병렬처리된 GPU가 약간의 성능개선을 보여주었다.
- ReLUs의 경우 normalization을 요구하지 않지만, normalization사용시 error rate이 줄어들어 ReLUs를 통과하고 나서 normalization 해주었다.
- overlapping pooling
- 전체적인 architecture를 살펴보면 아래와 같다
    - 아래에서 256x256x3의 고정된 이미지를 224x224x3의 data augmentation시켜준 이미지가 input이된다.
    - 224x224x3의 이미지를 96개의 11x11x3의 4 stride를 가지는 kernel에 투과시켜준다.
    - 55x55x96의 out을 다시 두번째 convolutional layer(256개의 5x5x48의 커널)에 normalization과 max pooling을 이용해 투과시켜 준다.
    - 27x27x256의 out을 3x3x256의 커널에 통과시켜 13x13x384의 output을 얻는다.
    - 마지막으로 이전에 얻은 output을 384개의 3x3x192의 커널에 통과시켜 준다.
    - 이후 4096의 뉴런을 가지는 fully conected layer에 통과시켜 준다.
    - 마지막 output layer에 1000개의 class를 출력해 내는 softmax를 통과해서 최종 결과를 얻는다.
    
4 Reducing Overfitting

- overfitting을 방지하기 위해 256x256x3의 이미지를 224x224x3의 랜덤패치를 이용해 추출해 낸다.
- 또한 RGB값에 PCA를 이용해 1%가량의 error rate를 줄일수 있었다.
- fully connected layer에 drop-out기법을 사용하였다.
- 말그대로 4096개의 뉴런중 0.5의 확률로 임의로 결과를 버린다.
- 이를 통해 현재(2018)에는 표준화 되었지만 상당히 overfitting을 방지할수 있게 되었다.



