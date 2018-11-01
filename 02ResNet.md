# Deep Residual Learning for Image Recognition (2015)

### summary

- 이전 소개한 AlexNet(ImageNet Classification with Deep Convolutional Neural Networks)과 마찬가지로 ImageNet challenge에서 우수한 성적으로 두곽을 나타낸 image classifier다.
- AlexNet의 경우 두개의 GTX 580 3G를 사용하여 5~6일 가량 모델을 학습하였다.
- 많은 연산량을 요구하고, 오랜 학습시간이 deep neural network의 장점인데 ResNet의 경우 residual network를 사용함으로써 더 깊은 계층을 사용하더라도 더 높은 수렴속도와 정확도를 기록하였다.

1. Introduction

- ImageNet뿐만 아니라 이미지분류에서 deep neural network의 depth(layer)가 깊을어질수록 연산량도 많아지지만 gradient vanishing/exploding 의 문제를 초래할수 있다.
- ResNet의 핵심개념이 소개된다.
  - 기존의 CNN 방식에서 목표는 최적의 H(x)를 갖는 것이다. 하지만 f(x) = H(x) - x로 목표를 수정하면 연산은 F(x) + x 로 x를 추가하는 방식만 추가된다. 연산은 F(x)가 0이 되는 방향으로 학습을 하고, optimization이 쉽게 일어날수 있다.

