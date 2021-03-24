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


## 텍스트 사전 준비 작업(텍스트 전처리) - 텍스트 정규화

- 클렌징 (Cleansing)
  - 불필요한 문자, 기호 제거
  - HTML, XML 제거 等
- 토큰화 (Tokenization)
  - 문서에서 문장을 분리 = 문장 토큰화 (Sentence Tokenization)
    - 문장의 마침표(.), 개행문자(\n) 등의 기호로 분리
    - 정규 표현식
  - 단어를 토큰으로 분리 = 단어 토큰화 (Word Tokenization)
    - 공백( ), 콤마(,), 마침표(.), 개행문자(\n) 등의 기호로 분리
    - 정규 표현식
- 필터링/스톱 워드 제거/철자 수정
  - 스톱 워드 (Stop Word) = 분석에 큰 의미가 없는 단어
  - NLTK 內 언어별 스톱워드 목록화
- Stemming / Lemmatization
  - 과거/현재 시제, 3인칭 단수 여부, 진행형 등과 같은 문법적 또는 의미적으로 변화하는 단어의 원형 찾기
  - Stemming : 원형 단어로 변환 시 일반적 또는 더 단순화된 방법을 통해 일부 철자가 훼손된 어근 단어 추출
  - Lemmatization : 품사와 같은 문법적인 요소와 더 의미적인 부분을 감안해 정확한 철자로 된 어근 단어 추출 (변환 시간이 더 소요됨)


## Bag of Words (BOW)

- 문서가 가지는 모든 단어를 문맥이나 순서를 무시하고 일괄적으로 단어에 대한 빈도 값을 부여해 피처 값을 추출하는 모델
- 문서 내 모든 단어를 한꺼번에 봉투(Bag) 안에 넣은 뒤에 흔들어서 섞는다는 의미로 Bag of Words 모델이라고 함
- 장점 : 쉽고 빠른 구축
- 단점
  - 문맥 의미(Semantic Context) 반영 부족
  - 희소 행렬 문제(희소성, 희소 행렬)
    - 대규모의 칼럼으로 구성된 행렬에서 대부분의 값이 0으로 채워지는 행렬 = 희소 행렬
    - 희소행렬은 일반적으로 ML 알고리즘 수행 시간과 예측 성능 저하 유발


### BOW 피처 벡터화
ML 알고리즘에 넣기 위해서는 텍스트를 특정 의미를 갖는 숫자형 값인 벡터 값으로 변환 필요 = 피처 벡터화

- 카운트 기반의 벡터화
  - 해당 단어가 나타나는 횟수 기준
  - 값이 높을수록 중요한 단어
  - 단점 : 자주 사용할 수 밖에 없는 단어까지 높은 값을 갖게 됨 → 해결하기 위해 TF-IDF
- TF-IDF (Term Frequency - Inverse Document Frequency) 기반의 
  - 자주 나타나는 단어에 높은 가중치를 주되
  - 문서에서 자주 나타나는 단어에 대해서는 패널티 부여


### BOW 벡터화를 위한 희소 행렬

- BOW 형태를 가진 언어 모델의 피처 벡터화는 대부분 희소행렬
- 희소행렬 = 메모리 공간이 많이 필요, 연산 시간도 많이 소요
- COO (Coordinate: 좌표) 형식
  - 0이 아닌 데이터만 별도의 데이터 배열에 저장
- CSR (Compressed Sparse Row) 형식
  - COO 형식 : 행과 열의 위치를 나타내기 위해서 반복적인 위치 데이터를 사용해야 하는 문제점 有
  - CSR 형식 : 위치값을 배열로 다시 저장
    - [ 0, 0, 1, 1, 1, 1, 1, 2, 2, 3, 4, 4, 5 ]
    - 총 항목 개수 배열 = [ 13 ]
    - → [ 0, 2, 7, 9, 10, 12, 13 ]
      - `0`이 시작하는 위치 0
      - '1'이 시작하는 위치 2
      - '2'가 시작하는 위치 7
      - ...
      - 총 항목 개수 13


## 텍스트 분류 실습 - 20 뉴스그룹 분류

...

---

## 감성 분석 (Sentiment Analysis)

- 지도 학습 : 일반적인 텍스트 기반의 분류와 거의 동일
- 비지도 학습 : `Lexicon`이라는 일종의 감성 어휘 사전 이용
  - Lexicon : 감성 분석을 위한 용어와 문맥에 대한 다양한 정보 보유


### 지도학습 기반 감성 분석 실습 - IMDB 영화평

...


### 비지도학습 기반 감성 분석 소개

- Lexicon = 감성사전
- 긍정(Positive) 감성 + 부정(Negative) 감성 = 감성 지수 (Polarity Score)
  - 단어 위치, 주변 단어, 문맥, POS(Part of Speech) 참고해서 결정됨
- NLP 패키지의 WordNet : Semantic 분석을 제공하는 방대한 영어 어휘 사전
  - Semantic : 문맥상 의미
  - 각각의 품사로 구성된 개별 단어를 Synset(Sets of cognitive Synonyms)이라는 개념을 이용해 표현


### 대표적인 감성 사전

- SentiwordNet : 감성 단어 전용 WordNet
- VADER : 소셜 미디어 텍스트에 대한 감정 분석
- Pattern : 예측 성능 측면에서 가장 주목받는 패키지


---

## 토픽 모델링 (Topic Modeling)

- Topic Modeling : 문서 집합에 숨어있는 주제 찾기
  - 사람 : 더 함축적인 의미로 문장을 요약
  - ML : 숨겨진 주제를 효과적으로 표현할 수 있는 중심 단어를 함축적으로 추출
- 대표 기법
  - LSA (Latent Semantic Analysis)
  - LDA (Latent Dirichlet Allocation)


---

## 문서 군집화 (Document Clustering)

- 비슷한 텍스트 구성의 문서를 clustering
- 텍스트 분류 기반의 문서 분류와 유사


---

## 문서 유사도 측정 방법 - 코사인 유사도 (Cosine Similarity)

- 두 벡터 사이의 사잇각을 구해서 얼마나 유사한지 수치로 적용

---

## 한글 텍스트 처리 - KoNLPy

- 한글 형태소 패키지
