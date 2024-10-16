---
title: Geojson 사용 예시
date: 2023-10-03
authors:
  - admin
tags:
  - GIS
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'  
---

```
import pandas as pd
import folium
from folium.plugins import MarkerCluster
from geopy.geocoders import Nominatim
import json
import requests
 
 
REST_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxx"
data = pd.read_csv("대전광역시_온통대전 신청 가맹점 목록_20211130.csv",encoding = "EUC-KR")
jsonfile = open("동구.json", 'r', encoding = "UTF-8").read()
jsondata = json.loads(jsonfile)
 
# 카카오 api로 좌표를 찾고 없으면 geolocoder로 찾고 그래도 안되면 0,0 반환(경도-위도순)하는 함수 선언
def find_coord_kakao(address):
    def find_coord_geo(address):
        try:
            geolocoder = Nominatim(user_agent="South Korea", timeout=None)
            geo = geolocoder.geocode(address)
 
            return geo.longitude, geo.latitude
        except:
            return 0, 0
    try:
        url = "https://dapi.kakao.com/v2/local/search/address.json?query={address}".format(address = address)
        headers = {"Authorization": f"KakaoAK {REST_API_KEY}"}
        result = json.loads(str(requests.get(url, headers=headers).text))
        coord = result["documents"][0]["address"]
        return float(coord["x"]), float(coord["y"])
    except:
        return find_coord_geo(address)
 
data = data[data['구'] == '동구']      # 불러온 csv에서 "동구"만을 선택해 데이터프레임을 갱신
 
 
data['주소'] = data['주소'].str.split(',').str.get(0)       # 도로명주소만을 골라내기 위해 문자열 슬라이싱
data['주소'] = data['주소'].str.split('(').str.get(0)
data.reset_index(inplace = True, drop = True)                            # 인덱스 리셋
data = data.drop(["구", "순번", "index"], axis = "columns")        # 구, 순번, index 컬럼을 지움
 
for i in data.index:                                    # 위에서 선언한 함수를 이용해 새로 생성한 경도, 위도 컬럼 입력
    data.loc[i, "경도"] = find_coord_kakao(data.loc[i, "주소"])[0]
    data.loc[i, "위도"] = find_coord_kakao(data.loc[i, "주소"])[1]
    print(i)
data = data.drop(data[data["경도"] == 0].index, axis = 1)           # 경도가 0인(도로명 주소를 찾지 못한) 데이터 행 삭제
 
 
 
home_address = input("도로명 주소를 입력하세요")               # 입력받은 도로명 주소를 좌표로 변환해서 그를 중심좌표로 맵을 생성
home_coord = find_coord_kakao(home_address)
 
m = folium.Map(location = [home_coord[1], home_coord[0]], zoom_start = 11)  # foium은 위도 경도 순으로 받아서
 
marker_cluster = MarkerCluster().add_to(m)  # cluster를 모을 것을 만듦(마커들의 집합을 만듦)
 
for i in data.index:                    # 마커 클러스트라는 집합 안에 좌표로 찍은 마커를 넣음
  folium.Marker(location = [data.loc[i, "위도"], data.loc[i, "경도"]], popup = "<pre>" + data.loc[i, "가맹점"] + "</pre>", icon = folium.Icon(color = "orange", icon = "glyphicon glyphicon-shopping-cart"),
  ).add_to(marker_cluster)
 
 
data = pd.DataFrame(data.groupby("동")["가맹점"].count())       # 동을 기준으로 그룹화하여 가맹점 수를 카운트
 
data.reset_index(inplace = True)    # 인덱스 리셋(데이터프레임을 갱신할 때 마다 해주면 좋다) 그래야 loc 쓸 때 편함
 
data = data.rename(columns = {"동" : "EMD_NM"})  # 편의를 위해 열 이름을 EMD_NM로 바꿈
 
for i in data.index:                                        # 가맹점수를 일반 int형으로 바꾸는 과정 (map이 안돼서 이렇게 함)
    data.loc[i, "가맹점"] = str(data.loc[i, "가맹점"])
for i in data.index:
    data.loc[i, "가맹점"] = int(data.loc[i, "가맹점"])
 
 
folium.Choropleth(geo_data = jsondata,         # columns = ["EMD_NM" <-와 key_on = 'feature.properties.EMD_NM' <-의 타입이 맞아야 된다
                  data = data,
                  columns = ["EMD_NM", "가맹점"],
                  fill_color='BuPu',
                  key_on = 'feature.properties.EMD_NM').add_to(m)
 
m.save("끝ㅋㅋ.html")
```

마음에 드는 geojson파일을 못찾겠으면 shp를 찾아서 변환해서 쓰자