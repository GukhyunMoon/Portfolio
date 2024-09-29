# 지역별 음식 유행에 따른 상권 분석

💭 Language : Python

🛠 Tool : Jupyter Notebook (Local)

📅 진행기간 : 2024.05.02 ~ 2024.05.30

👥 인원 : 5명

---------------------------------------------------------------------------------

## 프로젝트 개요

    - 코로나19 이후 국내 외식업체 폐업률 증가, 총 가게수 약 269만개 중 66.72% 비율로 절반 이상 문을 닫았음  
    - 음식점이 문닫는 기간은 평균 3.1년, 지역별 어느 음식 유형이 유행하는지 파악해서 전략 수집

<img src="https://github.com/user-attachments/assets/e2b6955d-e464-4566-975d-d6b0d09c6be0" width="1200">


## 주요 역할
- 데이터 수집 및 전처리(읍,면,동 컬럼을 세분화하여 법정동, 행정동으로 분리, [PublicDataReade](https://wooiljeong.github.io/python/pdr-code/) 모듈 사용)
- 탐색적 데이터 분석(EDA)을 위해 PCA(주성분 분석)를 사용, 주요 변수 간 관계 탐색
- KMeans 클러스터링을 통해 지역별 음식 유형의 특성을 군집화하여 중요 인사이트 도출


## 데이터 수집

<div style="display: flex; justify-content: space-around;">
  <img src="https://github.com/user-attachments/assets/7f722e58-ffa0-4d4a-add5-e3b7b1f61a71" width="500" alt="이미지 1">
  <img src="https://github.com/user-attachments/assets/2df9e697-8c60-4c9b-844c-50a1665de1aa" width="500" alt="이미지 2">
</div>

- 공공 데이터 포털에서 일반 음식점, 휴게음식점 개 폐업 데이터 활용
- 지역별 최근값, 최대치, 최소치일자, 최대치일자, 음식점 종류별, 법정동 데이터 생성


## 데이터 전처리

<div style="display: flex; justify-content: space-around;">
  <img src="https://github.com/user-attachments/assets/6abfcf80-ee4b-46ab-85f0-9fa2908a38d7" width="500" alt="이미지 1">
  <img src="https://github.com/user-attachments/assets/bf554593-f60a-4e9b-b7cc-ff1676de0716" width="500" alt="이미지 2">
</div>

- 기존 데이터 : 지역별 편차가 크고 표준화가 되어있지 않음
- 해당 지역을 총 음식점 당 가게수로 대체 > 지역별 편차 최소화
- 읍면동 컬럼에서 법정동, 행정동 분리
- 법정동 이름과 행정동 이름이 같은 지역은 법정동 이름을 할당
- 법정동, 행정동 데이터가 섞여 있기에 분리 시켜 결측치 방지
  

## EDA(탐색적 데이터 분석)
### 1) 지역별(광역) 가장 많은 음식점 유형, 인구수 확인
<img src="https://github.com/user-attachments/assets/160e49b4-a369-4186-9976-fa21da006357" width="500">
<img src="https://github.com/user-attachments/assets/26d769e2-5864-446c-a50a-860f295e2674" width="500">

- 지역별 치킨매장이 가장 많은걸로 확인된다. 
- 지역별 남여 인구수 확인 결과 서울, 부산, 대구, 광주, 전북, 대전, 인천 등은 여자 인구가 많다.

### 2) 변수 데이터 간 상관관계 확인
<p align="center">
    <img src="https://github.com/user-attachments/assets/8aecf871-0f19-42cf-895a-ac98cda38428" width="500">
</p>

### 3) PCA

<table>
  <tr>
    <td>
      <table border="1">
        <tr>
          <th>요인</th>
          <th>긍정적인 요인</th>
          <th>부정적인 요인</th>
        </tr>
        <tr>
          <td><strong>요인 1</strong></td>
          <td>마라 <br> 탕후루 <br> 와플 <br> 공차 <br> 토스트</td>
          <td>국밥 <br> 추어탕 <br> 횟집 <br> 분식 <br> 식당</td>
        </tr>
        <tr>
          <td><strong>요인 2</strong></td>
          <td>식당 <br> 분식 <br> 횟집 <br> 국밥 <br> 칼국수</td>
          <td>마라 <br> 호프 <br> 훠궈 <br> 꼬치 <br> 양꼬치</td>
        </tr>
        <tr>
          <td><strong>요인 3</strong></td>
          <td>전체 <br> 포케 <br> 샐러드 <br> 파스타 <br> 베이글</td>
          <td>김밥 <br> 국밥 <br> 분식 <br> 통닭 <br> 치킨</td>
        </tr>
        <tr>
          <td><strong>요인 4</strong></td>
          <td>국밥 <br> 횟집 <br> 아구찜 <br> 한솥 <br> 지코바</td>
          <td>냉면 <br> 삼겹살 <br> 호프 <br> 해장국 <br> 순대</td>
        </tr>
      </table>
    </td>
    <td>
      <img src="https://github.com/user-attachments/assets/cb35bf5b-bdb4-416a-9cd5-a57791211083" width="600">
    </td>
  </tr>
</table>

- 목적 : 로딩 값을 추출하여 특정 지역에서는 인기 있는 음식점 유형 파악, 주요 요인 도출
- 주성분 4개의 누적 설명 분산 비율이 약 81.4% 로 데이터의 주요 변동성을 충분히 설명
- 주성분 5개 이상 선택 시 누적 설명 분산 비율이 약 90% 이상 증가 하지만 설명력 향상 대비 모델의 복잡성 증가가 크다고 판단
- 각 요인 추출

### 4) KMeans 클러스터링
<p align="center">
    <img src="https://github.com/user-attachments/assets/7b1c110e-62eb-4c91-a0cd-709b4d876ebf" width="600">
</p>

- 목적 : 유사한 특성을 가진 지역을 군집화, 각 군집의 특성 분석
- 엘보우 방법을 사용해 최적의 클러스터 개수 결정 = 5

### 5) 클러스터링 시각화
<p align="center">
    <img src="https://github.com/user-attachments/assets/460f0a81-4a5b-4643-b5e6-0e4db07b69ea" width="800">
<p>

- 클러스터 0 (C0) : 10대 비율이 높은 지역, 학원가가 많아 10대 학생들이 몰려있음. (대표 지역 : 경기도 고양시 일산동구 백석동)
- 클러스터 1 (C1) : 지하철 근처에 있는 지역, 교통이 편리하여 주거지나 상업지구로 인기가 높음 (대표 지역 : 서울시 마포구 상암동)
- 클러스터 2 (C2) : 군부대 근처, 터미널 환승센터가 주변에 있음 (대표 지역 : 충청남도 계룡시 엄사면)
- 클러스터 3 (C3) : 공항 근처나 대학과 관련된 상업 활동이 활발한 지역. (대표 지역 : 서울시 강서구 방화동, 공항동) 
- 클러스터 4 (C4) : 다양한 특성을 가진 지역, 주로 시골일 가능성이 매우 높음 (대표 지역 : 경상북도 구미시 옥계동)


## 결과

<img src="https://github.com/user-attachments/assets/3dc945d4-ed65-4c87-ab1d-568491ca18f0" width="800">

- OLS 회귀 분석 : 각 요인별 독립 변수들이 종속 변수(음식점 밀도)에 미치는 영향을 평가하고 이를 바탕으로 상권을 예측
- TOP 3 와 Worst 3 지역 도출 : 실제 값과 예측 값 차이가 큰 기준으로 선정

- 주요 유행 음식 : 식당, 분식, 횟집, 국밥, 칼국수
- 주요 영향 변수 : 30대 비율, 40대 비율, 인구
- 결론 : 40대 비율이 높은 지역일수록 식당, 분식 등의 음식점 유형이 유행할 가능성이 크다


## 기대효과 및 Lesson and Learned

### 기대효과
- 지역별 음식 소비 패턴 분석을 통해 상권별 맞춤형 마케팅 전략 수립 가능
- PCA와 클러스터링을 통해 상권 특성을 구체적으로 파악함으로써, 상권별로 최적화된 비즈니스 의사결정 지원
- 음식점 창업이나 상권 분석을 위한 인사이트 제공, 지역 특성에 맞춘 메뉴 구성 및 고객 타겟팅에 활용 가능

### Lesson and Learned
- 고차원 데이터를 효율적으로 축소하여 분석할 수 있는 PCA 기법의 중요성을 습득
- 데이터의 분포와 패턴을 이해하는 데 있어 클러스터링의 유용성을 경험, 군집별 특성을 분석하여 중요한 인사이트를 도출하는 방법 학습
- EDA 과정에서 데이터 전처리의 중요성을 인식하고, 전처리 단계가 결과에 미치는 영향에 대해 깊이 이해
