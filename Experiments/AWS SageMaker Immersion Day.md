일자: 2024년 11월 12일(화)

KRX에서 주관한 AWS SageMaker Immersion Day에 참석하였습니다.

![](../src/Pasted%20image%2020250528232637.png)

![](../src/Pasted%20image%2020250528232650.png)

주요 내용은 "AWS 주요 서비스 설명", "AWS SageMaker 실습" 입니다.

<div class="page-break" style="page-break-before: always;"></div>

## AWS Infra 
- **주제:** AWS 퍼블릭 및 프라이빗 서브넷 구성, EC2 인스턴스, 오토스케일링, 네트워크 설정 및 보안 구성
![](../src/Pasted%20image%2020250528232703.png)

### 주요 설명 내용
1. **서브넷 및 라우팅 테이블**
   - 퍼블릭 서브넷과 프라이빗 서브넷의 활용 차이점을 설명하고, 프라이빗 서브넷에서 인터넷을 통해 접근 가능하도록 설정하는 방법 소개.
   - 라우팅 테이블을 통한 경로 설정과 다양한 서브넷의 네트워크 구성.

2. **EC2 인스턴스 관리**
   - **EC2 인스턴스 구성:** VM 기반의 가상화 환경에서 EC2의 생성 및 관리.
   - **온디맨드, 예약 인스턴스, 스팟 인스턴스**의 요금 정책 설명.
   - 오토스케일링을 통해 트래픽 변화에 따라 인스턴스를 자동으로 늘리고 줄이는 기능을 소개.

3. **인스턴스 수명 주기 관리**
   ![](../src/Pasted%20image%2020250528232711.png)
   - 인스턴스의 상태(실행 중, 정지, 종료)에 따른 과금 차이점을 설명하며 비용 최적화 방법 논의.

4. **VPC (Virtual Private Cloud) 설정**
![](../src/Pasted%20image%2020250528232718.png)
   - **VPC와 엔드포인트**를 활용하여 퍼블릭 네트워크 없이 안전하게 내부 통신을 설정하는 방법.
   - VPC 설정 실습에서 멀티 서브넷과 가용 영역을 설정하여 네트워크의 신뢰성 확보.

5. **AMI 및 사용자 스크립트 설정**
   - 인스턴스 시작 시 자동으로 스크립트를 실행해 소프트웨어 설치 및 환경 설정을 자동화하는 `User Data` 기능 활용.

6. **로드밸런서 구성**
   - 애플리케이션 로드밸런서(ALB)와 네트워크 로드밸런서를 통한 트래픽 분산 설정.
   - HTTP, HTTPS 트래픽의 효율적 분배를 위한 ALB 설정과 보안 그룹을 통한 접근 제어.

### 노트
AWS 인프라를 이용한다면 타 업체 대비 다음과 같은 이점이 있다고 언급함
- **비용 최적화:** 온디맨드와 예약형 인스턴스의 적절한 조합을 통한 비용 절감 전략 제안.
- **오토스케일링과 인프라 유연성:** 다양한 인스턴스 유형 및 오토스케일링으로 트래픽 변화에 따른 유연한 대응 가능.
- **보안 강화:** 퍼블릭과 프라이빗 서브넷, VPC 엔드포인트를 통한 내부 통신 최적화로 클라우드 환경 보안 강화.
- **퍼블릭 및 프라이빗 서브넷 구성:** VPC 내 멀티 서브넷 설정 및 각 서브넷의 사이더 블록 지정.
- **AMI 생성:** 커스텀 AMI를 생성해 동일한 환경을 재사용할 수 있도록 설정.
- **로드밸런서 및 오토스케일링 설정:** 로드밸런서와 오토스케일링 그룹을 통한 인스턴스의 수평적 확장 설정.

### 실습
- **주요 과정:** AWS 계정 관리, SageMaker 활용법, 모델 학습 환경 구축, 클라우드 상의 분산 학습과 효율적 자원 관리
![](../src/Pasted%20image%2020250528232726.png)
#### 주요 내용
1. **AWS 계정 및 크레딧 관리**
   - 인스턴스 유형별 비용 차이에 대한 설명과, 고사양 인스턴스를 사용할 경우 크레딧이 빨리 소진될 수 있음을 언급함

2. **AWS SageMaker 개요**
   - SageMaker는 머신러닝 모델의 개발, 학습, 배포까지 지원하는 완전 관리형 서비스.
   - SageMaker 노트북 인스턴스를 통해 개발 환경 구축 가능.
   - SageMaker에서 분산 학습 환경을 설정하여 대규모 데이터 학습에 최적화.

3. **SageMaker 노트북 인스턴스와 학습 인스턴스**
   - 개발용 노트북 인스턴스와 학습을 위한 고성능 인스턴스를 별도로 운영하여 비용 절감.
   - 학습은 별도의 컨테이너 환경에서 진행하며, 데이터는 S3와 연동하여 사용.

4. **배치 추론 및 실시간 추론**
   - SageMaker의 추론 기능을 통해 배치 및 실시간 추론을 지원.
   - 대규모 데이터에 대한 배치 추론과 작은 데이터에 대한 실시간 추론의 효율적인 관리 방법 설명.

5. **모델 배포와 ML Ops**
   - SageMaker를 통해 모델 배포와 모니터링을 자동화하고, DevOps와 유사한 ML Ops 개념 도입.
   - 추적, 모니터링, 로그 관리를 통해 모델의 지속적 성능 개선 가능.

- **비용 관리의 중요성:** SageMaker에서 사용할 수 있는 다양한 인스턴스를 전략적으로 선택하여 비용을 절감.
- **클라우드 자원 활용의 유연성:** 필요에 따라 인스턴스 스펙을 조절하여 분산 학습이 가능하고, 로컬 환경보다 확장성이 높음.
- **통합 워크플로우:** SageMaker를 통한 데이터 준비, 학습, 배포를 모두 처리하여 워크플로우가 일관되고 효율적임.
- **S3를 활용한 데이터 관리**: 데이터 세트를 S3에 저장하고 SageMaker와 연동하여 효율적 데이터 접근 가능.
- **컨테이너 관리**: 트레이닝과 추론을 위한 별도 컨테이너 관리 및 사용법 실습.
- **Hyperparameter Tuning**: 최적의 파라미터를 찾기 위한 SageMaker의 HPO 기능 소개.

이 강의는 AWS 환경에서 SageMaker를 활용하여 머신러닝 프로젝트의 비용 효율성을 극대화하고, 확장성 있는 학습과 배포 환경을 구축하는 실질적인 접근 방법을 강조하였습니다.

### AWS SageMaker 사용법
#### 강의 주제
 AWS SageMaker 노트북 인스턴스의 생성 및 사용법, 자원 관리와 비용 절감, 커널 및 패키지 설정, 모델 학습 환경 구축

#### SageMaker 사용 과정
1. **노트북 인스턴스 생성 및 자원 확인**
   - SageMaker 콘솔에서 노트북 인스턴스를 생성하며, 인스턴스 상태가 팬딩(Pending)에서 서비스 중(In Service)으로 전환되는 과정 확인.
   - 서비스 쿼터에서 필요한 인스턴스 유형(G5, G6 등)의 자원 할당 및 비용에 관한 설명.

2. **커널 설정 및 환경 구성**
   - 여러 머신러닝 프레임워크(PyTorch, TensorFlow 등)에 맞춰 사전 구성된 커널 제공.
   - `requirements.txt` 파일을 활용해 필요 패키지를 설치하고, 새로운 커널을 생성하여 원하는 학습 환경 구축.

3. **데이터 및 코드 설정**
   - 데이터는 AWS S3에 저장하여 인스턴스와 연동해 사용할 수 있도록 설정.
   - `git clone` 명령어를 통해 SageMaker 워크샵 예제를 클론해 실행하며, 필요한 템플릿을 정의하고 모델 학습에 맞는 환경 구성.

4. **모델 학습 및 분산 학습 설정**
   - 로컬 환경 및 클라우드 환경에서 모델을 학습시키는 방법과 SageMaker의 오토스케일링 기능을 활용한 분산 학습 설명.
   - Hyperparameter Tuning 및 Distributed Training을 위해 SageMaker에서 제공하는 분산 학습 기능 활용.

5. **모델 배포 및 MLOps**
   - 추론 작업을 위한 배포와 배치 및 실시간 추론의 차이점을 설명하며, SageMaker를 통한 ML 파이프라인의 자동화와 지속적 관리(MLOps).

본 강의는 AWS SageMaker의 노트북 인스턴스와 분산 학습 기능을 최대한 활용하여, 효율적이고 확장성 있는 모델 학습 환경을 구축할 수 있도록 하는 데 초점을 맞추었습니다.
llama3.1을 기반으로 실습을 진행하였습니다.

### 질의응답 내용
Q1: 리전별로 사용할 수 있는 인스턴스 이미지가 다르고, 모델 제공 여부 및 가격이 다른 이유
A1: 인프라 차이가 가장 큼. 서울 리전도 있지만, 너무 지원이 안되서 korea 본사 직원도 계속 요청해서 따내고 있는 상황이라고 함.  새로 나온 장비나 서비스가 리전별로 바로 지원 가능한 인프라가 있는 곳도 있고 없는 곳도 있음. 

Q2: VPC와 EC2의 차이
A2: Amazon Virtual Private Cloud(Amazon VPC)는 가상 네트워크를 만들고 관리할 수 있는 서비스. 이를 통해 사용자는 네트워크 설정을 커스터마이징하고, 리소스에 대한 보안과 접근을 세밀하게 제어할 수 있는 것. 즉, 목적은 AWS 상의 네트워크 인프라를 논리적으로 분리하여 사용자가 원하는 네트워크 구조를 만들고, 네트워크 트래픽을 효율적으로 제어할 수 있게 하는 것
Amazon EC2 (Elastic Compute Cloud)는 가상 서버를 제공하는 서비스. 사용자는 필요한 스펙의 인스턴스를 생성하고, 원하는 운영체제를 설치하여 애플리케이션을 실행할 수 있음
-> VPC는 AWS 네트워크 인프라를 논리적으로 나누어 관리하는 역할을 하고, EC2는 VPC 내에서 애플리케이션을 실행할 수 있는 가상 서버를 제공. vpc 내에 ec2가 있는거라 거의 비슷하다고 생각하면 된다고 함

Q3: EC2 인스턴스 크기가 오토스케일링 된다고 하는데, 최초에 선택하여 구축한 인스턴스를 중간에 키울 수 있는건지 (예로, 학습 시에만 GPU 자원을 더 가져와서 학습하고 끝나면 반환하는 시스템)
A3: 오토스케일링은 네트워크 대역폭(트래픽)을 타겟으로 진행되고 있는거고, 여러 인스턴트를 붙이는 방식임. AI 모델 학습을 위해서는 인스턴스를 붙일 수도 있겠으나 보통 인스턴스를 키우는게 대부분임. 그렇기 때문에 GPU가 더 필요한 순간에는 수동으로 키워야함

### 느낀점 종합
ML/DL 학습에 필요한 여러 프레임워크를 제공하고 비용 측면에서도 다양한 선택지가 있다는 것은 좋은 점이었지만, 사용하게 될 경우에 AWS 생태계에 지나치게 종속될 것이 걱정되었습니다. 
기존의 SageMaker는 오토 머신러닝 서비스에 가깝다고 느꼈으나, LLM을 학습할 수 있다는 점도 알게되었습니다. AWS 스페셜리스트님이 오셔서 많은 질문을 받아 주셨고, 평상시에 AWS 서비스를 이용하면서 들었던 의문들을 해결할 수 있어 좋았습니다. 실습 과정에서 따라하는 느낌이 강했으나 추후 AWS 서비스 이용 및 설명에 도움이 될 것 같습니다.

이상입니다. 감사합니다.