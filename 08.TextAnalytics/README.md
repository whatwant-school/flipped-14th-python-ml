# Chapter08. 텍스트 분석


## NLP vs. Text Analytics

- Text Analytics (텍스트 분석, TA) = Text Mining
  - 비정형 텍스트에서 의미 있는 정보를 추출하는데 중점

- NLP (National Language Processing)
  - 머신이 인간의 언어를 이해하고 해석하는데 중점
  - 텍스트 분석을 향상하게 하는 기반 기술


## 텍스트 분석 (Text Analytics)

- 텍스트 분류 (Text Classification, Text Categorization)
- 감성 분석 (Sentiment Analysis)
- 텍스트 요약 (Summarization)
- 텍스트 군집화 (Clustering) & 유사도 측정


## 피처 벡터화 (Featire Vectorization) = 피처 추출 (Feature Extraction)

- BOW (Bag of Words)
- Word2Vec


## 텍스트 분석 수행 프로세스

  1. 텍스트 사전 준비작업 (텍스트 전처리)
      - 클렌징, 대/소문자 변경, 특수문자 삭제 등의 클렌징 작업
      - 단어(Word) 등의 토큰화 작업
      - 의미 없는 단어(Stop word) 제거 작업
      - 어근 추출 (Stemming Lemmatization) 등의 텍스트 정규화 작업
  2. 피처 벡터화/추출
      - 피처를 추출하고 여기에 벡터 값을 할당
      - 대표적인 방법 : BOW, Word2Vec
  3. ML 모델 수립 및 학습/예측/평가


## NLP, 텍스트 분석 패키지

- NLTK (Natural Language Toolkit for Python)
  - 파이썬의 가장 대표적인 NLP 패키지
  - 방대한 데이터 세트와 서브 모듈 보유
  - NLP의 거의 모든 영역 지원
  - 수행 속도는 빠르지 않아서 대량의 데이터 기반에서는 활용 어려움
- Gensim
  - 토픽 모델링 분야에서 두각
  - Word2Vec 구현 등의 다양한 신기능 제공
- SpaCy
  - 뛰어난 수행 성능

