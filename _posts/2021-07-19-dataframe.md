---
title: "DataFrame"
date: 2021-07-19 -0400
categories: 
 - Pandas
tags: 
 - [데이터 청년 캠퍼스, Pandas]

toc: true

---
## DataFrame 생성하고 데이터 할당  

```py  
df1 = DataFrame([['Big', [2,3,4], 'Year']])  
```  

## 사전 타입 데이터를 이용하여 DataFrame 생성  

```py  
인구통계 = {'서울': [950, 945, 938.5],  
        '대전':[50, 151, 145],  
        '대구':[85, 88, 92],  
        '부산':[180, 187, 192],  
        '광주':[74, 80, 80]
      }  
df2 = DataFrame(인구통계, index=[2018,2019,2020])  
```  

## DataFrame 속성 조회  

- index: DataFrame의 인덱스를 리스트로 반환  
  
  ```py  
  df2.index  
    
  Out:  
  Int64Index([2018, 2019, 2020], dtype='int64')  
  ```  
  
- columns: DataFrame의 데이터 반환(ndarray)  
  
  ```py  
  df2.values  
    
  Out:  
  array([[950. ,  50. ,  85. , 180. ,  74. ],  
       [945. , 151. ,  88. , 187. ,  80. ],  
       [938.5, 145. ,  92. , 192. ,  80. ]])  
  ```  
  
- shape: 행(row)과 열(column)의 개수(차원)을 Tuple로 반환 
  
  ```py  
  df2.shape  
    
  Out:  
  (3, 5)  
  ```  
- T(Tramspose): 행과 열을 바꾸기  
  
  ```py  
  df2.T  
    
  Out:  
        2018	2019	2020  
  서울	950.0	945.0	938.5  
  대전	50.0	151.0	145.0  
  대구	85.0	88.0	92.0  
  부산	180.0	187.0	192.0  
  광주	74.0	80.0	80.0  
  ```  
- axes: 행과 열 이름을 리스트로 반환  
  
  ```py  
  df2.axes  
    
  Out:  
  [Int64Index([2018, 2019, 2020], dtype='int64'),  
  Index(['서울', '대전', '대구', '부산', '광주'], dtype='object')]  
  ```  
  
- dtypes: 컬럼별 데이터 타입 반환  
  
  ```py  
  df2.dtypes  
    
  Out:  
  서울    float64  
  대전      int64  
  대구      int64  
  부산      int64  
  광주      int64  
  dtype: object  
  ```  
- size: DataFrame의 원소의 개수를 반환  
  
  ```py  
  df2.size  
    
  Out:  
  15  
  ```  
  
## DataFrame 기본 함수  
- info(): 기본 정보 출력  
  
  ```py  
  df2.info()  
    
  Out:  
  <class 'pandas.core.frame.DataFrame'>  
  Int64Index: 3 entries, 2018 to 2020  
  Data columns (total 5 columns):  
   #   Column  Non-Null Count  Dtype   
  ---  ------  --------------  -----  
   0   서울      3 non-null      float64  
   1   대전      3 non-null      int64  
   2   대구      3 non-null      int64  
   3   부산      3 non-null      int64  
   4   광주      3 non-null      int64  
  dtypes: float64(1), int64(4)  
  memory usage: 252.0 bytes  
  ```  
  
- describe(): 기본 통계 정보 출력  

  ```py  
  df2.describe()  
    
  Out:  
          서울	     대전	     대구	      부산	   광주  
  count	3.000000	3.000000	3.000000	3.000000	3.000000  
  mean	944.500000	115.333333	88.333333	186.333333	78.000000  
  std  	5.766281	56.659804	3.511885	6.027714	3.464102  
  min	  938.500000	50.000000	85.000000	180.000000	74.000000  
  25%	  941.750000	97.500000	86.500000	183.500000	77.000000  
  50%	  945.000000	145.000000	88.000000	187.000000	80.000000  
  75%	  947.500000	148.000000	90.000000	189.500000	80.000000  
  max	  950.000000	151.000000	92.000000	192.000000	80.000000  
  ```  
  
- 통계함수(mean, sum, max, min, ...)  

  * ```py  
    df2.mean()  
      
    Out:  
    서울    944.500000  
    대전    115.333333  
    대구     88.333333  
    부산    186.333333  
    광주     78.000000  
    dtype: float64  
    ```  
    
  * ```py  
    df2.max()  
      
    Out:  
    서울    950.0  
    대전    151.0  
    대구     92.0  
    부산    192.0  
    광주     80.0  
    dtype: float64  
    ```  
    
  * ```py  
    df2.quantile(0.6)  
      
    Out:  
    서울    946.0  
    대전    146.2  
    대구     88.8  
    부산    188.0  
    광주     80.0  
    Name: 0.6, dtype: float64  
    ```  
    
- sample(): 일부 데이터를 랜덤으로 선택  
  
  ```py  
  df2.sample()  
  ```  
  
- head(): 맨 앞의 x개의 데이터만 출력  
  
  ```py  
  df2.head()  
  ```  
  
- tail(): 맨 뒤의 x개의 데이터만 출력
  
  ```py  
  df2.tail()  
  ```  
  
- nunique(): unique한 값의 개수  
  
  ```py  
  df2.nunique()  
  
  Out:  
  서울    3  
  대전    3  
  대구    3  
  부산    3  
  광주    2  
  dtype: int64  
  ```  
  
- plot(): 데이터 시각화  
  
  ```py  
  import matplotlib as plt  
  plt.rcParams['font.family'] = 'Malgun Gothic'  
  df2.plot()  
  ```
  ![image](data:image/png;base64,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){: .align-center}
  
- filter(): 원하는 데이터만 선택  

  * ```py  
    df2.filter(['서울'])  
    
    Out:  
           서울  
    2018	950.0  
    2019	945.0  
    2020	938.5  
    ```   
    
   * ```py  
     # 2018, 2019년 데이터만 선택  
     df3.filter([2018,2019],axis=0)  
     
     Out:  
           서울	  대전	 대구	 부산	 광주  
     2018	 950.0	 50	   85	  180	   74  
     2019	 945.0	 151	 88	  187	   80  
     ```  
     
     * 정규표현식(어떤 패턴을 정의하고 거기에 맞는것을 선택하는 것) 활용 
     
       + ```py
         # '울'로 끝나는 컬럼을 모두 선택  
         df3.filter(regex='울$')  
         
         Out:  
               서울  
         2018	950.0  
         2019	945.0  
         2020	938.5  
         ```  
         
       + ```py  
         # '대'로 시작하는 컬럼을 모두 선택 
         df3.filter(regex='^대')  
         
         Out:  
             대전	대구  
         2018	50	85  
         2019	151	88  
         2020	145	92  
         ``` 
         
       + ```py  
         # 2010년대 데이터만 선택(2010, 2011, 2012, ..., 2019)  
         df3.filter(regex='^201',axis=0)  
         
         Out:  
         서울	대전	대구	부산	광주  
         2018	950.0	50	85	180	74  
         2019	945.0	151	88	187	80  
         ```  
         
       + ```py  
         # 10년 단위의 데이터만 선택(1990, 2000, 2010, 2020, ...)  
         df3.filter(regex='0$', axis=0)  
         
         Out:  
         서울	대전	대구	부산	광주  
         2020	938.5	145	92	192	80  
         ```  

## DataFrame 조회하기  
```py  
df4 = DataFrame({'Class': ['IoT','Network', 'Economy','Big Data', 'Cloud'],  
                      'Year': [2018, 2017, 2018, 2018, 2019],  
                      'Price': [100, 125, 132, 312, 250],
                      'Location': ['Korea','Korea', 'Korea', 'US','Korea']},  
                     index=['C01','C02','C03', 'C04', 'C05'])  
```  

- 원하는 열(column)만 조회

  * Class만 조회
  
    + ```py  
      df4['Class']  # 1차원 데이터(Series)가 됨  
      ```  
      
    + ```py  
      df4.Class  
      ```  
    
  * Class와 Price 조회  
  
    ```py  
    df4[['Class', 'Price']]  
    ```  
    
- 원하는 행(row)만 조회  
  * C03 클래스의 데이터를 선택  
    
    + ```py  
      df4.loc['C03']  
      ```  
    + ```py  
      df4.iloc[2]  
      ```  
    + ```py  
      df4['C03', axis=0]  
      ```  
  * C02, C04 클래스 데이터를 선택
  
    ```py  
    df4.loc['C02', 'C04']  
    ```  
    
- 인덱스 슬라이싱  
  * 02 ~ C04 클래스 데이터 선택  
   
    + ```py  
      df4.loc['C02':'C04']  
      ```  
     
    + ```py  
      # loc생략 가능 -> 슬라이싱의 경우 자동적으로 로우 인덱스를 색인  
      # 컬럼 인덱스는 순서가 없으므로 슬라이싱 불가  
      df4.['C02':'C04']  
      ```  
     
- 원하는 행과 열을 선택하여 조회  
  * C02, C03 강의의 Class와 Year만 조회  
  
    + ```py  
      df4[['Class','Year']].loc[['C02','C03']]  
      ```  
      
    + ```py  
      df4.loc['C02':'C03'][['Class','Year']]  
      ```  
      
    + ```py  
      df4['C02':'C03'][['Class','Year']]  
      ```  
      
    + ```py  
       df4.loc[['C02','C03']][['Class','Year']]  
      ```  
      
    + ```py  
      df4.loc[['C02','C03'],['Class','Year']]  
      ```  
      
    + ```py  
      df4.loc['C02':'C03',['Class','Year']]  
      ```  
      
    + ```py  
      df4.loc['C02':'C03','Class':'Year']  
      ```  
      
- 조건 색인
  * 가격(Price)이 200 이상인 강의만 선택  
  
    + ```py  
      df4[[False, False,False,True,True]]  
      ```  
      
    + ```py  
      df4[df4.Price>=200]  
      ```  
      
## 데이터 프레임에 새로운 컬럼 추가
- limitStudent(정원) 컬럼을 추가하고 값을 30으로 저장  

  ```py  
  df4['limitStudent']=30  
  ```  
  
- numStudent(수강학생 수) 컬럼을 추가하고 값을 25, 30, 10, 23, 17로 저장  

  ```py  
  df4['numStudent']=[25,30,10,23,17]  
  ```  


나머지는 동영상 보고 
  
