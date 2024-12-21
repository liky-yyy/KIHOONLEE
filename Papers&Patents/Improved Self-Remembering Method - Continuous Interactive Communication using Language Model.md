![](../src/Pasted%20image%2020241221193907.png)

## Information
- Tittle: Improved Self-Remembering Method: Continuous Interactive Communication using Language Model
- Author: Kihoon Lee, Chang Choi
- Date: None  
- Publisher: IEEE
- Journal: Transactions on Neural Networks and Learning Systems
- Impact Vector: 10.4
- Status: Under Review
- Submitted: 05-Oct-2023

## 간단한 내용 정리
![](../src/Pasted%20image%2020241221194118.png)
- LLM은 현재 입력 문장에 대해 인간 수준의 뛰어난 분석을 수행할 수 있는 수준에 도달했다.
- 그러나 LLM은 "기억"하는 방안이 없기 때문에 이전 대화를 유지할 수 없다.
- 이를 해결하기 위해 많은 서비스와 연구에서 과거의 입출력 내용을 현재 입력에 추가하는 방안을 채택하고 있다.
- 이러한 방안은 대규모 자원을 필요로 하며, 컴퓨팅 자원 손실 및 탄소 배출에 크게 기여한다.

![](../src/Pasted%20image%2020241221194128.png)

- LLM이 이전의 입력 정보를 효율적으로 유지할 수 있도록 "Self-remembering method"를 제안한다.
- 본 방안은 과거의 입력에 대해 학습된 과거 토큰을 현재의 입력에 재사용하는 방안이며, 이를 통해 언어모델이 모든 대화 내용을 고려하도록 만든다.
- 본 방안은 하나의 토큰만을 사용하기 때문에 매우 적은 자원을 사용하며, 인간-컴퓨터 상호 작용 연구에 기여할 수 있는 상당한 잠재력을 가지고 있다.
- DeBERTa-v3를 백본으로 Emotion Recognition in Conversation 작업에서 실험을 진행한 결과 SOTA를 달성하며 효과성을 검증하였다.


