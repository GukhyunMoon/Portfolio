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

![image](https://github.com/user-attachments/assets/f879cb33-63b2-4dbd-9f5e-e959d626c4d6)
