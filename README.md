# ML_team4_Tow-of-PM-Analysis
위치 데이터를 기반으로 한 전동 킥보드 견인 위치의 환경적 원인 및 특성 탐색<br/>

### 🛴 킥킥 - 위치 데이터를 기반으로 한 전동 킥보드 견인 위치의 환경적 원인 및 특성 탐색 <br/>
![image](https://github.com/khuda-5th/ML_team4_Tow-of-PM-Analysis/assets/70475010/384ece5c-8123-46b7-89b3-8a0f910ca93d)



### 💡주제 선정

우리가 쉽게 사용할 수 있는 킥보드는 우리에게 편의성을 주는 동시에 불편함도 가져온다. 무분별하게 주차된 킥보드들은 보행자의 통행을 방해하거나 차량 주차에 피해를 준다. 대부분의 킥보드 기업은 이용의 편리성과 반납의 효율성을 생각해 킥보드 거치대를 설치하지 않는다고 한다. 하지만, 무분별하게 주차된 킥보드로 인해 피해를 입고, 견인 신청하는 사례가 정말 많았기에 이를 바탕으로 견인된 위치의 특징을 분석하여 거치대 설치를 위한 인사이트를 도출하고자 한다.<br/><br/>

### 👨‍💻 팀원

| 팀원 | 역할 |
| --- | --- |
| 김민서 | 아이디어 빌딩, 데이터 전처리, 데이터 시각화 |
| 김민아 | 아이디어 빌딩, 모델링, 하이퍼파라미터 튜닝 |
| 박진우 | 아이디어 빌딩, 모델링,  하이퍼파라미터 튜닝 |
| 이소연 | 아이디어 빌딩, 모델링,  하이퍼파라미터 튜닝 |
| 이승준 | 아이디어 빌딩,데이터 전처리, 데이터 시각화 |
| 지인태 | 아이디어 빌딩,데이터 전처리, 데이터 시각화 |
| 황종훈 | 아이디어 빌딩, 모델링,  하이퍼파라미터 튜닝 |


### 📍Data
- [서울특별시 전동킥보드 견인 현황](https://data.seoul.go.kr/dataList/OA-21304/S/1/datasetView.do)<br/>
- [서울시 지하철역 엘리베이터 위치정보](https://data.seoul.go.kr/dataList/OA-21212/S/1/datasetView.do)<br/>
- [서울시 버스정류소 위치정보](https://data.seoul.go.kr/dataList/OA-15067/S/1/datasetView.do)<br/>
- [서울시 상권분석서비스(길단위인구-상권배후지)](https://data.seoul.go.kr/dataList/OA-15582/S/1/datasetView.do)<br/>
- 카카오맵 API<br/><br/>

### 🤝 프로젝트 진행 과정

**1. 데이터 전처리** <br/><br/>

![image](https://github.com/khuda-5th/ML_team4_Tow-of-PM-Analysis/assets/70475010/9780479f-b369-479f-8815-d102867b168c)
![image](https://github.com/khuda-5th/ML_team4_Tow-of-PM-Analysis/assets/70475010/947e77cb-93bc-4584-ac85-bbfa72a7a943)
![image](https://github.com/khuda-5th/ML_team4_Tow-of-PM-Analysis/assets/70475010/050f9e20-0ada-48bf-a13e-19a81d62610e)
- 견인 위치 데이터셋의 지번 위치를 위경도로 변환 <br/>
- 버스정류장 데이터셋 & 지하철 위치 데이터셋 시각화 <br/>
- 견인 위치가 중복됨을 확인, 이를 횟수로 계산한 Column 추가 <br/>
- 견인 유형 EDA, 견인 위치 시각화 <br/>
- 지하철과의 거리, 버스정거장과의 거리, 행정동, 거주 인구수, 유동인구수, 상권과의 거리, 상권 유동인구수, 500m 내의 상권 갯수, 고등학교 대학교 갯수를 계산한 Column 추가 <br/><br/>


**2. 모델링**<br/><br/>
![image](https://github.com/khuda-5th/ML_team4_Tow-of-PM-Analysis/assets/70475010/9a9d06b8-2722-49a4-97c1-13e9f4c8c316)
![image](https://github.com/khuda-5th/ML_team4_Tow-of-PM-Analysis/assets/70475010/38490343-aa3d-48b7-8f3c-09ed11fb2d02)
- 결정 트리, PCA, K평균 클러스터링 사용
- 결정트리: 견인 횟수가 30번 이상인 지역과 그렇지 않은 지역을 타깃으로 설정, 이를 통해 어떤 특성이 모델링에 가장 큰 영향 미치는지 파악
- PCA & k평균 클러스터링: PCA를 통해 설명된 분산 값이 85%인 주성분 5개 설정, 변환된 데이터셋으로 K평균 클러스터링 진행 <br/>
엘보우 기법을 통해 가장 적절한 k값 설정, 클러스터링 결과를 원본 데이터셋에 합성 <br/>


**4. 결과 분석**<br/><br/>
![image](https://github.com/khuda-5th/ML_team4_Tow-of-PM-Analysis/assets/70475010/0afd76ff-ff74-4aa7-90e5-d55ddfb4c3df)

- 결정 트리 및 클러스터링 결과에 따른 column값 시각화 <br/>
- 결정 트리 특성별 중요도: 연간 유동인구 > 상권과의 거리 > 거주 인구수 > 반경 500m 내 상권 개수 > 버스 정거장 거리 <br/>
- 지하철 역, 버스 정류장, 상권의 개수는견인 위치와 상관 관계 존재 <br/>


