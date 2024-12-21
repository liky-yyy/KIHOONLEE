## Information
- 영문제목: Research on Efficient Modality Fusion for Enhanced Uni-modal Ensemble
- 국문제목: 향상된 단일모달 앙상블을 위한 효율적인 모달리티 결합에 관한 연구
- Link:  https://www.riss.kr/link?id=T16946098
- 발표자료: [PDF](../src/Research%20on%20Efficient%20Modality%20Fusion%20for%20Enhanced%20Uni-modal%20Ensemble-presentation.pdf)

## 다국어 초록
Recently, research on multi-modal learning, which can comprehensively learn from various data types, is being actively conducted. While the latest pre-trained large multi-modal models show high performance in many tasks, they require many resources, limiting their use in general situations. The ensemble of uni-modal networks is essential to perform practical multi-modal tasks with efficient computing resources, but there needs to be more empirical research. To solve this, this study emphasizes the ensemble of uni-modal networks and proposes a Unified Modal Ensemble (UME) Method, an effective modality combination method. UME minimizes the heterogeneity between modalities through sequential Representation Learning and maps each modality to the same latent space. We conducted Visual Question Answering Task experiments to verify the UME approach by combining traditional deep-learning networks with the latest pre-trained models. As a result of the experiment, when VGG and LSTM were combined, the UME approach showed a 40.64% improved accuracy compared to the simple combination method. In addition, when a pre-trained language model and vision model based on the transformer were combined, it showed an increase in accuracy of more than 16% on average. The UME approach has been proven to improve the learning and inference performance of the model and minimize the heterogeneity between modalities. This method emphasizes its generality and universality, which can be applied to all deep learning network structures and data types in theory while efficiently managing computational complexity.

## 간단한 내용 요약
- LMM(대형 멀티모달 모델, Large Multimodality Model) 혹은 VLM(이미지-언어 모델, Vision-Language Model)은 많은 멀티모달 작업에서 높은 성능을 보이나 리소스가 많이 필요하기 때문에 일반적인 상황에서 사용이 제한된다.
- 효율적인 컴퓨팅 자원으로 실용적인 멀티모달 작업을 수행하기 위해 'Unified Modal Ensemble(UME)' 방안을 제시한다.
- UME 방안은 순차 표현 학습을 통해 모달리티 간의 이질성을 최소화하고 각 모달리티를 같은 잠재 공간에 매핑한다.
![](../src/Pasted%20image%2020241221193425.png)

- VQA Task에서 실험한 결과, 본 방안은 단순 결합 방안 대비 약 40.65% 향상된 정확도를 보이며, 최신 모델을 결합했을 때 평균적으로 16% 이상 향상된 정확도를 보인다.
- 본 방안은 계산 복잡도를 효율적으로 관리하며, 이론상 모든 딥러닝 네트워크 구조와 데이터 유형에 적용 가능한 방안이다.

![](../src/Pasted%20image%2020241221193459.png)