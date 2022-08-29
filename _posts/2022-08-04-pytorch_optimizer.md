---
title: "pytorch optimizer란?"
date: 2022-08-04 00:00:00
categories: [AI]
tags: [pytorch] # TAG names should always be lowercase
---

## PyTorch Optimizer

모델이 학습 단계에서 epoch를 거치면서 성능이 좋아지는 이유는 **모델의 parameters를 조절해 loss 값을 줄이기 때문**이다.
모델의 parameters에는 가중치(weight)와 편향(bias) 등이 있다.

> 가중치와 편향에 관한 글: <https://jh2021.tistory.com/3>{:target="\_blank"}

**loss**(손실)란 예측 값과 실제 값의 틀린 정도를 나타내는 수치로, 이것을 **최소화**하는 것이 학습 단계의 목적이다.

이때 필요한 것이 optimizer이다. pytorch에서 제공하는 optimizer는 모델의 loss 값을 줄이는 방향으로 parameters를 조절한다.

optimizer에는 다양한 종류가 있는데, 모델에 따라서 잘 맞는 optimizer가 존재한다.  
내가 사용해본 optimizer는 ADAM인데, 아래는 ADAM optimizer를 초기화하는 코드이다.

```
optimizer = torch.optim.Adam(model.parameters(), lr=1e-4)
```

학습하려는 모델의 parameters와 hyperparameter인 learning rate를 등록해주었다. 따로 넣어주지 않은 weight decay 등의 값은 기본 값으로 처리된다.

## 최적화 과정

각 학습 단계에서 최적화는 총 **3단계**로 이루어진다.

- **optimizer.zero_grad()** : parameter 변화도(gradient)를 **0**으로 초기화
- **loss.backwards()** : prediction loss를 역전파(반대 방향으로 loss를 돌려보냄)하고, loss의 **변화도를 저장**
- **optimizer.step()** : 저장한 변화도로 **parameters를 조정**

> reference: <https://pytorch.org/tutorials/beginner/basics/optimization_tutorial.html>{:target="\_blank"}
