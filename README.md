# Data Scientist / Analyst
-----------------------------------------------------------
## 목차(Contents)
(목차의 프로젝트를 클릭시 상세내용으로 이동합니다.)

1. [지역별 음식 유행에 따른 상권 분석](./E-commerce/README.md) **E-commerce**(ML)
2. [외국인 대상 영문 법령 검색 AI](./NLP/README.md) **NLP**(ML / DL)
3. [초 개인화 보드게임 추천 시스템](./Board Game/README.md) **Board Game**(ML / DL)
-----------------------------------------------------------

<br>

## [1. 지역별 음식 유행에 따른 상권 분석](./1.%20Project/README.md)

### 문제 정의
- 코로나19 이후 국내 외식업체 폐업률 증가, 총 가게수 약 269만개 중 66.72% 비율로 절반 이상 문을 닫았음
- 지역별 상권의 음식점 유형이 각종 요인에 어떤 영향을 받는지 분석하고, 이를 바탕으로 각 지역에 최적화된 창업 전략을 수립
  
### 주요 역할
1. 데이터 수집 및 전처리(읍,면,동 컬럼을 세분화하여 법정동, 행정동으로 분리, PublicDataReade 모듈 사용)
2. 탐색적 데이터 분석(EDA)을 위해 PCA(주성분 분석)를 사용, 주요 변수 간 관계 탐색
3. KMeans 클러스터링을 통해 지역별 음식 유형의 특성을 군집화하여 중요 인사이트 도출
   
### 기대효과 및 Lesson and Learned
- 지역별 음식 소비 패턴 분석을 통해 상권별 맞춤형 마케팅 전략 수립 가능
- 음식점 창업이나 상권 분석을 위한 인사이트 제공, 지역 특성에 맞춘 메뉴 구성 및 고객 타겟팅에 활용 가능
- 데이터의 분포와 패턴을 이해하는 데 있어 클러스터링의 유용성을 경험, 군집별 특성을 분석하여 중요한 인사이트를 도출 방법 학습

<br>

## [2. 외국인 대상 영문 법령 검색 AI](./2.%20Project/README.md)

### 문제 정의
- 외국인 대상 범죄가 자주 발생, 외국인을 위한 맞춤형 영문 법령 추천 AI 생성
  
### 주요 역할
1. 데이터 수집 및 전처리
2. TF-IDF 방식으로 데이터 벡터화
3. 코사인 유사도를 통한 텍스트 간 유사도 계산 및 상위 유사 항목 도출
   
### 기대효과 및 Lesson and Learned
- 외국인을 위한 맞춤형 법령 검색 시스템 구축을 통해, 외국인들이 법령을 쉽게 이해하고 관련 법령을 신속하게 찾을 수 있음
- ML 및 DL 모델을 결합한 AI 시스템을 통해 법률 전문가들이 법령 검토 시간을 단축할 수 있음
- 데이터 전처리와 텍스트 처리의 중요성을 이해하고, 다양한 전처리 기법을 학습

<br>

## [3. 초 개인화 보드게임 추천 시스템](./3.%20Project/README.md)

### 문제 정의
- 넷플릭스, 쿠팡, 스포티파이, 유튜브 등 여러 산업 분야에서 개인화된 추천 시스템이 활발해짐
- 하지만 보드게임 추천 분야에서는 추천 시스템이 미흡한 상태
- 각 사용자의 취향을 반영한 맞춤형 보드게임 추천 시스템을 개발

### 주요 역할
1. 유저 세그먼트 분석 : 유저 평점을 기준으로 세그먼트 구분, 파레토 법칙을 활용
2. 상위 20%의 사용자 군을 탐색적 데이터 분석(EDA) 수행
3. 각 유저(신규 유저, 소프트 유저, 하드 유저)에 맞는 추천 모델 개발 및 성능 평가

### 기대효과 및 Lesson and Learned
- 개인화된 추천 시스템을 통해 보드게임을 보다 정확하게 추천함으로써 유저의 만족도와 참여도를 크게 향상시킬 수 있음
- 신규유저, 소프트유저, 하드유저로 나뉜 다양한 유저군의 특성에 맞춘 맞춤형 추천을 제공하여 사용자 경험을 극대화할 수 있음
- NDCG, 다양성 지표 등을 고려하여 최종 우수 모델을 선정하면서, 정확도보다 복합적인 지표 사용이 성능 개선에 중요성을 학습
