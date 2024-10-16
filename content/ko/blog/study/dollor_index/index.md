---
title: 달러인덱스와 환율의 상관계수 및 그래프 그리기
summary: 달러인덱스와 환율 간 상관계수를 구하고, 그래프를 그리는 과정을 소개합니다.
date: 2023-10-03
authors:
  - admin
tags:
  - Pandas
  - Data Analysis
  - Python
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'  
---

```  
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import matplotlib
 
matplotlib.rcParams["font.family"] = "Malgun Gothic"            # 한글, -깨짐방지
matplotlib.rcParams["font.size"] = 15.0                         # 플롯 기본 폰트사이즈 설정
matplotlib.rcParams["axes.unicode_minus"] = False
 
 
dollar_index = pd.read_csv("C:\PycharmProjects\달러인덱스전체.csv", encoding="UTF-8")  # 달러인덱스 데이터 읽어옴
dollar_index = dollar_index.drop(columns=["Unnamed: 0"])                            # 이상한 컬럼 붙어있어서 지움
 
krw_dollar = pd.read_csv("C:\PycharmProjects\환율전체.csv", encoding="UTF-8")   # 환율 데이터 읽어옴
krw_dollar.dropna(inplace=True)                                               # 결측데이터 행 제거
krw_dollar["환율"] = krw_dollar["환율"].str.replace(",", "")                    # 천단위 ,기호 제거
krw_dollar.rename(columns = {"날짜" : "Date"}, inplace=True)                   # merge시의 편의를 위해 컬럼명을 Date로 통일
krw_dollar["환율"] = pd.to_numeric(krw_dollar["환율"], errors = "coerce")       # str->int로 타입변환
krw_dollar.reset_index(inplace=True, drop=True)                               # 인덱스 초기화
 
 
entire = pd.merge(dollar_index, krw_dollar, how = "inner")                    # 달러인덱스와 환율을 Date를 기준으로 병합
entire.reset_index(inplace=True, drop=True)                                   # inner로 병합했으니 인덱스 초기화
entire.rename(columns = {"Close" : "Dollar index"}, inplace=True)
 
 
for i in entire.index:          # 전일대비환율변화율을 구함. 변화율이 0인경우 /가 안되기때문에 에러 발생하므로 if문으로 케이스 분류
    try:                        # entire.index라서 인덱스 끝에서 한번 더 실행되는데 이때 에러 무시하기 위해 except-break
        i += 1
        if entire.loc[i, "환율"] != entire.loc[i-1, "환율"]:
            entire.loc[i, "전일대비환율변화율"] = (entire.loc[i, "환율"] - entire.loc[i-1, "환율"]) / entire.loc[i-1, "환율"]
        else:
            entire.loc[i, "전일대비환율변화율"] = 0
    except:
        break
entire.dropna(inplace = True)
entire.reset_index(inplace = True, drop = True)
q1_c_ratio = entire["전일대비환율변화율"].quantile(0.25)         # 1사분위값
q2_c_ratio = entire["전일대비환율변화율"].quantile(0.5)          # 2사분위값
q3_c_ratio = entire["전일대비환율변화율"].quantile(0.75)         # 3사분위값
iqr_c_ratio  = q3_c_ratio - q1_c_ratio                       # 박스 범위를 3사분위값-1사분위값으로 설정
 
upper_abnormal = entire["전일대비환율변화율"]>q3_c_ratio+1.5*iqr_c_ratio     # 윗쪽 이상치 제거
upper_abnormal_index = entire[upper_abnormal].index
entire.drop(upper_abnormal_index, inplace=True)
 
lower_abnormal_c_ratio = entire["전일대비환율변화율"]<q1_c_ratio-1.5*iqr_c_ratio     # 아랫쪽 이상치 제거
lower_abnormal_index_c_ratio = entire[lower_abnormal_c_ratio].index
entire.drop(lower_abnormal_index_c_ratio, inplace=True)
 
entire.reset_index(inplace=True, drop=True)         # 이상치 제거했으니 인덱스 리셋
 
for i in entire.index:      # 위와 같음
    try:
        i += 1
        if entire.loc[i-1, "Dollar index"] != entire.loc[i, "Dollar index"]:
            entire.loc[i, "전일대비달러인덱스변화율"] = (entire.loc[i, "Dollar index"] - entire.loc[i-1, "Dollar index"]) / entire.loc[i-1, "Dollar index"]
        else:
            entire.loc[i, "전일대비달러인덱스변화율"] = 0
    except:
        break
 
q1_d = entire["전일대비달러인덱스변화율"].quantile(0.25)    # 위와 같음
q2_d = entire["전일대비달러인덱스변화율"].quantile(0.5)
q3_d = entire["전일대비달러인덱스변화율"].quantile(0.75)
iqr_d  = q3_d - q1_d
 
upper_abnormal_d = entire["전일대비달러인덱스변화율"]>q3_d+1.5*iqr_d
upper_abnormal_index_d = entire[upper_abnormal_d].index
entire.drop(upper_abnormal_index_d, inplace=True)
 
lower_abnormal_d = entire["전일대비달러인덱스변화율"]<q1_d-1.5*iqr_d
lower_abnormal_index_d = entire[lower_abnormal_d].index
entire.drop(lower_abnormal_index_d, inplace=True)
 
 
entire.dropna(inplace=True)
entire.reset_index(inplace=True, drop=True)
entire = entire.drop(["전일대비환율변화율", "전일대비달러인덱스변화율"], axis = "columns")
 
 
 
entire = entire[8092:8256]              # 구하고자 하는 구간의 범위를 설정하는 곳
corr = entire.corr(method = "pearson")      # 피어슨 상관계수 구하기
#imf 3713:4024          # 확인하기 귀찮아서 메모해놓은 구간 인덱스
#지금 8092:8256
 
# 산포도 그리고 싶으면 이걸 쓰세요
'''entire.plot(kind='scatter',x="환율",y="Dollar index")
plt.show()'''
 
 
 
plt.rcParams["figure.figsize"] = (30,13)
plt.rcParams["lines.linewidth"] = 2         #플롯 내 선 굵기
 
x1 = entire["Date"]
y1 = entire["Dollar index"]
 
x2 = entire["Date"]
y2 = entire["환율"]
 
plt.title("달러인덱스 & 환율", size = 20)
plt.xlabel("날짜", fontdict = {"size" : 15})
plt.xticks(np.arange(0, len(entire.index)+1, 8), rotation = 45)
ax = plt.plot(x1, y1, color = "black", label = "달러인덱스")
plt.ylabel("달러인덱스", color = "black", fontdict = {"size" : 15})
plt.tick_params(axis = "y", labelcolor = "black")
 
y_right = plt.twinx()
plt.xticks(np.arange(0, len(entire.index)+1, 8), rotation = 45)
ax2 = y_right.plot(x2, y2, color = "red", label = "환율")
plt.ylabel("환율", color = "red", fontdict = {"size" : 15})
y_right.tick_params(axis = "y", labelcolor = "red")
 
plt.legend(handles = ax + ax2, loc = "best")
 
plt.show()

```

처음 데이터셋으로 받아온 달러인덱스와 환율에서 이상치를 제거하기 위해 각 항목의 전일대비변동률을 따로 구해준 뒤, 변동률을 기준으로 박스플롯을 이용해 이상치를 제거하였다.



달러인덱스와 환율이 일 단위 시간변화에 따라 연속적인 값을 가지는 데이터기 때문에 원데이터에서 이상치를 제거하면



첫째로 위에서 구현한 코드대로라면 상관계수를 구하거나 그래프를 그리는 과정에서 시간변화를 고려하지 않기 때문에 절대적으로 값의 낮고 높음만으로 이상치를 판단하게 됨

둘째로 연속적인 값임을 고려하지 않기 때문에 한 구간을 이상치로 판단하여 제외하게 되면 그 다음 구간도 높은 확률로 이상치가 되어 어떤 특정 구간이 통째로 이상치로 판단되어 날아감

와 같은 문제가 발생하기 때문이다.





또 그래프 그릴 때 각각의 y축 값을 따로 설정하는 과정에서 좀 헤맸는데

x-y1의 그래프(위에선 ax)와 x-y2의 그래프(위에선 ax2)를 그리고 plt.twinx()로 각각의 그래프가 x축을 공유하도록 설정해주면 된다.

이 때 범례를 x-y1, x-y2에서 따로 잡아주면 같은 위치에 겹쳐서 그려지는데, x축을 공유하도록 설정한 후

```  
plt.legend(handles = ax + ax2, loc = "best")
```

이렇게 handles로 범례 표시할 그래프를 잡아주면 알아서 잘 표시해준다.


