---
title: "pytorch optimizer란?"
date: 2022-08-04 00:00:00
categories: [AI]
tags: [pytorch] # TAG names should always be lowercase
---

(작성 중)

optimizer란.. 간단히 말해서 모델의 parameter를 **최적화**하는 함수이다.  
**최적화**를 하는 이유는, 각 학습 단계에서 **모델의 오류를 줄여 성능을 높이기 위함**이다.

optimizer는 다양한 종류가 있는데, 모델에 따라서 잘 맞는 다양한 optimizer가 있다.  
내가 사용한 optimzer는 ADAM이고, 아래는 optimizer를 초기화하는 코드이다.

```
optimizer = torch.optim.Adam(model.parameters(), lr=1e-4)
```

학습하려는 모델의 parameter와 hyperparameter인 learning rate를 등록해주었다.

각 학습 단계에서 최적화는 총 **3단계**로 이루어진다.

- **optimizer.zero_grad()** : parameter 변화도(gradient)를 **0**으로 재설정
- **loss.backwards()** : prediction loss를 역전파하고, loss의 **변화도를 저장**
- **optimizer.step()** : 저장한 변화도로 **parameter를 조정**

> reference: <https://tutorials.pytorch.kr/beginner/basics/optimization_tutorial.html>
