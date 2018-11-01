# Deep Neural Networks for YouTube Recommendations (2016)

### Google AI에서 공개한 Deep learning을 이용한 Youtube 추천 시스탬

- Google AI에서 기존에 statistical model들을 deep learning으로 전환하는 일들을 하고 있다.
- 이중 youtube 추천시스탬을 deep learning으로 어떻게 활용하였는 가에 대한 논문이다.
- 논문에서는 핵심개념을 두가지로 요약한다; generation, ranking
    - generation : 수백만의 corpus중에서 사용자의 기록과 검색어를 바탕으로 수백개의 후보를 생산해 낸다.
    - ranking : 수백개의 후보중 다시 사용자의 기록과 검색어, 기타 요소를 활용해 expected watch time을 예측한다.

### 1. INTRODUCTION

- youtube의 경우 방대한 사용자와 컨탠츠를 가지고 있어서 아래의 3가지 문제점을 인지하고 해결하여야 한다.

    - scale : 
    - freshness : 
    - noise : 