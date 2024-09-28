# 지역별 음식 유행에 따른 상권 분석

💭 Language : Python

🛠 Tool : Jupyter Notebook (Local)

📅 진행기간 : 2024.05.02 ~ 2024.05.30

👥 인원 : 5명

---------------------------------------------------------------------------------

## 프로젝트 개요
- 코로나19 이후 국내 외식업체 폐업률 증가, 총 가게수 약 269만개 중 66.72% 비율로 절반 이상 문을 닫았음
- 음식점이 문닫는 기간은 평균 3.1년, 지역별 어느 음식 유형이 유행하는지 파악해서 전략 수집


## 프로세스

<img width="1228" alt="image" src="https://github.com/user-attachments/assets/dd9a5c1b-0853-4b62-b50a-a6adaa92951f">" width="800">


## 주요 역할
- 1. 데이터 수집 및 전처리(읍,면,동 컬럼을 세분화하여 법정동, 행정동으로 분리, [PublicDataReade](https://wooiljeong.github.io/python/pdr-code/) 모듈 사용)
- 2. 탐색적 데이터 분석(EDA)을 위해 PCA(주성분 분석)를 사용, 주요 변수 간 관계 탐색
- 3. KMeans 클러스터링을 통해 지역별 음식 유형의 특성을 군집화하여 중요 인사이트 도출


## 데이터 수집

<div style="display: flex; justify-content: space-between;">

<table>
  <tr>
    <th>개방서비스명</th>
    <th>인허가일자</th>
    <th>영업상태명</th>
    <th>상세영업상태명</th>
    <th>폐업일자</th>
  </tr>
  <tr>
    <td>휴게음식점</td>
    <td>2023.11.24</td>
    <td>폐업</td>
    <td>폐업</td>
    <td>2023.12.14</td>
  </tr>
  <tr>
    <td>휴게음식점</td>
    <td>2023.11.20</td>
    <td>폐업</td>
    <td>폐업</td>
    <td>2023.12.07</td>
  </tr>
  <tr>
    <td>휴게음식점</td>
    <td>2023.11.20</td>
    <td>폐업</td>
    <td>폐업</td>
    <td>2023.11.22</td>
  </tr>
</table>

<table>
  <tr>
    <th>광역</th>
    <th>시군구</th>
    <th>읍면동</th>
    <th>추이당</th>
    <th>recent2</th>
    <th>닭갈비 recent2</th>
    <th>오리 recent2</th>
  </tr>
  <tr>
    <td>강원도특별자치도</td>
    <td>강릉시</td>
    <td>강동면</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>강원도특별자치도</td>
    <td>강릉시</td>
    <td>강문동</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>강원도특별자치도</td>
    <td>강릉시</td>
    <td>견소동</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
</table>

</div>

- 공공 데이터 포털에서 일반 음식점, 휴게음식점 개 폐업 데이터 활용
- 지역별 최근값, 최대치, 최소치일자, 최대치일자, 음식점 종류별, 법정동 데이터 생성


### 총 음식점 리스트
<img src="https://github.com/user-attachments/assets/350bf61c-17a1-4a7c-aef8-d757fe3f50a7" width="600">


## 데이터 전처리
- 기존 데이터 : 지역별 편차가 크고 표준화가 되어있지 않음
- 해당 지역을 총 음식점 당 가게수로 대체 > 지역별 편차 최소화
- 읍면동 컬럼에서 법정동, 행정동 분리
- 법정동 이름과 행정동 이름이 같은 지역은 법정동 이름을 할당
- 법정동, 행정동 데이터가 섞여 있기에 분리 시켜 결측치 방지
  

## EDA
<img src="https://github.com/user-attachments/assets/0d25f745-a1b5-4e1a-b2ef-ccff864e8dfc" width="500">
<img src="https://github.com/user-attachments/assets/13fd0928-3360-4091-8e13-2dab416e1f27" width="500">

- 광역시별 치킨매장이 제일 많다. 
- 광역시별 인구수 확인


## PCA 및 클러스터링
### 1. PCA
<img src="https://github.com/user-attachments/assets/cb35bf5b-bdb4-416a-9cd5-a57791211083" width="600">

- 목적 : 로딩 값을 추출하여 특정 지역에서는 인기 있는 음식점 유형 파악, 주요 요인 도출
- 주성분 4개의 누적 설명 분산 비율이 약 81.4% 로 데이터의 주요 변동성을 충분히 설명
- 주성분 5개 이상 선택 시 누적 설명 분산 비율이 약 90% 이상 증가 하지만 설명력 향상 대비 모델의 복잡성 증가가 크다고 판단

### KMeans 클러스터링
<img src="https://github.com/user-attachments/assets/7b1c110e-62eb-4c91-a0cd-709b4d876ebf" width="600">

- 목적 : 유사한 특성을 가진 지역을 군집화, 각 군집의 특성 분석
- 엘보우 방법을 사용해 최적의 클러스터 개수 결정 = 5





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
