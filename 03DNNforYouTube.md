# Deep Neural Networks for YouTube Recommendations (2016)

### Google AI에서 공개한 Deep learning을 이용한 Youtube 추천 시스탬

- Google AI에서 기존에 statistical model들을 deep learning으로 전환하는 일들을 하고 있다.
- 이중 youtube 추천시스탬을 deep learning으로 어떻게 활용하였는 가에 대한 논문이다.
- 논문에서는 핵심개념을 두가지로 요약한다; generation, ranking
    - generation : 수백만의 corpus중에서 사용자의 기록과 검색어를 바탕으로 수백개의 후보를 생산해 낸다.
    - ranking : 수백개의 후보중 다시 사용자의 기록과 검색어, 기타 요소를 활용해 expected watch time을 예측한다.

### 1. INTRODUCTION

- youtube의 경우 방대한 사용자와 컨탠츠를 가지고 있어서 아래의 3가지 문제점을 인지하고 해결하여야 한다.

    - scale : 기존의 추천시스탬은 youtube의 특성상 문제해결하지 못하였다. 그래서 massive한 corpus를 처리하고, highly distributed system이 필요하였다.
    - freshness : 신규컨탠츠를 잘 수용하면서도, 기존의 모델이 exploration / exploitation 를 통해서 이해할수 있어야한다.
    - noise : 기존에는 feedback을 바탕으로 metadata를 정의하는데 robustic한 시스탬을 갖추지 못하였다.

- 앞서 언급하였듯이 Google AI에서 기존의 모델들을 deep learning를 활용하여 개선하고 있다. Youtube는 10억개의 parameter와  1000억개의 학습데이터를 사용하였다.
- 추천시스탬에는 item-based(matrix factorization), content-based에 deep auto-encoder와 deep neural network를 활용하고 있다. 해당 논문을 통해서 deep learning을 활용한 모델의 이점, 그리고 클릭기반의 ranking이 아니라 왜 expected watch time을 사용하였는지에 대해 다룬다.


### 2. SYSTEM OVERVIEW

- recommand system은 크게 두가지 구조로 나뉜다; candidate generation, ranking. 구조에 대한 설명은 아래에서 자세히 다루기에 넘어가겠다.
- Deep neural network를 학습하는데 offilne metric으로 recall, precision, loss등을 사용하였지만, 실제로는 A/B테스트를 통해 모델을 평가하였다.
- click-through rate, watch time등을 통한 A/B테스트의 성능개선이 있을때를 기준으로 모델을 평가하였다고 한다. 이는 Google Analytics에서 제공하는 지표들이므로 GA를 사용해 실제 UI/UX의 개선유무를 고민하였다고 추정된다.

### 3. CANDIDATE GENERATION

##### 3.1 Recommendation as Classification

- 



