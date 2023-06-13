---
title: InstructGPT 논문 리뷰 - 2 
author: amazingkmy
day: 2023.06.13
---

# InstructGPT 논문 리뷰 - 2
오늘은 운동하고 왔더니 많이 쓰진 못할꺼 같네요 ㅎㅎ
이전 글에서 썼던 대로 제가 작성한 부분에 있어서 잘못된 부분이 있다면 언제든지 연락주시면 감사하겠습니다.

---

## InstructGPT 학습 과정 다시 정리
InstructGPT 학습은 3가지로 구분할 수 있습니다
1. Supervised Fine-Tuning (SFT)
2. Reward Model Training
3. Reinforcement learning proximal policy optimization
![instructGPT-learning-preview]({{"/assets/img/post_img/instructGPT-learning-preview.png"|relative_url}})
여기에서 3번에 대한 내용이 조금 부실했던 것 같습니다
아무래도 PPO에 대한 설명이 부족했기 때문이라고 생각합니다. 이 내용에 대해서는 추후에 정리가 필요합니다. (TRPO vs PPO)
간단하게 표현하면 강화학습에 필요한 정책 알고리즘 중에 SOTA를 달성하고 있는 알고리즘이라고 보시면 되겠습니다.

---
## InstructGPT의 특징
#### 라벨링 작업자가 바라본 GPT3 vs InstructGPT
결론을 먼저 이야기하면 파라메터가 100배 작은 InstructGPT이지만, 좀 더 사람다운 결과를 내보냈다고 합니다.
똑같은 175B에서는 InstructGPT가 GPT3 보다 85% 정도 확률로 선호도를 가졌으며, GPT-3에 Few-shot을 적용해도 71%를 상회하는 선호도를 가졌다고 하네요

#### InstructGPT의 편향성
OpenAI팀에서는 [RealToxicityPrompts dataset](https://allenai.org/data/real-toxicity-prompts)을 이용하여 테스트를 진행하였더니 GPT-3에 비해 25%나 편향성이 감소되는 결과를 얻었다고 하네요.
다만, 사회 편향적인 데이터인 [CrowS-Pairs](https://paperswithcode.com/dataset/crows-pairs)와 젠더 편향 데이터인 [Winogender](https://github.com/rudinger/winogender-schemas)는 뚜렷한 결과를 못 얻었다고 합니다

#### InstructGPT의 NLP 성능 하락
소제목으로만 보면 NLP의 성능이 하락했다고 써져있어 말이 안되는 것으로 보이지만, 여기에서 말하는 NLP 성능은 현재 공개되어있는 NLP 데이터셋인 WMT2015, notably S
SQuAD 등을 말합니다.
이 논문에서는 사람이 교육했음에도 불구하고 성능이 하락한 원인을 "정렬을 학습함으로 인한 비용지불"이라고 하네요

#### 선호도 조사는 Training Data를 만들지 않은 작업자가 수행
선호도 조사를 해봤더니 InstructGPT를 더 선호했다.
하지만, Training Data를 만들지 않은 작업자가 선호했다는 이유만으로 일반화 할 수는 없다.

#### 일반적인 NLP 데이터셋은 InstructGPT 사용 방식을 참고하지 않음
이 부분은.. 잘 이해가 안가는 내용인데, 각각의 NLP Task에 대해 각 작업에 대한 지침으로 데이터를 만들었고, InstructGPT에 알맞게 prompt했더니 T0와 FLAN보다 73% 좋은 성능을 보였다고 합니다

오늘은 여기까지..