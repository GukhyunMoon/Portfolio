<div align="center">

<h1>외국인 대상 영문 법령 검색 AI</h1>

</div>

**💭 Language : Python**

**🛠 Tool : Google Colab**

**📅 진행기간 : 2024.06.17 ~ 2024.07.11**

**👥 인원 : 5명**

----------------------------------------------------------------

# 프로젝트 개요
- 법령 정보의 복잡성과 언어 장벽으로 인해 외국인들이 법령을 이해하는 데 어려움을 겪음
- 외국인 대상 범죄가 자주 발생 하지만 범죄 관련 기타 다른 법령 검색은 쉽지 않다.
- 그렇기에 외국인을 위한 맞춤형 영문 법령을 쉽게 찾아볼 수 있는 법령 추천 AI를 생성

<br>

# 프로세스
<p align="center">
 <img src="https://github.com/user-attachments/assets/bb40df48-50a2-4092-947f-7379509077ea" width="1000">	
<p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/849ba289-4f06-4ed8-9656-a4a31b16ad79" width="800">	
<p>
	
<br>


# 주요 역할
1. 데이터 수집 및 전처리
2. TF-IDF 방식으로 데이터 벡터화
3. 코사인 유사도를 통한 텍스트 간 유사도 계산 및 상위 유사 항목 도출
4. 상위 유사 텍스트 중 가장 자주 등장하는 법령명 분석
5. 법령 최적화를 위해 다양한 n-gram 과 텍스트 전처리 기법 활용

<br>

# 데이터 수집 및 전처리

<div style="display: flex; justify-content: center;">

  <!-- 법령 본문 데이터 -->
  <table border="1" style="width: 45%;">
    <tr>
      <th>법령일련번호</th>
      <th>Title</th>
      <th>Contents</th>
    </tr>
    <tr>
      <td>253949</td>
      <td>Purpose</td>
      <td>Article 1 (Purpose) The purpose of this Act is to strengthen the national capacity to rescue and provide emergency medical services, protect the lives, bodies, and property of the people, and contribute to the improvement of the quality of lives of the people by prescribing necessary matters concerning the efficient operation of 119 rescue and emergency medical services in the cases of fire, disaster, accident, terrorism, or other emergencies.</td>
    </tr>
  </table>

  <!-- 기본 정보 데이터 -->
  <table border="1" style="width: 45%;">
    <tr>
      <th>법령일련번호</th>
      <th>법령명한글</th>
      <th>법령명영문</th>
      <th>소관부처명</th>
      <th>법령구분명</th>
    </tr>
    <tr>
      <td>253949</td>
      <td>119구조ㆍ구급에 관한 법률</td>
      <td>ACT ON 119 RESCUE AND EMERGENCY MEDICAL SERVICES</td>
      <td>소방청, 소방청, 소방청, 소방청, 소방청</td>
      <td>법률</td>
    </tr>
  </table>

</div>

- 국가법령정보 공동활용의 영문법령 API를 활용하여 추출 : [링크](https://law.go.kr/engLsSc.do?menuId=1&subMenuId=21&tabMenuId=117&query=)
- 법령 본문과 기본정보로 분리해서 추출 / 총 2691개의 법령, 12만개의 조항 확인
- 법령 중 외국인 비대상 법령 제거
	 ↳  Ex:) 군사, 평창, 공무원, 전쟁, 운영, 국가 유공자, 공직자 … 등의 키워드를 포함한 법령
- 조항 내 의미 없는 키워드 제거(노이즈 제거)
	 ↳  Ex:) Definitions, Purpose, decree, presidential 등 같은 단어가 반복적으로 등장, 높은 빈도로 나타남(중요한 키워드의 가중치를 낮추고 전체 모델의 성능 저하 우려)
- 불용어 제거
	 ↳  Ex:) and, is, it, by, the 등 과 같은 불용어 제거,  모델의 성능을 향상시키고, 처리 속도를 증가
 
<br>


# TF-IDF 유사도 모델



<br>


# 결과
<p align="center">
  <img src="https://github.com/user-attachments/assets/59ce11bb-6b1f-43d2-b2aa-ef8b251666db" width="800">
<p>
  
- 검색한 문장과의 유사도 검사를 통해 관련 법령 검색 (4가지 모델의 결과를 Voting 후 최종 결과 도출)

<br>

# 기대효과 및 Lesson and Learned

## 기대효과
- 외국인을 위한 맞춤형 법령 검색 시스템 구축을 통해, 외국인들이 법령을 쉽게 이해하고 관련 법령을 신속하게 찾을 수 있음
- 외국인 관련 법적 분쟁 및 범죄 발생을 줄이는 데 기여
- ML 및 DL 모델을 결합한 AI 시스템을 통해 법률 전문가들이 법령 검토 시간을 단축할 수 있음

## Lesson & Learned
- 데이터 전처리와 텍스트 처리의 중요성을 이해하고, 다양한 전처리 기법을 학습
- TF-IDF 및 코사인 유사도를 통한 텍스트 유사도 분석 과정에서 텍스트 데이터의 특성을 다루는 방법을 터득
- 머신러닝 및 딥러닝 모델을 결합하여 최적의 성능을 내기 위한 모델 선택과 튜닝의 중요성을 학습
