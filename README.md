# pisa_2018 데이터와 2018년 국가별 GDP의 상관관계 분석

## 개요
엘리스 AI 4기 2차 프로젝트 <문해한 하루> 를 진행하면서 문해력이 좋지 않은 경우 어떤 영향이 있는지, 왜 문해력을 키워야 하는지에 대한 근거를 찾고 싶었습니다.
> PISA는 국제 학생 평가를 위한 OECD의 프로그램입니다. PISA는 15세 아동의 읽기, 수학, 과학 지식과 기술을 사용하여 실생활의 문제를 해결하는 능력을 측정합니다.
> 출처 : [OECD](https://www.oecd.org/pisa/)

PISA의 세 분야중 읽기 테스트의 점수를 국가별 문해력의 정도라고 판단하였고 PISA의 Reading Score와 국가별 GDP 데이터를 비교하여 문해력과 GDP의 상관관계를 분석하였습니다.


## 데이터 출처
`Kaggle` 데이터셋을 사용하였습니다.
- [PISA scores 2006-2018](https://www.kaggle.com/datasets/prasertk/pisa-scores-20062018)
- [World GDP(GDP, GDP per capita, and annual growths)](https://www.kaggle.com/datasets/zgrcemta/world-gdpgdp-gdp-per-capita-and-annual-growths)

## 사용 라이브러리
- python
- numpy
- pandas
- matplotlib.pyplot
- seaborn
- scikit-learn

## 요약
데이터 분석 과정은
- 데이터셋 탐색
- 데이터셋 전처리
- 데이터 분석
- 데이터 시각화            

Kaggle에서 찾은 데이터셋을 전처리(불필요한 컬럼 제거, 국가명 통일, 데이터셋 형태 통일, 이상치 제거 등) 하였고        
`LinearRegression`과 `RANSACRegressor`를 사용하여 분석하고 시각화 하였습니다.

🔥 `RANSAC Regressor` 를 사용한 이유
> RANSAC은 전체 데이터 집합의 인라이어 하위 집합에서 매개 변수를 강력하게 추정하기 위한 반복 알고리즘이다.
> 출처: [scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.RANSACRegressor.html)

- PISA Score와 상관 없이 GDP가 높은 국가들(이상치) 에 영향을 크게 받지 않도록 Ransac 알고리즘을 사용
- 이상치를 제거하지 않아도 양의 상관관계가 나타남
- but 데이터 자체가 엄청 많은게 아니라서 이상치 제거도 병행해주었음


## 결과
- PISA Reading Score와 GDP와의 상관관계가 충분히 크게 나타났고 문해력이 높을수록 GDP도 높은 경향을 보여준다는 결과를 도출해냈습니다.
- 
![image](https://user-images.githubusercontent.com/55697800/171431893-35655eab-4a24-4cd5-882b-779ce90b68d0.png)


## 한계 및 의의
- PISA가 15세 청소년을 대상으로 한 테스트이기 때문에 청소년들의 문해력이 높은 것이 GDP에 큰 영향을 끼친다고 명확하게 결론내리기 어렵습니다.
- PISA Reading Test가 문해력 정도를 확실하게 나타내줄 수 있는 지표라고 할 수는 없습니다.
- 
