## Information
![](../src/Pasted%20image%2020241221194219.png)

- Title: A Study on Emotion Recognition in Conversation Based on Multi-Dimensional CNN and Transfer Learning
- Author: Kihoon Lee, Namgyu Jung, Chang Choi
- Date: 13 December 2023
- Conference: The 12th International Conference on Smart Media & Applications

## 간단한 내용 정리
![](../src/Pasted%20image%2020241221194356.png)

- 실제 대화는 특정 감정에 치우쳐져 있는 불균형한 데이터이며, 같은 문장이어도 다른 감정을 갖는 문맥적 어려움이 존재한다.
- 불균형 데이터셋을 해결하기 위해 대부분 증대를 진행하나, 이는 대화의 흐름을 고려하지 않으며 특정 문장에 대해서만 학습하게 된다.
- 데이터 증대 없이 과거의 발화를 고려한 전이 학습(Transfer Learning) 및 1D CNN과 2D CNN의 앙상블 방안을 제안했다.
- 6개의 감정 데이터셋으로 미세조정된 Emotion DistilRoBERTa을 KEMDy20 데이터셋에 전이 학습하고 다차원 CNN을 통해 동시에 학습한 결과 기존 방안 대비 Macro F1 점수가 129.7% 향상하였다.
- 본 논문에서 제안하는 방안은 KEMDy20에서 83.135%의 정확도와 86.863%의 가중 F1 점수를 달성하며 기존 ERC 연구의 문제점을 개선할 수 있음을 검증하였다.
