---
title: Pandas 자주 쓰이는 메소드 정리
date: 2023-10-03
authors:
  - admin
tags:
  - Pandas
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'  
---

### 정보 확인하기

```
df.info()
```

### 컬럼 형변환

```
df = df.astype({'month' : 'int', 'week' : 'int'})
```

### 행 자르기

```
df = df[1:10]
```

### 결측치 제거

```
df = df.dropna(axis = 0) 행 전체 제거
df = df.dropna(axis = 1) 열 전체 제거
df = df.dropna(subset = ['컬럼명'], how = 'any', axis = 0) 특정 컬럼에 nan있는 행 제거
```

### 컬럼명 변경

```
df.columns = ['컬럼명1', '컬럼명2', '컬럼명3'] 컬럼명 전부 써줘야 됨
df.rename(columns = {'원래컬럼명' : '바꿀컬럼명'}, inplace = True) 지정 변경
```

### 컬럼 피쳐 항목 확인

```
print(pd['컬럼명'].unique())
```

### 레이블 인코딩

```
from sklearn.preprocessing import LabelEncoder
df['컬럼명'] = LabelEncoder().fit_transform(df['컬럼명'].values)
```

### 원 핫 인코딩

```
temp = pd.get_dummies(df['컬럼명'])
```

### 데이터프레임 세로로 합치기 병합

```
result = pd.concat([df1, df2], axis = 0) join = 'inner/outer' 가능
```

### 데이터프레임 가로로 합치기 병합

```
result = pd.concat([df1, df2], axis = 1) join = 'inner/outer' 가능
```

### 데이터프레임 특정 키를 기준으로 합치기 병합

```
df_result = pd.merge(df1, df2, how = 'outer')
```

### 데이터프레임 인덱스 초기화

```
df.reset_index(drop = True, inplace = True)
```

### 컬럼을 인덱스로 사용

```
df.set_index('컬럼명', inplace=True)
```

### 특정 컬럼 제거

```
df.drop('컬럼명', axis = 1, inplace = True)
```

### 표준화(StandardScaler) 피쳐별 평균0 분산1 가우시안 정규분포인 넘파이 배열로 변환

```
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(df)
df_scaled = scaler.transform(df)
```

### 정규화(MinMaxScaler) 피쳐별로 0~1 사이의 값으로 정규화

```
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
scaler.fit(df)
df_scaled = scaler.transform(df)
```

### ndarray <-> 데이터프레임 변환

```
arr = np.array(df)
df = pd.DataFrame(data = arr)
```

### 0으로 채워진 n차원 배열 생성

```
arr = np.zeros()
```

### 넘파이 데이터 차원 확인

```
print(arr.shape)
```

### 데이터프레임 그룹화

```
pd.groupby(by = '컬럼명')
pd.groupby(level = '인덱스')
```

### 위치 기반 인덱싱

```
df.iloc[2:5]
```

### 레이블 기반 인덱싱

```
df.loc['값 또는 컬럼명']
```

### 데이터 정렬

```
df.sort_values('컬럼명', ascending = True/False) 오름치순/내림차순
```

### 랜덤 표본 추출

```
temp_df = df.sample(frac = 0.5) 1/2 크기의 랜덤 표본 추출
temp_df = df.sample(n = 10) 10줄의 랜덤 표본 추출
```

### 특정 표본 추출

```
temp_df = df.nlargest(n, 'value’) 개수, 기준값
temp_df = df.nsmallest(n, 'value') 개수, 기준값
temp_df = df.head(n) 맨 앞 몇개
temp_df = df.tail(n) 맨 뒤 몇개
```

### 정규표현식 이용 추출

```
temp_df = df.filter(regex = 'regex')
정규표현식
'\.' : Matches strings containing a period '.'
'문자열$' : '문자열'로 끝나는 값
'^문자열' : '문자열'로 시작하는 값
'^x[1-5]$' : x로 시작하고 1,2,3,4,5로 끝나는 값
'^(?!Species$).*' : Matches strings except the string 'Species'
```

### 결측치 채우기

```
df.fillna(value) 널 값을 value로 치환.
```

### 상관계수

```
df.corr(method = 'pearson')
df.corrwith(other_df, axis = 0, drop = False, method = 'pearson')
method 종류 : pearson, kendall tou, spearman
```

### 메소드체이닝 예시

```
df['컬럼명'] = df['컬럼명'].strip.replace('바꾸고싶은 문자열', '바꿀 문자열').get([0])```
