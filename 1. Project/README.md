# 외국인 대상 영문 법령 검색 AI
----------------------------
## 프로젝트 개요
- 법령 정보의 복잡성과 언어 장벽으로 인해 외국인들이 법령을 이해하는 데 어려움을 겪음
- 외국인 대상 범죄가 자주 발생 하지만 범죄 관련 기타 다른 법령 검색은 쉽지 않다.
- 그렇기에 외국인을 위한 맞춤형 영문 법령을 쉽게 찾아볼 수 있는 법령 추천 AI를 생성

## 프로세스
1. 데이터 : 국가법령정보 공동활용의 영문법령 API를 활용하여 추출 > 외국인 비대상 법령 정제
2. ML모델 : Text Cleaning, Tokenization > Stopwords 제거 > TF-IDF 기반 Sentence Similarity 검색 모델
3. DL 모델 : 조항별 Keyword 추출 : Key-Bert / (Clustering : UMAP, HDBSCAN) > Transformers 기반 검색 모델
4. 최종 모델 : 앙상블 방법 적용

<img src="https://github.com/user-attachments/assets/849ba289-4f06-4ed8-9656-a4a31b16ad79" width="800">

## 결과
- 검색한 문장과의 유사도 검사를 통해 관련 법령 검색 (4가지 모델의 결과를 Voting 후 최종 결과 도출)
<img src="https://github.com/user-attachments/assets/59ce11bb-6b1f-43d2-b2aa-ef8b251666db" width="800">

## 기대효과 및 Lesson and Learned

### 기대효과
- 외국인을 위한 맞춤형 법령 검색 시스템 구축을 통해, 외국인들이 법령을 쉽게 이해하고 관련 법령을 신속하게 찾을 수 있음
- 외국인 관련 법적 분쟁 및 범죄 발생을 줄이는 데 기여
- ML 및 DL 모델을 결합한 AI 시스템을 통해 법률 전문가들이 법령 검토 시간을 단축할 수 있음

### Lesson and Learned
- 데이터 전처리와 텍스트 처리의 중요성을 이해하고, 다양한 전처리 기법을 학습
- TF-IDF 및 코사인 유사도를 통한 텍스트 유사도 분석 과정에서 텍스트 데이터의 특성을 다루는 방법을 터득
- 머신러닝 및 딥러닝 모델을 결합하여 최적의 성능을 내기 위한 모델 선택과 튜닝의 중요성을 학습