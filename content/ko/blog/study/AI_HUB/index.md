---
title: AI Hub 데이터 bounding box 변환(json to txt)
date: 2023-10-03
authors:
  - admin
tags:
  - AI
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'  
---

## AI Hub에서 제공되는 데이터셋의 bounding box 좌표를 yolo에서 사용하는 형태로 변환

```
import re
import os
 
# 이미지 파일들 상위 디렉토리
input_dir = 'C:\yolov5\새 폴더'
 
file_list = os.listdir(input_dir)
 
json_name_list = [file for file in file_list if file.endswith('.Json')]
 
for i in range(len(json_name_list)):
    json_name_list[i] = input_dir + '/' + json_name_list[i]
 
for i in json_name_list:
    try:
        with open(i, 'r', encoding='UTF-8') as file:
            data = file.read().replace('\n', '')
        coord_list = list(map(int, re.findall(r'\d+', data.split('BOX')[1].strip())))
        for k in range(4):
            del coord_list[k]
        coord_list[1], coord_list[2] = coord_list[2], coord_list[1]
        size = list(map(int, (re.findall(r'\d+\*\d+', data)[0]).split('*')))
        category = re.findall('[가-힣]+', data.split('DETAILS')[1].split(',')[0])[0]
 
 
        def convert(size, coord_list):
            dw = 1. / size[0]
            dh = 1. / size[1]
            x = (coord_list[0] + coord_list[1]) / 2.0
            y = (coord_list[2] + coord_list[3]) / 2.0
            w = coord_list[1] - coord_list[0]
            h = coord_list[3] - coord_list[2]
            x = x * dw
            w = w * dw
            y = y * dh
            h = h * dh
            return (x, y, w, h)
 
 
        yolo_style = list(convert(size, coord_list))
        yolo_style.insert(0, category)
 
        result = ' '.join(map(str, yolo_style))
        output_file_name = i.split('.')[0] + '.txt'
        save_txt = open(output_file_name, 'w')
        save_txt.write(result)
        save_txt.close()
 
    except:
        print('오류')
        break
```

혹시 몰라서...

```
import re
import os
 
# Json 파일들 상위 디렉토리
input_dir = 'C:\PythonProjects\R.Free'
 
 
def convert(size, coord_list):
    dw = 1. / size[0]
    dh = 1. / size[1]
    x = (coord_list[0] + coord_list[1]) / 2.0
    y = (coord_list[2] + coord_list[3]) / 2.0
    w = coord_list[1] - coord_list[0]
    h = coord_list[3] - coord_list[2]
    x = x * dw
    w = w * dw
    y = y * dh
    h = h * dh
    return (x, y, w, h)
 
file_list = os.listdir(input_dir)
 
json_name_list = [file for file in file_list if file.endswith('.json')]
 
for i in range(len(json_name_list)):
    json_name_list[i] = input_dir + '/' + json_name_list[i]
 
count = 0
 
for i in json_name_list:
    output_file_name = i.split('.')[0] + '.txt'
    with open(i, 'r', encoding='UTF-8') as file:
        data = file.read().replace('\n', '')
    count_data = data.count('\"data\"')
    height = re.findall('\d+', data.split('height')[1].split(',')[0])
    width = re.findall('\d+', data.split('width')[1].split(',')[0])
    size = [width[0], height[0]]
    size =  list(map(int, size))
    data = data.split("bbox")[1]
    data_list = data.split("}")
    result = []
    for j in range(count_data):
        temp_data = data_list[j]
        data_name = temp_data.split('\"data\":')[1].split(',')[0]
        x_list = temp_data.split(',      \"y\": ')[0].split('"x": ')[1].replace('[', '').replace(']', '').replace(' ', '').split(',')
        y_list = temp_data.split(',      \"y\": ')[1].replace('[', '').replace(']', '').replace(' ', '').split(',')
        coord_list = [x_list[0], x_list[-1], y_list[0], y_list[-1]]
        coord_list =  list(map(int, coord_list))
        yolo_style = list(convert(size, coord_list))
        yolo_style.insert(0, data_name)
        result.append(' '.join(map(str, yolo_style)))
 
    for n in range(len(result)):
        result[n] = result[n].strip()
 
 
    with open(output_file_name, 'w+') as lf:
        lf.write('\n'.join(result))
 
    with open(output_file_name, 'r') as lf:
        readList = lf.readlines()
```

