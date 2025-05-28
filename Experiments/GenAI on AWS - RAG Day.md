## 워크샵 개요
- **일시:** 2024년 8월 12일
- **장소:** AWS Korea

## Agenda

| **시간**        | **내용**                       | **강사** |
| ------------- | ---------------------------- | ------ |
| 09:30 - 10:05 | RAG 및 Vector Database (이론)   | SA 이유정 |
| 10:05 - 10:55 | Amazon OpenSearch 실전 활용 (이론) | SA 명기현 |
| 11:10 - 11:45 | RAG 구성을 위한 오픈소스              | SA 황장환 |
| 11:45 - 11:55 | 실습환경 배포                      | SA 황장환 |
| 13:15 - 14:30 | OpenSearch를 활용한 RAG 구성 (실습)  | SA 현진환 |
| 14:45 - 15:20 | Advanced RAG (이론)            | SA 임연욱 |
| 15:30 - 16:45 | Advanced RAG (실습)            | SA 박경수 |
| 16:45 - 17:00 | Q&A / Closing                | -      |

## 1. RAG 및 Vector Database

### 주요 내용
- **Foundation Model에 대해**
	- FM의 한계와 커스터마이징 방법론 설명 (프롬프트 엔지니어링, RAG, 파인튜닝 등)
- **RAG 구성 및 동작 과정**
	- 검색 방법 설명 (키워드 검색, 구조화된 데이터 검색, 시맨틱 검색)
- **임베딩 발전 과정 설명**
	- Distributed Representation (Word2Vec, GloVe, FastText)
	- Contextualized embedding (ELMo 등)
	- Transformer 기반 임베딩 (BERT, GPT, T5)
- **벡터DB와 유사도 검색 관련 내용 설명**: 
	  - K-NN (Cosine, Euclidean, Manhattan) vs. ANN 알고리즘 (HNSW, LSH, IVF)
- **Amazon Titan Text Embedding 소개**
	- v2 (다국어 지원), G1 (이미지 및 영어 텍스트 지원) 모델 소개
	- 타이탄 임베딩 모델의 벤치마크 및 성능 비교 여부
- **Amazon Bedrock 소개**
	- 다양한 데이터 포맷 지원 (txt, md, html, docs, csv 등)


AWS는 Knowledge basesd for amazon bedrock을 제공하고 있으며, 다양한 포맷을 지원하나 ppt, hwp 등은 지원하고 있지 않았습니다. 모델은 Claude-3을 사용한다고 합니다. 

Amazon Titan Text Embedding은 v2와 G1이 대표적이며, 두 모델은 동일한 max tokens(= 8,192)을 가지고 있습니다. v2는 텍스트 임베딩만 지원하나 다국어에 특화되어있고, G1은 이미지또한 임베딩이 가능하나 영어만 지원한다고 합니다. 이미지는 5mb, 2048\*2048\*3 까지 처리 가능하다고 합니다. 실제로 이미지 넣었을 때 어느정도 어울리는 한국어 텍스트를 리트리브하는 것 보여주셨습니다. 그러나 이를 본 어떤 분이 본인이 테스트해봤을때는 G1 모델이 퀄리티가 낮았다고하며 심지어 영어도 퀄리티가 안좋았다고하니 '아 그런가요.. 갈길이 멀었네요..ㅎㅎ' 로 답변하셨습니다. 타이탄 임베딩 모델과 타 모델간의 성능 비교가 있었으면 좋았을 것 같다고 생각하였습니다.


## 2. Amazon OpenSearch 실전 활용

### 주요 내용
- Advanced RAG에 대해
- OpenSearch 설명
- AWS는 하이브리드 서치 시 텍스트(BM25) 점수와 벡터(임베딩 모델) 점수 간의 갭을 normalization하여 제공하고 있음. 각각의 가중치 -> 0.7, 0.3

## 3. RAG 구성을 위한 오픈소스

### 주요 내용
- 생성형 AI 애플리케이션 구현 한계
	- 검색 정확도를 높이기 위한 방법론 (프롬프트 엔지니어링, RAG, 파인튜닝 등)

- **오픈소스 프레임워크**
	- **LangChain**: 높은 러닝 커브, 데이터 수집 및 인덱싱 기능 부족
	- LlamaIndex: 제한된 LLM 지원, 작은 커뮤니티
	- Haystack: 검색 및 질문 답변 시스템 구축에 특화, 대규모 데이터셋 처리 시 리소스 요구, 일부 최신 LLM이나 도구와의 통합이 랭체인에 비해 부족함

	특별한 상황 아니면 LangChain 따라가는게 좋을 것 같다고 말하셨습니다.

- **Document Loader:**
![](../src/Pasted%20image%2020250528232911.png)
	1. PyPDFium2
		1. 빠른 처리속도
		2. 복잡한 레이아웃에서도 정확한 텍스트 추출
		3. 텍스트 추출, 이미지 렌더링, pdf 편집 기능 가능
		4. 상업적 사용 가능
		5. 부족한 커뮤니티 및 문서화
		6. 일부 고급 PDF 지원 X
	2. **PyMuPDF**
		1. 빠른 처리 속도 및 정확한 텍스트 추출
		2. 광범위한 기능 제공
		3. **AWS 기준 제일 높은 정확도**
		4. AGPL 라이선스로 인한 상업적 사용 제한 및 일부 복잡하거나 손상된 PDF 파일에서 충돌이나 오류 발생 가능
	3. PyPDF2
		1. 기본적인 PDF 기능
		2. 상업적 사용 가능
		3. 파이썬 기반 라이브러리로 크로스 플랫폼 호환성 좋음
		4. 복잡한 레이아웃에서 텍스트 추출 정확도 낮음
		5. 대용량 PDF 처리시 낮은 성능
	4. PDFMiner
		1. 레이아웃 분석에 특화되어 복잡한 구조에서도 텍스트 추출 가능
		2. 다국어 PDF 처리에 적합
		3. 텍스트 위치정보 제공으로 원본 레이아웃 재구성 가능
		4. 상대적으로 느린 처리속도 및 대량 PDF, 대용량 PDF 처리시 느려지고 메모리도 많이먹음
	5. PDFPlumber
		1. 다양한 기능 제공
		2. 테이블 추출에 강점이 있음
		3. 느린 처리속도 및 복잡한 PDF 에서 정확성 저하
		4. 높은 메모리 사용량
		5. PDFMiner 기반 고도화 된 버전
	
	개인용은 무조건 Pymupdf, 상업적일땐 pypdfium2, 테이블이 많으면 pdfplumber 라고 말씀하셨습니다.

- **Text Splitter**:
	1. 토큰기반 분할, 시맨틱 분할 등이있음
	2. CharacterTextSplitter
		1. 구현 간단
		2. 빠른 처리속도
		3. 일관된 크기의 청크 생성
		4. 의미단위 고려X 문맥 유지에 제한적
		5. 긴문장이나 단락을 부적적하게 분할할수있음
		6. 간단한 텍스트 분할할때, 처리속도 중요한 대규모 데이터셋, 문맥유지 크게 중요하지 않는경우
	3. **RecursiveCharacterTextSplitter**
		1. 다양한 구분자(\\n 등)를 추가해 더 의미있는 청크 생성
		2. 문맥유지 효과적
		3. 처리속도 느리고 일관된 크기의 청크 생성 어려움
		4. 문맥유지 중요한 복잡한 문서일때, 다양한 형식의 텍스트 처리할때, **일반적인 환경에서 기본 선택으로 추천함**
	4. TokenTextSplitter
		1. LLM의 토큰 제한을 정확히 고려함
		2. 토큰화 과정으로 처리속도가 상대적으로 느림
		3. 의미 단위 고려하지 않아서 문맥유지에 제한적임
		4. 토큰수제한이 엄격할 시스템 및 정확한 토큰 수 계산이 필요할떄 사용하면 좋음
	5. MarkDownHeaderTextSplitter
		1. 마크다운 문서의 구조를 유지하면서 분할
		2. 문서의 계층 구조를 메타데이터로 활용 가능
		3. 마크다운만 가능하고 헤더가 없는 긴 섹션의 경우 적절한 분할이 어려움
		4. 문서 구조와 계층을 유지해야할 때, 기술 문서, 위키, readme 파일 등의 처리할때 좋음

- **임베딩 모델 비교**:
![](../src/Pasted%20image%2020250528232922.png)
	1. (AWS) Titan Text Embedding v2
		1. 256, 512, 1024 차원 선택 가능
		2. 100개 이상 언어 지원
		3. 1k 토큰에 0.00002 달러
		4. 다른 모델과의 벤치마킹 및 검증 필요함
		5. amazon 생태계에 의존성이 높음
		6. openai 대비 1/6 수준
	2. (openai) text embedding 3 large
		1. 3072 차원 및 매우 다양한 언어 지원
		2. 높은 성능과 정확도
		3. 데이터 프라이버시 우려 (데이터 프라이버시 방침 및 규정을 공개하지 않음)
	3. (upstage) solar embedding-1-large
		1. 쿼라용과 문서용 별도의 두가지 모델 제공
		2. 영어 한국어 일본어에 최적화되어있음 (openai 모델보다 우수하다고 표현함)
		3. 가격은 비공개되어있으나 효율적이라 생각한다고함
	4. (huggingface) 모델 알아서 사용가능

- **Vector Store 비교**
	![](../src/Pasted%20image%2020250528232929.png)
	1. opensearch
		1. elasticsearch 기반 텍스트 검색 및 분석 기능
		2. 온프라이미스로도 가능하고 AWS 관리형 서비스로도 사용 가능함
		3. 엘라스틱서치 기반이나 완전한 호환성 부족함. (점점 떨어지고있음)
	2. chroma
		1. 파이썬 네이티브 벡터데이터베이스
		2. 내장 임베딩 모델 제공
		3. 대규모 환경에서의 성능 검증 부족
		4. 기능 제한적
	3. weaviate
		1. GraphQL 유사 API로 유연한 쿼리 가능
		2. 자연어검색(키워드검색), 키워드 검색 모드 지원
	4. milvus
		1. 대규모 벡터데이터 처리에 최적화
		2. 다양한 인덱스 유형 지원(11가지)
		3. GPU 가속화 지원으로 고성능 제공


## 4. 실습환경 배포

### 주요 내용
- **키워드 검색**이 중요하다고 하며, AWS의 '노리'는 특정 회사만의 용어, 패턴 등을 등록할 수 있고 쓸모없는 부사 등을 제거하는 등 관리하기 용이하다고 합니다.
  - Token filter, decompound, custom word, 동의어, 불용어 등 관리 가능

## 5. Advanced RAG

### 주요 내용
- **프로덕션 환경에서 RAG의 한계**
	1. specific한 환경이기 떄문
	2. 검색이 불필요한데 쓰는경우
	3. 관련 없는 문서를 검색하는 경우
	4. 데이터가 응답 생성에 항상 도움이 될까

- **Advanced RAG 기술**:
	- **Pre-retrieval**: Query expansion
	- **Retrieval**: Multi-hop retrieval, sentence window retrieval
	- **Post-retrieval**: Reranking
	- **Generation**: Critique
	- **Combined Techniques**: Self-RAG, CRAG (Corrective RAG)
	- **Optimization**: Chunking, Query Augmentation
	
- **Self-RAG**:
	- 다음 두가지의 일반적인 RAG 문제점을 해결하기 위해 나왔습니다
		1. Top-K로 인해 아주 적은 부분의 정답과 대부분의 필요없는 문서가 들어가게된다
		2. 히스토리가 들어가면서 새로운 질문을 했을 때 이전의 내용을 고려해서 답변이 출력되게된다
	- 검색 필요 여부를 1차 분류, 필요한 경우 문서별로 검색 결과 생성 및 검증
		1. 검색이 필요한지 안한지 1차적으로 classification
		2. 검색이 필요하다면 병렬로 세그먼트 생성
			1. Q + 문서1 
			2. Q + 문서2
			3. Q + 문서3
			4. 이런식으로 입력해서 출력을 뽑고, 각각 맞는 문구인지 아닌지 classification 진행
		3. 맞는 문구만 입력으로 선택해서 최종적으로 해당 문서만 입력에 포함
- **Corrective RAG**:
	- 자체 평가를 통한 실시간 정보 보정, Knowledge Refinement 및 Knowledge Searching
	- 어떻게 하면 지식 저장소에 없는 정답을 가져올 수 있을까? 라는 의문에서 시작
	- 방법
		1. 문서를 가져오면 그걸 sLM을 통해 맞는건지 확인
		2. 맞다면 Knowledge Refinement (더 작은 단위로 청킹한 뒤 sLM 필터링을통해 필요한 정보만 recompose)
		3. 틀리면  knowledge searching (질의 rewrite한 뒤  웹검색 후 뽑은 문서 중에 선택)
		4. 애매하면 둘다 수행

- **LangGraph & Langsmith**:
	- Agent 활용한 Reasoning + Action(ReAct) 기법 설명


## 느낀점
이번 GenAI on AWS(Rag Day)를 통해 AWS 서비스에 적용된 RAG 시스템이 어떻게 작동하도록 설계했는지 알 수 있었습니다. 저희 팀의 기술 수준이 높다는 것을 다시한번 느꼈으며, 최신 RAG 기법들을 정리하고 기존 기술들의 비교 평가 결과를 공유한 점에 있어 많은 도움을 얻은 것 같습니다.