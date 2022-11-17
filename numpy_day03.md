```python
import numpy as np
import pandas as pd

# 배열의 정보를 확인하기 위한 함수 정의

def aryInfo(ary) :
    print('type - ', type(ary))
    print('shape - ', ary.shape)
    print('dimension - ', ary.ndim)
    print('dtype - ', ary.dtype)
    print()
    print('data - ')
    print(ary)
```

- 난수: 정해진 알고리즘에 의해 특정한 숫자를 무작위로 만드는 것
- random 서브패키지를 이용해서 난수를 발생
- rand(): 균일분포 0~1 사이의 균일한 확률분포로 실수 난수를 생성하는 것
- randn(): 표준정규분포(실수)
- randint(): 균일분포 0~1 사이의 균일한 확률분포로 정수 난수를 생성하는 것


```python
np.random.rand(10)
```




    array([0.79756859, 0.00888705, 0.34753362, 0.49102923, 0.79428711,
           0.34940702, 0.48456826, 0.53078253, 0.85074455, 0.37155509])




```python
np.random.rand(5)
```




    array([0.62839423, 0.62064677, 0.67769459, 0.02878915, 0.04258879])




```python
np.random.seed(100)  #seed를 설정하면 동일한 난수
```


```python
np.random.rand(10)
```




    array([0.54340494, 0.27836939, 0.42451759, 0.84477613, 0.00471886,
           0.12156912, 0.67074908, 0.82585276, 0.13670659, 0.57509333])




```python
np.random.rand(5)
```




    array([0.89132195, 0.20920212, 0.18532822, 0.10837689, 0.21969749])




```python
np.random.seed(100)
```


```python
np.random.rand(10)
```




    array([0.54340494, 0.27836939, 0.42451759, 0.84477613, 0.00471886,
           0.12156912, 0.67074908, 0.82585276, 0.13670659, 0.57509333])




```python
np.random.rand(5)
```




    array([0.89132195, 0.20920212, 0.18532822, 0.10837689, 0.21969749])




```python
np.random.rand(3,5)
```




    array([[0.97862378, 0.81168315, 0.17194101, 0.81622475, 0.27407375],
           [0.43170418, 0.94002982, 0.81764938, 0.33611195, 0.17541045],
           [0.37283205, 0.00568851, 0.25242635, 0.79566251, 0.01525497]])




```python
np.random.randn(3,5)
```




    array([[ 1.61898166,  1.54160517, -0.25187914, -0.84243574,  0.18451869],
           [ 0.9370822 ,  0.73100034,  1.36155613, -0.32623806,  0.05567601],
           [ 0.22239961, -1.443217  , -0.75635231,  0.81645401,  0.75044476]])




```python
np.random.randint(10, 20, size = 10)
```




    array([13, 14, 17, 16, 13, 19, 10, 14, 14, 15])




```python
np.random.randint(10,20, size=(3,5))
```




    array([[17, 16, 16, 12, 14],
           [12, 17, 11, 16, 16],
           [10, 17, 12, 13, 15]])



- 데이터 샘플링
- choice(범위, 개수, p)


```python
np.random.choice(5,10, p=[0.1, 0, 0.3, 0.6, 0])
```




    array([0, 3, 3, 0, 3, 3, 2, 2, 3, 3])




```python
print('문제) 동전을 20번 던져서 앞면(1)과 뒷면(0) 나오는 실험을 한다면? -')
np.random.choice(2,20, replace=True) #복원추출
```

    문제) 동전을 20번 던져서 앞면(1)과 뒷면(0) 나오는 실험을 한다면? -
    




    array([0, 1, 1, 0, 0, 0, 0, 1, 0, 1, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1])




```python
np.random.randint(0, 2, 20)
```




    array([1, 0, 1, 1, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 1, 1, 0, 1, 1])




```python
print('문제) 주사위를 100번 던져서 나오는 숫자의 평균?')
print(np.mean(np.random.randint(1, 6, 100)))

dice = np.random.choice(np.arange(1,7), 100, replace = True)
print('dice - ', np.mean(dice))
```

    문제) 주사위를 100번 던져서 나오는 숫자의 평균?
    3.27
    dice -  3.48
    


```python
#문제) 가격이 10,000원 주식이 있다. 이 주식의 일간 수익률(%)의 기대값이 0이고 
#표준편차가 1인 정규분포를 따른다고 했을 때 250일 동안의 주가를 무작위로 생성하고 싶다면?
price = 10000
price + (price*np.random.randn(250))/100
```




    array([ 9971.17573052, 10037.52751708, 10004.20953186,  9991.00431597,
           10131.44282946,  9979.44780939,  9903.88814804,  9912.29202953,
            9965.0619461 , 10065.95634651, 10067.90203045,  9959.06260109,
            9964.66822719, 10042.93192866, 10134.87878683,  9972.71086438,
           10018.39363403, 10055.88657879,  9862.86767529,  9966.93561285,
           10045.22332724,  9946.94816856,  9971.8541781 ,  9935.58721261,
            9886.99737743,  9883.82334661, 10016.93330928,  9994.03018604,
           10110.58364466,  9933.81087241,  9964.14955627,  9992.88296499,
           10009.78638009, 10177.06682608, 10071.61109143,  9974.79653073,
           10166.81794413,  9916.65183546, 10116.51817812, 10016.82413857,
            9990.29802396,  9889.16283595, 10116.31257344,  9779.57730799,
            9987.66371228,  9956.08952808, 10062.99876168,  9913.04492935,
            9939.19189181, 10119.93328108, 10272.50208073, 10045.07629856,
            9916.05222756,  9995.98045247, 10088.50898919, 10158.60651416,
           10202.57792339, 10153.03010309, 10183.27334301, 10096.89045577,
           10017.0770932 , 10070.79943796, 10130.16102245, 10037.74260241,
            9921.20988708, 10092.8212355 , 10203.33233171, 10058.126291  ,
           10156.07234238, 10007.3711577 ,  9997.76432889, 10068.55820937,
            9977.9926904 ,  9793.11095046, 10063.36131127,  9765.90744836,
            9958.01539205, 10101.73191686,  9961.08924595,  9926.27378384,
            9999.34017965, 10027.6502952 ,  9941.47322635, 10228.12721074,
           10115.35198871, 10129.72505366,  9977.70934759, 10034.4213463 ,
            9800.17179124, 10055.15401814,  9916.52997654,  9918.93741878,
           10010.38273621,  9971.14596698,  9907.05023159, 10044.87887876,
            9944.39318405, 10130.99523238,  9931.36041345,  9886.67527289,
            9983.56682677, 10106.04911834,  9947.03504974,  9957.91833903,
            9740.69506122, 10028.76810779, 10081.01916423, 10010.19376473,
            9971.94903681,  9942.22272829,  9975.6788885 ,  9850.74798264,
           10024.20458354,  9858.69592723,  9905.46653879, 10152.215286  ,
           10200.06720241,  9934.36210148,  9952.7086806 , 10174.62563183,
           10144.30875835,  9908.05508152, 10109.01528926, 10109.2563362 ,
            9967.58498018, 10082.37126081, 10195.50554439,  9934.8869483 ,
           10096.88868482, 10042.02392505,  9829.22851096,  9999.40759277,
            9925.95029937, 10135.21367586,  9935.50114579,  9984.4857191 ,
            9993.13497472,  9956.76799974,  9780.23080733, 10089.22578847,
           10014.3860996 , 10127.55973233,  9953.10128449, 10047.41248278,
           10066.83952189,  9879.52841201,  9914.88679118, 10089.91245293,
           10093.71915337, 10095.35866517,  9779.48965354,  9771.86942073,
            9938.83689241, 10280.97011436, 10017.58457117,  9936.92444093,
           10185.55455404, 10016.02907499,  9857.7150453 ,  9963.23401465,
            9811.37116325, 10075.48220932, 10178.12245782, 10065.262946  ,
           10023.7503794 , 10059.42014265,  9886.70656687, 10049.74278728,
            9975.57654812, 10104.0681518 ,  9973.29289664,  9932.27163138,
            9932.8392177 , 10262.56144458,  9888.31993598, 10093.62535725,
            9943.38176163,  9949.46530785,  9913.35827147, 10139.70311144,
            9913.80780257,  9988.48436568, 10001.05366974,  9948.038364  ,
            9975.04287423, 10224.36594507,  9951.70034011,  9763.1019825 ,
            9907.84191774, 10151.90033139, 10055.24984189,  9930.73183863,
            9893.99917408, 10146.71555504,  9983.20868272, 10075.97959068,
            9979.13782681,  9995.17783644,  9981.66254081, 10128.30307747,
           10068.47631555, 10050.7827176 , 10041.61459758, 10014.29569525,
            9993.83724337,  9968.51932544, 10066.10574335,  9890.51315104,
            9965.26457363, 10135.83611934,  9970.19410998,  9991.99170934,
           10049.46812991, 10137.3326412 ,  9907.12342392,  9894.3719392 ,
           10020.22550669,  9932.17490921,  9997.7987533 ,  9809.96303085,
            9897.60635807, 10021.5068047 ,  9947.33017974,  9947.55650195,
           10054.70527976, 10011.87319258,  9769.46775766, 10071.99911387,
            9871.54954404, 10135.69787877, 10048.4686278 ,  9974.38845857,
           10135.46263068, 10207.59505804, 10066.68801994,  9898.62802976,
           10019.65950691, 10021.087317  ,  9844.76112936,  9888.9365328 ,
           10045.04456178, 10228.03112732, 10169.2590628 , 10088.41718182,
            9946.15200553,  9962.33256578,  9956.76136338, 10158.06598294,
            9831.52935848, 10213.58395797])



- 기후통계분석.csv 파일로드
- 문제) 기상관측 이래 서울의 최고기온이 가장 높았던 날짜 및 최고기온을 추출


```python
raw_data = np.loadtxt('./data/numpy_data/기후통계분석.csv',
                     skiprows = 1,
                     dtype = 'U',
                     delimiter = ',')
aryInfo(raw_data)
```

    type -  <class 'numpy.ndarray'>
    shape -  (40414, 5)
    dimension -  2
    dtype -  <U10
    
    data - 
    [['1907-10-01' '108' '13.5' '7.9' '20.7']
     ['1907-10-02' '108' '16.2' '7.9' '22']
     ['1907-10-03' '108' '16.2' '13.1' '21.3']
     ...
     ['2021-08-23' '108' '22.4' '21' '24']
     ['2021-08-24' '108' '23.4' '21.1' '26.4']
     ['2021-08-25' '108' '25' '23.5' '27.3']]
    


```python
print('type - ', type(raw_data[0]))
print('data - ', raw_data[0])
```

    type -  <class 'numpy.ndarray'>
    data -  ['1907-10-01' '108' '13.5' '7.9' '20.7']
    


```python
temp = raw_data[:, 4]
print('type - ', type(temp))
print('data - ', temp)
print('dtype - ', temp.dtype)
temp = temp.astype(float)
print('dtype - ', temp.dtype)

```

    type -  <class 'numpy.ndarray'>
    data -  ['20.7' '22' '21.3' ... '24' '26.4' '27.3']
    dtype -  <U10
    dtype -  float64
    


```python
np.argsort(temp)[::-1]
```




    array([39293, 30520, 39292, ...,  2662,  8503,  2661], dtype=int64)




```python
answer = raw_data[np.argsort(temp)[::-1]][0, :]
print(answer)
```

    ['2018-08-01' '108' '33.6' '27.8' '39.6']
    


```python
# --실습
```


```python
ratings_data = np.loadtxt('./data/ratings.dat' , delimiter = "::", dtype=np.int64)

# 데이터의 첫 5행만 확인
print(ratings_data[:5])

# 데이터의 형태 확인
print(ratings_data.shape)


```

    [[        1      1193         5 978300760]
     [        1       661         3 978302109]
     [        1       914         3 978301968]
     [        1      3408         4 978300275]
     [        1      2355         5 978824291]]
    (1000209, 4)
    


```python
# 전체 평균 평점 계산
np.mean(ratings_data[:, 2])
```




    3.581564453029317




```python
#사용자 아이디 수집
x = []
for i in range(len(ratings_data)):
    if ratings_data[i,0] not in x:
        x.append(ratings_data[i,0])
print(x)
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27,  ...  6036, 6037, 6038, 6039, 6040]
    


```python
#사용자별 평점 확인
temp_list = []
for y in x:
    temp = ratings_data[ratings_data[:,0]==y, 2].mean()
    temp_list.append([y, temp])
print(temp_list)
```

    [[1, 4.188679245283019], [2, 3.7131782945736433], [3, 3.9019607843137254], [4, 4.190476190476191], [5, 3.1464646464646466], [6, 3.9014084507042255], [7, 4.32258064516129], ... [6035, 2.6107142857142858], [6036, 3.3029279279279278], [6037, 3.717821782178218], [6038, 3.8], [6039, 3.8780487804878048], [6040, 3.5777126099706744]]
    


```python
id_ratings = np.array(temp_list)
upper_id = id_ratings[id_ratings[:,1] >= 4, :]
aryInfo(upper_id)
```

    type -  <class 'numpy.ndarray'>
    shape -  (1544, 2)
    dimension -  2
    dtype -  float64
    
    data - 
    [[1.00000000e+00 4.18867925e+00]
     [4.00000000e+00 4.19047619e+00]
     [7.00000000e+00 4.32258065e+00]
     ...
     [6.02700000e+03 4.25000000e+00]
     [6.03200000e+03 4.13461538e+00]
     [6.03400000e+03 4.09523810e+00]]
    


```python
np.savetxt('test.csv', upper_id, fmt='%.1f', delimiter=',' )
```

#### 실습2


```python
seoul = np.loadtxt('./data/numpy_data/seoul.csv' , delimiter = ",", dtype=np.str, skiprows=8)
seoul
daegu = np.loadtxt('./data/numpy_data/daegu.csv' , delimiter = ",", dtype=np.str, skiprows=8)
daegu

```

    C:\Users\user\AppData\Local\Temp\ipykernel_27960\830380556.py:1: DeprecationWarning: `np.str` is a deprecated alias for the builtin `str`. To silence this warning, use `str` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.str_` here.
    Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
      seoul = np.loadtxt('./data/numpy_data/seoul.csv' , delimiter = ",", dtype=np.str, skiprows=8)
    C:\Users\user\AppData\Local\Temp\ipykernel_27960\830380556.py:3: DeprecationWarning: `np.str` is a deprecated alias for the builtin `str`. To silence this warning, use `str` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.str_` here.
    Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
      daegu = np.loadtxt('./data/numpy_data/daegu.csv' , delimiter = ",", dtype=np.str, skiprows=8)
    




    array([['1907-01-31', '143', '', '-7', '0.8'],
           ['1907-02-01', '143', '', '', ''],
           ['1907-02-02', '143', '', '', ''],
           ...,
           ['2020-09-04', '143', '24.1', '18.3', '30.4'],
           ['2020-09-05', '143', '19.9', '17.3', '23.1'],
           ['2020-09-06', '143', '19.5', '17.6', '20.7']], dtype='<U10')




```python
#서울 최고기온 높았던날 언제인가?
for x in seoul:
    if x[4] == '':
        x[4] = -20
highday = np.argmax(seoul[:, 4].astype(np.float))
seoul[highday, :]

```

    C:\Users\user\AppData\Local\Temp\ipykernel_27960\2299773467.py:4: DeprecationWarning: `np.float` is a deprecated alias for the builtin `float`. To silence this warning, use `float` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.float64` here.
    Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
      highday = np.argmax(seoul[:, 4].astype(np.float))
    




    array(['2018-08-01', '108', '33.6', '27.8', '39.6'], dtype='<U10')




```python
#일교차 가장 큰 날짜?

whole = np.vstack([seoul, daegu])
for y in whole:
    if y[3] == '':
        y[3] = -20
    if y[4] == '':
        y[4] = -20
high_diff = np.argmax(whole[:, 4].astype(np.float)-whole[:,3].astype(np.float))
whole[high_diff, :]
```

    C:\Users\user\AppData\Local\Temp\ipykernel_27960\2456745669.py:9: DeprecationWarning: `np.float` is a deprecated alias for the builtin `float`. To silence this warning, use `float` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.float64` here.
    Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
      high_diff = np.argmax(whole[:, 4].astype(np.float)-whole[:,3].astype(np.float))
    




    array(['1913-04-04', '143', '12.5', '-0.2', '26'], dtype='<U10')




```python
#평균적으로 일교차가 가장 큰 날짜?

day_list = []
day = []

for d in whole:
    if d[3] == '':
        d[3] = -20
    if d[4] == '':
        d[4] = -20
    temp = float(d[4]) - float(d[3])
    day_list.append([d[0], float(temp)])
    if d[0] not in day:
        day.append(d[0])
day_list = np.array(day_list)
```


```python
day_list
```




    array([['1907-10-01', '12.799999999999999'],
           ['1907-10-02', '14.1'],
           ['1907-10-03', '8.200000000000001'],
           ...,
           ['2020-09-04', '12.099999999999998'],
           ['2020-09-05', '5.800000000000001'],
           ['2020-09-06', '3.099999999999998']], dtype='<U32')




```python
day_mean = []
for d in day:
    temp = day_list[day_list[:,0]==d, 1].astype(np.float).mean()
    day_mean.append([d,temp])
day_mean = np.array(day_mean)
day_max = np.array(day_mean)[:,1].astype(np.float).argmax()
day_mean[day_max, :]
```

    C:\Users\user\AppData\Local\Temp\ipykernel_27960\3706789879.py:3: DeprecationWarning: `np.float` is a deprecated alias for the builtin `float`. To silence this warning, use `float` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.float64` here.
    Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
      temp = day_list[day_list[:,0]==d, 1].astype(np.float).mean()
    C:\Users\user\AppData\Local\Temp\ipykernel_27960\3706789879.py:6: DeprecationWarning: `np.float` is a deprecated alias for the builtin `float`. To silence this warning, use `float` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.float64` here.
    Deprecated in NumPy 1.20; for more details and guidance: https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations
      day_max = np.array(day_mean)[:,1].astype(np.float).argmax()
    




    array(['1913-04-04', '22.299999999999997'], dtype='<U32')




```python
#대구보다 서울이 더 더운날이 가장 많은 연도는?

for x in seoul :
    if x[4] == '':
        x[4] = -20

for x in daegu :
    if x[4] == '':
        x[4] = -20
winner = []

for d in seoul:
    t = daegu[daegu[:,0] == d[0], 4]
    if (float(d[4]) > float(t) and t!='-20'):
        winner.append(d[0][:4])
        
winner = np.array(winner)
(a, b) = np.unique(winner, return_counts = True)
print(a, len(a))
print(b, len(b))
c = b.argmax()
a[c]
```

    ['1907' '1908' '1909' '1910' '1911' '1912' '1913' '1914' '1915' '1916'
     '1917' '1918' '1919' '1920' '1921' '1922' '1923' '1924' '1925' '1926'
     '1927' '1928' '1929' '1930' '1931' '1932' '1933' '1934' '1935' '1936'
     '1937' '1938' '1939' '1940' '1941' '1942' '1943' '1944' '1945' '1946'
     '1947' '1948' '1949' '1950' '1953' '1954' '1955' '1956' '1957' '1958'
     '1959' '1960' '1961' '1962' '1963' '1964' '1965' '1966' '1967' '1968'
     '1969' '1970' '1971' '1972' '1973' '1974' '1975' '1976' '1977' '1978'
     '1979' '1980' '1981' '1982' '1983' '1984' '1985' '1986' '1987' '1988'
     '1989' '1990' '1991' '1992' '1993' '1994' '1995' '1996' '1997' '1998'
     '1999' '2000' '2001' '2002' '2003' '2004' '2005' '2006' '2007' '2008'
     '2009' '2010' '2011' '2012' '2013' '2014' '2015' '2016' '2017' '2018'
     '2019' '2020'] 112
    [  1   7  52  81  71  50  67  64  46 119  94  98 103 115 121  78  91  98
     102  78  92  95 107 133 122 104  64  61  78  79 107  89 109  94 122  83
     132  80  94 106  77 119 106  88   1  97  88  81  80  84  81  77  93  64
      83  72  77  89  85 102  70  96  73  87  63  68 103  88  78  55  67  73
      57  82  86  75  67  63  61  76  82  53  91  58  82  61  46  63  71 113
     103  78  75  82 101  63  46  76  68  65  59  48  68  76  41  93 119 128
      83  98  94  65] 112
    




    '1930'




```python

```


```python

```


```python

```


```python

```


```python

```
