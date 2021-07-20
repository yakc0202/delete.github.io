---
title: "Series 실습"
date: 2021-07-19 -0400
categories: 
- Pandas
tags:
- [데이터 청년 캠퍼스, Pandas]

toc: true
---

```py  
from pandas import Series  
sample = Series([85, 90, 75, 55, 45, 90, 95, 85, 90, 100], 
               index = ['a','b','c','d','e','f','g','h','i','j'])  
```  

## 앞에 5개의 데이터에는 5를 더하고, 나머지 5개의 데이터에는 10을 더하라  

```py  
sample.add([5,5,5,5,5,10,10,10,10,10])  

Out:  
a     90  
b     95  
c     80  
d     60  
e     50  
f    100  
g    105  
h     95  
i    100  
j    110  
dtype: int64  
```  

## sample 데이터 내에 80이 있는지 확인하여 있으면 True, 없으면 False를 출력  

- ```py  
  80 in sample.values  
  ```  
- ```py  
  sample.isin([80])  
  ```  

## sample의 인덱스 내에 'h'가 있는지 확인하여 있으면 True, 없으면 False를 출력  

```py  
'h' in sample.index  
```  

## sample 데이터의 평균값보다 큰 데이터만 선택  

- ```py  
  sample[sample>smaple.mean()]  
  ```  
  
- ```py  
  bbol_idx = sample>sample.mean()  
  sample[bool_idx]  
  ```  

## sample의 값이 50과 80사이의 데이터만 선택  
- ```py
  sample[50 <= sample][sample <= 80]  
  ```  
- ```py  
  sample[(50 <= sample) & (sample <= 80)]  
  ```  

## 실습문제  

```py  
import random  
# 1 ~ 100사이의 값을 26개 생성하여 list로 반환  
sample = random.sample(range(1,100),26)  
data = Series(sample, index = list('ABCDEFGHIJKLMNOPQRSTUVWXYZ')  

# seed값을 고정해두면 실행할때 마다 값을 고정되게 출력할 수 있음  
```  
- 인덱스 라벨이 'K'인 항목의 값을 출력
  ```py  
  data['K']  
  ```  
  - 대문자인데 소문자를 넣으면 key error가 난다 -> 대소문자가 구별됨  
- 인덱스 라벨이 'A', 'F', 'C'인 항목의 값을 출력  
  * ```py  
    print(data['A'], data['F'], data['C'])  
    ```  
  * ```py  
    data[['A', 'F', 'C']]  
    ```  
- 5번 인덱스부터 15번 인덱스까지의 항목 출력
  ```py  
  data[5:16]  
  ```  
- 뒤에서 5개 항목 출력
  ```py  
  data[-5:]  
  ```  
- data의 항목 갯수 출력
  ```py  
  data.size()  
  ```  
- data 항목 값들의 평균보다 큰 항목만 출력
  ```py  
  data[data>data.mean()]  
  ```  
- data의 항목 값 중에 50이 있는지 확인하여 있으면 True, 없으면 False 출력
  ```py  
  50 in data  
  ```  
- data의 인덱스 라벨과 각 항목 값을 출력  
  ```py 
  index: A, value: XX  
  index: B, value: XX    <- 이렇게 나오도록
  index: C, value: XX  
  ```  
  ```py   
  for idx, val in data.items():  
      print('index:', idx, 'value:', val)  
  ```   
