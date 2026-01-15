# Walmart Review Analysis and Retrieval System

이 리포지토리는 Walmart의 고객 리뷰를 스크레이핑, 처리 및 분석하기 위한 도구를 제공합니다. 이 시스템은 벡터 스토리지로 Pinecone을, 시맨틱 검색을 위해 Sentence Transformers를, 그리고 리뷰 추출 및 분석을 위해 Google의 Gemini AI를 활용합니다.

## Components

- **`rag-chatbot.py`**: Retrieval-Augmented Generator (RAG) 파이프라인을 사용하여 서비스를 초기화하고 응답을 생성하기 위한 메인 스크립트입니다.
- **`review_to_pinecone.py`**: 추출된 리뷰를 처리하고 임베딩을 생성하여 Pinecone에 저장합니다.
- **`semantic_search_client.py`**: 저장된 임베딩에 대해 시맨틱 검색 쿼리를 수행하는 서비스를 제공합니다.
- **`walmart_review_extractor.py`**: Bright Data를 사용하여 Walmart에서 리뷰를 스크레이핑하고 Google Gemini AI를 사용하여 처리합니다.

## Prerequisites

- Python 3.7+
- Pinecone, Gemini AI 및 Bright Data에 대한 액세스 키

## Setup

1. 리포지토리를 클론합니다:
   - `git clone https://github.com/yourusername/your-repo.git`
   - `cd your-repo`

2. 필요한 Python 패키지를 설치합니다:
   - `pip install -r requirements.txt`

3. 루트 디렉터리에 `.env` 파일을 생성하여 환경 변수를 설정합니다. 다음 변수를 추가합니다:
   - `PINECONE_API_KEY=your_pinecone_api_key`
   - `GEMINI_API_KEY=your_gemini_api_key`
   - `BRIGHT_DATA_API_KEY=your_bright_data_api_key`

4. 처리할 수 있도록 리뷰 데이터셋 파일(`extracted_walmart_reviews.json`)을 프로젝트 루트에 배치합니다.

## Usage

### Extract Reviews

`walmart_review_extractor.py`를 사용하여 Walmart에서 리뷰를 가져옵니다:
- `python walmart_review_extractor.py`

### Process Reviews and Populate Pinecone

추출된 리뷰를 처리하고 다음을 사용하여 Pinecone에 upsert합니다:
- `python review_to_pinecone.py`

### Semantic Search

다음을 사용하여 인덱싱된 데이터에서 시맨틱 검색을 수행합니다:
- `python semantic_search_client.py`

### Run the RAG Chatbot

마지막으로 RAG 파이프라인을 실행하고 상호작용하려면 다음을 실행합니다:
- `python rag-chatbot.py`

## Logging

로그는 `data_pipeline.log`에 저장되며, 실시간 모니터링을 위해 콘솔에도 출력됩니다.

## Note

스크립트가 원활하게 동작하도록 필요한 모든 환경 변수와 API 키가 올바르게 구성되어 있는지 확인하시기 바랍니다.