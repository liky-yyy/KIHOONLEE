## Information
- Tittle: **Use all tokens method to improve semantic relationship learning**
- Author: **Kihoon Lee, Gyuho Choi, Chang Choi**
- Date: **15 December 2023**(Available online 30 June 2023)
- Publisher: **Elsevier**
- Journal: **Expert Systems with Applications**
- Impact Vector: **8.5 (Top 6.4%)**
- Received 27 February 2023;
  Received in revised form 1 May 2023;
  Accepted 24 June 2023
- Link: 

- BERT 기반의 언어모델은 입력 문장의 정보를 함축하는 CLS 토큰을 사용하여 분류를 진행한다.
- CLS 토큰은 attention 메커니즘을 통해 입력 문장의 정보를 간접적으로 습득하기 때문에 전체 문장을 대표함을 가정한다.
- 단일 토큰 추론을 사용하는 추론 방안은 각 단어 간의 close connection 정보를 가지고 있는 나머지 hidden state vector를 사용하지 않으므로 의미론적 관계를 추론하는데 한계가 있으며, 언어모델의 지식을 완전히 활용하지 못하는 방안이다.
![fig1](src/Pasted%20image%2020241221190126.png)
- 단일 token을 통한 추론 방안을 개선하기 위해 사용하지 않던 token을 조합하여 사용하는 Use All Tokens(UAT) 방안을 제안한다.
- UAT 방안은 입력 토큰들의 관계 정보를 직접적으로 가지고 있는 최종 계층의 벡터값들을 조합하여 학습 및 추론하는 방안이다.
- UAT 방안은 hidden state vectors를 효과적으로 조합하며 문장의 글로벌한 정보와 단어 간의 로컬한 정보를 앙상블한다.
- 본 방안은 NLI(자연어추론) 작업에서 기존 방안 대비 높은 성능을 보이며 효과를 검증했다.

![](src/Pasted%20image%2020241221190143.png)
![](src/Pasted%20image%2020241221190149.png)
