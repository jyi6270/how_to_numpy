#### Numpy 학습 목표

- 배열 데이터 타입(인공지능에서 사용되는 데이터의 타입)
- 생성방법, 다루는 방법
- 통계에 관련된 다양한 함수를 지원

#### 배열(벡터화 연산, 행렬의 벡터화 연산)
- 리스트와 차이가 있다(배열의 모든 원소는 같은 자료형)
- 원소의 개수를 바꿀 수 없다(resizing X)
- 배열의 차원, 크기, 타입(ndim, shape, dtype)


```python
import numpy as np
import pandas as pd
```


```python
# 배열의 정보를 확인하기 위한 함수 정의

def aryInfo(ary):
    print('type - ', type(ary))
    print('shape - ', ary.shape)
    print('dimension - ', ary.ndim)
    print('dtype - ', ary.dtype)
    print()
    print('data - ')
    print(ary)
```

- 배열 객체를 생성할 때 사용하는 함수: array(), arrange(), reshape()


```python
np.array([1,2,3,4,5,6,7,8,9])   # array함수에 리스트를 넣으면 배열이 됨
ary = np.array([1,2,3,4,5,6,7,8,9])
aryInfo(ary)
```

    type -  <class 'numpy.ndarray'>
    shape -  (9,)
    dimension -  1
    dtype -  int32
    
    data - 
    [1 2 3 4 5 6 7 8 9]
    

- 벡터화 연산(vectorized operation)


```python
data = [1,2,3,4,5,6,7,8,9]
print('type - ', type(data))
print()
print(data*2)
print()

result=[]
for value in data :
    result.append(value*2)
print(result)
print()

result = [value*2 for value in data]
print(result)
print()

print(ary*2)
```

    type -  <class 'list'>
    
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    [2, 4, 6, 8, 10, 12, 14, 16, 18]
    
    [2, 4, 6, 8, 10, 12, 14, 16, 18]
    
    [ 2  4  6  8 10 12 14 16 18]
    

- 산술, 비교, 논리


```python
ary01 = np.array([1,2,3,4,5])
ary02 = np.array([10,20,30,40,50])
print('type - ', type(ary01), type(ary02))
```

    type -  <class 'numpy.ndarray'> <class 'numpy.ndarray'>
    


```python
print('산술연산 - ')
print(ary01 * ary02)
```

    산술연산 - 
    [ 10  40  90 160 250]
    


```python
print('비교연산 - ')
ary01 == 2
boolean_masking = (ary01==2)
print(boolean_masking, type(boolean_masking), boolean_masking[0])
print(ary01[boolean_masking])
```

    비교연산 - 
    [False  True False False False] <class 'numpy.ndarray'> False
    [2]
    


```python
print('논리연산 - ')
print(ary01 == 2)
print(ary02 > 10)
print( (ary01 == 2) & (ary02 > 10))
print( (ary01 == 2) | (ary02 > 10))
```

    논리연산 - 
    [False  True False False False]
    [False  True  True  True  True]
    [False  True False False False]
    [False  True  True  True  True]
    

- 2차원배열(matrix - 행렬): list of list
- N-dimensional Array


```python
print('2*3의 배열을 생성한다면? - ')
ary = np.array( [[1,2,3],[4,5,6]])
aryInfo(ary)
print()

print('len() - ', len(ary)) # 행의 개수
print('len() - ', len(ary[0])) # 첫 번째 행의 요소의 개수
print('len() - ', len(ary[1])) # 두 번째 행의 요소의 개수

```

    2*3의 배열을 생성한다면? - 
    type -  <class 'numpy.ndarray'>
    shape -  (2, 3)
    dimension -  2
    dtype -  int32
    
    data - 
    [[1 2 3]
     [4 5 6]]
    
    len() -  2
    len() -  3
    len() -  3
    


```python
print('3*4의 배열을 두 개 생성한다면? - ')
ary = np.array([[[1,2,3,4],[5,6,7,8],[9,10,11,12]],
                [[13,14,15,16],[17,18,19,20],[21,22,23,24]]])
aryInfo(ary)
print()

print('len() - ', len(ary))
print('len() - ', len(ary[0]))
```

    3*4의 배열을 두 개 생성한다면? - 
    type -  <class 'numpy.ndarray'>
    shape -  (2, 3, 4)
    dimension -  3
    dtype -  int32
    
    data - 
    [[[ 1  2  3  4]
      [ 5  6  7  8]
      [ 9 10 11 12]]
    
     [[13 14 15 16]
      [17 18 19 20]
      [21 22 23 24]]]
    
    len() -  2
    len() -  3
    

- astype() : 요소의 타입을 변경할 때 사용


```python
aryInfo(ary.astype(np.float64))
```

    type -  <class 'numpy.ndarray'>
    shape -  (2, 3, 4)
    dimension -  3
    dtype -  float64
    
    data - 
    [[[ 1.  2.  3.  4.]
      [ 5.  6.  7.  8.]
      [ 9. 10. 11. 12.]]
    
     [[13. 14. 15. 16.]
      [17. 18. 19. 20.]
      [21. 22. 23. 24.]]]
    

- 인덱싱과 슬라이싱


```python
ary = np.array([1,2,3,4,5,6,7,8,9])
aryInfo(ary)
print('indexing - ' , ary[0], ary[-1])
print('slicing - ', ary[4:7])
print()

print(ary[ [0,2] ]) # 다중 인덱싱은 또 다른 리스트로
masking = [True, False, True, False, False, False, False, False, False]
print(ary[masking])
```

    type -  <class 'numpy.ndarray'>
    shape -  (9,)
    dimension -  1
    dtype -  int32
    
    data - 
    [1 2 3 4 5 6 7 8 9]
    indexing -  1 9
    slicing -  [5 6 7]
    
    [1 3]
    [1 3]
    


```python
ary = np.array([[1,2,3],[4,5,6]])
aryInfo(ary)
print('첫 번째 행의 첫 번째 열의 값을 추출 - ', ary[0,0])
print('두 번째 행의 첫 번째 열 - ', ary[1,0])
print('마지막 행의 마지막 열 - ', ary[1,2], ary[-1,-1])
print('첫 번째 행의 전체 열 - ', ary[0,], ary[0, :])
print('두 번째 열의 전체 행 - ', ary[:,1])
print('두 번째 행의 두번째부터 끝까지 - ', ary[1,1:])
```

    type -  <class 'numpy.ndarray'>
    shape -  (2, 3)
    dimension -  2
    dtype -  int32
    
    data - 
    [[1 2 3]
     [4 5 6]]
    첫 번째 행의 첫 번째 열의 값을 추출 -  1
    두 번째 행의 첫 번째 열 -  4
    마지막 행의 마지막 열 -  6 6
    첫 번째 행의 전체 열 -  [1 2 3] [1 2 3]
    두 번째 열의 전체 행 -  [2 5]
    두 번째 행의 두번째부터 끝까지 -  [5 6]
    

- fancy indexing == array indexing
- 정수 배열 인덱싱
- 불리언 인덱싱


```python
ary = np.array([1,2,3,4,5,6,7,8,9])
aryInfo(ary)
print('짝수의 원소만 추출? - ', ary[ary%2==0])

evenidx = np.array([1,3,5,7,9])
oddidx = np.array([0,2,4,6,8])
```

    type -  <class 'numpy.ndarray'>
    shape -  (9,)
    dimension -  1
    dtype -  int32
    
    data - 
    [1 2 3 4 5 6 7 8 9]
    짝수의 원소만 추출? -  [2 4 6 8]
    


```python
ary = np.arange(1, 21)
aryInfo(ary)
print()

print('3의 배수만 추출 - ', ary[ary%3==0])
print('4로 나누면 1이 남는 수를 추출 - ', ary[ary%4==1])
print('3의 배수이고 4로 나누면 1이 남는 수를 추출 - ', ary[(ary%3==0) & (ary%4==1)])
```

    type -  <class 'numpy.ndarray'>
    shape -  (20,)
    dimension -  1
    dtype -  int32
    
    data - 
    [ 1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20]
    
    3의 배수만 추출 -  [ 3  6  9 12 15 18]
    4로 나누면 1이 남는 수를 추출 -  [ 1  5  9 13 17]
    3의 배수이고 4로 나누면 1이 남는 수를 추출 -  [9]
    

- reshape(): 배열의 변형


```python
ary = np.arange(1,13).reshape(3,-1)
aryInfo(ary)
print()

print('정수 배열 인덱싱 - ')
col_idx = [0,3]
print(ary[:, col_idx])
print()

print('위 코드를 불리언 인덱싱으로 - ')
boolean_col_idx= [True, False, False, True]
print(ary[:,boolean_col_idx])
print()

print('5 추출 - ', ary[1,0], type(ary[1,0]))
print('5 추출 - ', ary[1:2, 0:1], type(ary[1:2, 0:1]))
print()

print(' [2 10] 추출 - ', ary[ [0,2], 1])
print(' [[2] [10]] 추출 - ', ary[[0,2],1:2])
print(' [[1 3] [9 11]] 추출 - ')
row_idx = np.array([0,2])
col_idx = np.array([0,2])
print(ary[[row_idx]][:, col_idx])

print('numpy ix_() 함수')
print(ary[np.ix_(row_idx, col_idx)])
```

    type -  <class 'numpy.ndarray'>
    shape -  (3, 4)
    dimension -  2
    dtype -  int32
    
    data - 
    [[ 1  2  3  4]
     [ 5  6  7  8]
     [ 9 10 11 12]]
    
    정수 배열 인덱싱 - 
    [[ 1  4]
     [ 5  8]
     [ 9 12]]
    
    위 코드를 불리언 인덱싱으로 - 
    [[ 1  4]
     [ 5  8]
     [ 9 12]]
    
    5 추출 -  5 <class 'numpy.int32'>
    5 추출 -  [[5]] <class 'numpy.ndarray'>
    
     [2 10] 추출 -  [ 2 10]
     [[2] [10]] 추출 -  [[ 2]
     [10]]
     [[1 3] [9 11]] 추출 - 
    [[ 1  3]
     [ 9 11]]
    numpy ix_() 함수
    [[ 1  3]
     [ 9 11]]
    

    C:\Users\user\AppData\Local\Temp\ipykernel_35428\2456886232.py:24: FutureWarning: Using a non-tuple sequence for multidimensional indexing is deprecated; use `arr[tuple(seq)]` instead of `arr[seq]`. In the future this will be interpreted as an array index, `arr[np.array(seq)]`, which will result either in an error or a different result.
      print(ary[[row_idx]][:, col_idx])
    

- dtype: b - > 불리언, i -> 정수, u -> 부호 없는 정수, f - > 부동소수점, U -> 문자열


```python
ary = np.array([1,2,3], dtype = 'U')
aryInfo(ary)
```

    type -  <class 'numpy.ndarray'>
    shape -  (3,)
    dimension -  1
    dtype -  <U1
    
    data - 
    ['1' '2' '3']
    

- inf(infinity), nan(not a number)


```python
print('infinity - ', np.log(0) )
print('infinity - not a number - ', np.array([1,0]) / np.array([0, 0]))
```

    infinity -  -inf
    infinity - not a number -  [inf nan]
    

    C:\Users\user\AppData\Local\Temp\ipykernel_35428\2693944456.py:1: RuntimeWarning: divide by zero encountered in log
      print('infinity - ', np.log(0) )
    C:\Users\user\AppData\Local\Temp\ipykernel_35428\2693944456.py:2: RuntimeWarning: divide by zero encountered in true_divide
      print('infinity - not a number - ', np.array([1,0]) / np.array([0, 0]))
    C:\Users\user\AppData\Local\Temp\ipykernel_35428\2693944456.py:2: RuntimeWarning: invalid value encountered in true_divide
      print('infinity - not a number - ', np.array([1,0]) / np.array([0, 0]))
    

- 배열 생성: array(), arange(), zeros(), ones, zeros_like(), ones_like(), empty(), linspace(), logspace()


```python
ary = np.zeros((3,5,2), dtype='i')
aryInfo(ary)
```

    type -  <class 'numpy.ndarray'>
    shape -  (3, 5, 2)
    dimension -  3
    dtype -  int32
    
    data - 
    [[[0 0]
      [0 0]
      [0 0]
      [0 0]
      [0 0]]
    
     [[0 0]
      [0 0]
      [0 0]
      [0 0]
      [0 0]]
    
     [[0 0]
      [0 0]
      [0 0]
      [0 0]
      [0 0]]]
    


```python
ary= np.arange(3, 21, 2)
ary
```




    array([ 3,  5,  7,  9, 11, 13, 15, 17, 19])




```python
np.linspace(0, 100, 5)
```




    array([  0.,  25.,  50.,  75., 100.])




```python
np.logspace(0.1, 1, 10)
```




    array([ 1.25892541,  1.58489319,  1.99526231,  2.51188643,  3.16227766,
            3.98107171,  5.01187234,  6.30957344,  7.94328235, 10.        ])



- transpose matrix(전치행렬)
- T


```python
ary = np.arange(1,7).reshape(3,2)
aryInfo(ary)
print()

print('T')
ary_transpose = ary.T
aryInfo(ary_transpose)
```

    type -  <class 'numpy.ndarray'>
    shape -  (3, 2)
    dimension -  2
    dtype -  int32
    
    data - 
    [[1 2]
     [3 4]
     [5 6]]
    
    T
    type -  <class 'numpy.ndarray'>
    shape -  (2, 3)
    dimension -  2
    dtype -  int32
    
    data - 
    [[1 3 5]
     [2 4 6]]
    


```python
print('1차원 배열에 대한 전치행렬이 필요한 경우 - ')
ary = np.arange(1,7)
aryInfo(ary)
ary_transpose = ary.reshape(1,6)
aryInfo(ary_transpose)
print(ary_transpose.T)
```

    1차원 배열에 대한 전치행렬이 필요한 경우 - 
    type -  <class 'numpy.ndarray'>
    shape -  (6,)
    dimension -  1
    dtype -  int32
    
    data - 
    [1 2 3 4 5 6]
    type -  <class 'numpy.ndarray'>
    shape -  (1, 6)
    dimension -  2
    dtype -  int32
    
    data - 
    [[1 2 3 4 5 6]]
    [[1]
     [2]
     [3]
     [4]
     [5]
     [6]]
    

- 다차원 배열을 1차원으로 만들어야 한다면?
- flatten()


```python
aryInfo(ary_transpose.flatten())
```

    type -  <class 'numpy.ndarray'>
    shape -  (6,)
    dimension -  1
    dtype -  int32
    
    data - 
    [1 2 3 4 5 6]
    

- 배열 사용시 주의점(차원에 대한 주의)


```python
ary = np.arange(10)
aryinfo(ary)
print('reshape - ', ary.reshape(1,10))
print('reshape - ', ary.reshape(10,1))
print()

print('차원의 변경이 아닌 차원증가를 위해서는 - newaxis')
print(ary[np.newaxis, : ])
print(ary[ :, np.newaxis])

```

    type -  <class 'numpy.ndarray'>
    shape -  (10,)
    dimension -  1
    dtype -  int32
    
    data - 
    [0 1 2 3 4 5 6 7 8 9]
    reshape -  [[0 1 2 3 4 5 6 7 8 9]]
    reshape -  [[0]
     [1]
     [2]
     [3]
     [4]
     [5]
     [6]
     [7]
     [8]
     [9]]
    
    차원의 변경이 아닌 차원증가를 위해서는 - newaxis
    [[0 1 2 3 4 5 6 7 8 9]]
    [[0]
     [1]
     [2]
     [3]
     [4]
     [5]
     [6]
     [7]
     [8]
     [9]]
    

- ndarray(배열) 모든 원소에 대해서 순차적으로 접근해야하는 경우
- iternext(), finished


```python
ary = np.arange(1,11)
ary
```




    array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10])




```python
for tmp in ary :
    print(tmp, end="\t")
print()

for idx in range(len(ary)) :
    print(ary[idx], end="\t")
```

    0	1	2	3	4	5	6	7	8	9	
    0	1	2	3	4	5	6	7	8	9	


```python
print('1차원 ndarray 에 대한 순차 접근 - ')
iter = np.nditer(ary, flags = ['c_index'])

while not iter.finished:
    idx= iter.index
    print('idx - ', idx, ary[idx], end="\t")
    iter.iternext()
```

    1차원 ndarray 에 대한 순차 접근 - 
    idx -  0 1	idx -  1 2	idx -  2 3	idx -  3 4	idx -  4 5	idx -  5 6	idx -  6 7	idx -  7 8	idx -  8 9	idx -  9 10	


```python
print('2차원 ndarray에 대한 iterator - ')

ary = ary.reshape(2,5)
print(ary)

print('기존 for 구문을 이용한 순차 접근')
print(ary.shape)
print(ary.shape[0])
print(ary.shape[1])
for row in range(ary.shape[0]) :
    for col in range(ary.shape[1]) :
        print(ary[row][col], end = '\t')
    print()

print('nditer - ')
iter = np.nditer(ary, flags = ['multi_index'])

cnt=0
while not iter.finished:
    idx = iter.multi_index
    #print('idx - ', idx, ary[idx], end="\t")
    #print('row - index : ', idx[0])
    if idx[0] == 0:
        print(ary[idx], end="\t")
        cnt = cnt +1
        if cnt%5 == 0:
            print()
    else :
        print(ary[idx], end="\t")
        
        
    iter.iternext()
```

    2차원 ndarray에 대한 iterator - 
    [[ 1  2  3  4  5]
     [ 6  7  8  9 10]]
    기존 for 구문을 이용한 순차 접근
    (2, 5)
    2
    5
    1	2	3	4	5	
    6	7	8	9	10	
    nditer - 
    1	2	3	4	5	
    6	7	8	9	10	


```python

```


```python

```
