---
title: "Numpy 기초 문법"
author: "HS"
date: '2022-03-24'
---
# NumPy 기초 문법

## NumPy 라이브 블러오기


```python
import numpy as np # 앨리어싱
print(np.__version__)
```

    1.21.5
    

## 배열로 변환
- 1부터 10까지의 리스트를 만든다.
- NumPy 배열로 변환해서 저장한다.


```python
temp = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
arr = np.array(temp) # 리스트를 배열로 변환하자
print(arr)
```

    [ 1  2  3  4  5  6  7  8  9 10]
    

- 타입 확인하기


```python
print(type(temp))
print(type(arr)) # ndarray는 Numpy의 핵심인 다차원 행렬 자료구조 클래스 입니다.
```

    <class 'list'>
    <class 'numpy.ndarray'>
    

- arr 배열 숫자 5 출력


```python
print(arr[4])   # 인덱싱
print(arr[4:8]) # 슬라이싱
```

    5
    [5 6 7 8]
    

- NumPy를 사용하여 기초 통계 함수를 사용한다.


```python
print(np.mean(arr)) # 평균
print(np.sum(arr)) # 합계
print(np.median(arr)) # 중간값
print(np.std(arr)) # 표준편차
```

    5.5
    55
    5.5
    2.8722813232690143
    

## 사칙연산



```python
math_scores = [90, 80, 88]
english_scores = [80, 70, 90]

total_scores = math_scores + english_scores
print(total_scores) # 원하는 답이 안 나온다.
```

    [90, 80, 88, 80, 70, 90]
    


```python
math_scores = [90, 80, 88]
english_scores = [80, 70, 90]

math_arr = np.array(math_scores)
english_arr = np.array(english_scores)

total_scores = math_arr + english_arr
print(total_scores) # 원하는 답!
```

    [170 150 178]
    


```python
print(np.min(total_scores)) # 최솟값
print(np.max(total_scores)) # 최댓값
```

    150
    178
    

## NumPy 메서드
### 사칙연산


```python
# 덧셈
print("덧셈:", np.add(math_arr, english_arr))

# 뺄셈
print("뺄셈:", np.subtract(math_arr, english_arr))

# 곱셈
print("곱셈:", np.multiply(math_arr, english_arr))

# 나눗셈
print("나눗셈:", np.divide(math_arr, english_arr))

# 거듭제곱
print("거듭제곱:", np.power(math_arr, english_arr)) # 값이 너무 크다. 그래서 0이 나옴
```

    덧셈: [170 150 178]
    뺄셈: [10 10 -2]
    곱셈: [7200 5600 7920]
    나눗셈: [1.125      1.14285714 0.97777778]
    거듭제곱: [0 0 0]
    

## 배열의 생성
- 0차원부터 3차원까지 생성하는 방법
- .shape 은 배열의 크기
- .ndim 은 차원을 알려준다.


```python
temp_arr = np.array(20)
print(temp_arr)
print(type(temp_arr))
print(temp_arr.shape) # 배열의 크기
print(temp_arr.ndim) # 차원은 0.
```

    20
    <class 'numpy.ndarray'>
    ()
    0
    


```python
# 1차원 배열
temp_arr = np.array([1, 2, 3])
print(temp_arr)
print(type(temp_arr))
print(temp_arr.shape) # 1차원 배열에 3개의 사이즈
print(temp_arr.ndim) # 차원이 1이다.
```

    [1 2 3]
    <class 'numpy.ndarray'>
    (3,)
    1
    

### 2차원 배열


```python
temp_arr = np.array([[1, 2, 3],[4, 5, 6]])
print(temp_arr)
print(type(temp_arr))
print(temp_arr.shape) # 2 * 3 배열
print(temp_arr.ndim) # 차원이 2이다.
```

    [[1 2 3]
     [4 5 6]]
    <class 'numpy.ndarray'>
    (2, 3)
    2
    

### 3차원 배열


```python
temp_arr = np.array([[[1, 2, 3],[4, 5, 6]], [[1, 2, 3],[4, 5, 6]]])
print(temp_arr)
print(type(temp_arr))
print(temp_arr.shape) # 2 * 2 * 3 배열
print(temp_arr.ndim) # 차원이 3이다.
```

    [[[1 2 3]
      [4 5 6]]
    
     [[1 2 3]
      [4 5 6]]]
    <class 'numpy.ndarray'>
    (2, 2, 3)
    3
    

- 2 * 2 * 3 에서 각 숫자를 하나의 축이라고 생각하면 된다.
- 숫자가 3개니 3차원인 것이다.


```python
temp_arr = np.array([1, 2, 3, 4], ndmin = 2)
print(temp_arr)
print(type(temp_arr))
print(temp_arr.shape) # 1 * 4 배열
print(temp_arr.ndim) # 차원이 2이다.
```

    [[1 2 3 4]]
    <class 'numpy.ndarray'>
    (1, 4)
    2
    

- 마찬가지로, 1 * 4 는 2개의 축으로 이루어져 있으니 2차원인 것이다.

## 소숫점 정렬


```python
temp_arr = np.trunc([-1.23, 1,23])
temp_arr
```




    array([-1.,  1., 23.])




```python
temp_arr = np.fix([-1.23, 1,23])
temp_arr
```




    array([-1.,  1., 23.])




```python
temp_arr = np.around([-1.23789, 1,23789], 4)
temp_arr
```




    array([-1.2379e+00,  1.0000e+00,  2.3789e+04])




```python
temp_arr = np.round([-1.23, 1,23], 4)
temp_arr
```




    array([-1.23,  1.  , 23.  ])




```python
temp_arr = np.floor([-1.23, 1,23])
temp_arr
```




    array([-2.,  1., 23.])




```python
temp_arr = np.ceil([-1.23, 1,23])
temp_arr
```




    array([-1.,  1., 23.])



## 다양한 배열 생성 방법


```python
temp_arr = np.arange(5) # range
temp_arr
```




    array([0, 1, 2, 3, 4])




```python
temp_arr = np.arange(1, 9, 3) # 1에서부터 9까지 3칸씩 띄어라
temp_arr
```




    array([1, 4, 7])



- np.zeros(()) 는 원하는 사이즈만큼 0으로 구성된 배열 생성


```python
zero_arr = np.zeros((2, 3)) # 원하는 사이즈만큼 0으로 구성된 배열 만들기
print(zero_arr)
print(type(zero_arr))
print(zero_arr.shape)
print(zero_arr.ndim)
print(zero_arr.dtype) # float64는 비트
```

    [[0. 0. 0.]
     [0. 0. 0.]]
    <class 'numpy.ndarray'>
    (2, 3)
    2
    float64
    

- flaot64, 이게 지금은 중요하지 않지만, 나중에 프로젝트를 할 때, 필요한 내용이다.
- 예를 들면, int32와 float64는 연산이 안된다.
- https://numpy.org/doc/stable/user/basics.types.html


- np.ones(())는 원하는 사이즈만큼 1로 구성된 배열 생성


```python
temp_arr = np.ones((4, 5), dtype="int32") # 원하는 사이즈만큼 1로 구성된 배열 만들기 
# dtype으로 비트유형을 바꿔줄 수 있다.

print(temp_arr)
print(type(temp_arr))
print(temp_arr.shape)
print(temp_arr.ndim)
print(temp_arr.dtype) 
```

    [[1 1 1 1 1]
     [1 1 1 1 1]
     [1 1 1 1 1]
     [1 1 1 1 1]]
    <class 'numpy.ndarray'>
    (4, 5)
    2
    int32
    

## reshape
- -1의 의미는 자동설정해준다는 것이다. 나중에 머신러닝할 때 유용하다.
- magic keyword라고 한다.


```python
temp_arr = np.ones((12, 12), dtype="int32") 
temp_res_arr = temp_arr.reshape(4, -1) # -1은 알아서 자동설정 해준다.


print(temp_res_arr)
print(type(temp_res_arr))
print(temp_res_arr.shape)
print(temp_res_arr.ndim)
print(temp_res_arr.dtype)
```

    [[1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1]
     [1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1]
     [1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1]
     [1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1]]
    <class 'numpy.ndarray'>
    (4, 36)
    2
    int32
    

## numpy 조건식
### np.where(조건식, 참, 거짓)
- 조건식이 하나일때 np.where()을 사용한다.



```python
temp_arr = np.arange(10)
temp_arr
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
# 5보다 작은 값은 원래값으로 반환
# 5보다 큰 값은 원래 값 * 10

np.where(temp_arr < 5, temp_arr, temp_arr * 10)
```




    array([ 0,  1,  2,  3,  4, 50, 60, 70, 80, 90])



- 퀴즈
- 0 ~ 100 까지의 배열 생성 후, 50보다 작은 값은 곱하기 10, 나머지는 그냥 원래 값 반환


```python
temp_arr = np.arange(101)
temp_arr
np.where(temp_arr < 50, temp_arr * 10, temp_arr)
```




    array([  0,  10,  20,  30,  40,  50,  60,  70,  80,  90, 100, 110, 120,
           130, 140, 150, 160, 170, 180, 190, 200, 210, 220, 230, 240, 250,
           260, 270, 280, 290, 300, 310, 320, 330, 340, 350, 360, 370, 380,
           390, 400, 410, 420, 430, 440, 450, 460, 470, 480, 490,  50,  51,
            52,  53,  54,  55,  56,  57,  58,  59,  60,  61,  62,  63,  64,
            65,  66,  67,  68,  69,  70,  71,  72,  73,  74,  75,  76,  77,
            78,  79,  80,  81,  82,  83,  84,  85,  86,  87,  88,  89,  90,
            91,  92,  93,  94,  95,  96,  97,  98,  99, 100])



### np.select(condlist, choicelist, default = )
- 사실 다중조건을 더 많이 사용한다.
- 이 때는 np.select를 사용한다.
- condlist는 조건식 리스트이다.
- choicelist는 조건식이 참일때 수행할 명령 리스트이다.
- condlist와 choicelist 요소들은 맞춰주어야 한다.
- default를 설정 안해주면 0인데, 아래에서 확인해보자.


```python
temp_arr = np.arange(10)
temp_arr

# 5보다 큰 수는 곱하기 2, 2보다 작은 값은 더하기 100

```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
condlist = [temp_arr > 5, temp_arr < 2] # 이거라면,
choicelist = [temp_arr * 2, temp_arr + 100] # 이렇게 해줘라
print(np.select(condlist, choicelist)) # default를 지정 안해주면, 조건에 맞지 않는 값들이 모두 0이 된다.
print(np.select(condlist, choicelist, default = temp_arr))
```

    [100 101   0   0   0   0  12  14  16  18]
    [100 101   2   3   4   5  12  14  16  18]
    

## 교재 넘파이 부분 손코딩 실습
- 도미와 빙어를 분류하는 머신러닝 코드짜기


```python
fish_length = [25.4, 26.3, 26.5, 29.0, 29.0, 29.7, 29.7, 30.0, 30.0, 30.7, 31.0, 31.0, 
                31.5, 32.0, 32.0, 32.0, 33.0, 33.0, 33.5, 33.5, 34.0, 34.0, 34.5, 35.0, 
                35.0, 35.0, 35.0, 36.0, 36.0, 37.0, 38.5, 38.5, 39.5, 41.0, 41.0, 9.8, 
                10.5, 10.6, 11.0, 11.2, 11.3, 11.8, 11.8, 12.0, 12.2, 12.4, 13.0, 14.3, 15.0]
fish_weight = [242.0, 290.0, 340.0, 363.0, 430.0, 450.0, 500.0, 390.0, 450.0, 500.0, 475.0, 500.0, 
                500.0, 340.0, 600.0, 600.0, 700.0, 700.0, 610.0, 650.0, 575.0, 685.0, 620.0, 680.0, 
                700.0, 725.0, 720.0, 714.0, 850.0, 1000.0, 920.0, 955.0, 925.0, 975.0, 950.0, 6.7, 
                7.5, 7.0, 9.7, 9.8, 8.7, 10.0, 9.9, 9.8, 12.2, 13.4, 12.2, 19.7, 19.9]

fish_data = [[l ,w] for l, w in zip(fish_length, fish_weight)]
fish_target = [1]*35 + [0]*14
```


```python
from sklearn.neighbors import KNeighborsClassifier
kn = KNeighborsClassifier()
```


```python
print(fish_data[4]) # fish_data의 다섯 번째 샘플 가져오기
```

    [29.0, 430.0]
    


```python
print(fish_data[0:5]) # fish_data의 처음 다섯 개의 샘플 가져오기
```

    [[25.4, 242.0], [26.3, 290.0], [26.5, 340.0], [29.0, 363.0], [29.0, 430.0]]
    


```python
train_input = fish_data[:35] # 처음부터 34번째 인덱스까지는 훈련 세트
train_target = fish_target[:35]
test_input = fish_data[35:] # 35번 부터 나머지까지는 테스트 세트
test_target = fish_target[35:]
```


```python
kn = kn.fit(train_input, train_target)
kn.score(test_input, test_target) # 정확도가 0...
```




    0.0



- 도미와 빙어가 골고루 섞여야 하는데 마지막 35번부터는 빙어만 있으니 제대로 학습을 못하게 된 것.
- 이것을 샘플링 편향 sampling bias
- 즉, 훈련 세트에 도미만 있기 때문에 테스트 세트가 무엇이든 도미로 판단하게 된다.
- 골고루 섞기 위해서 numpy 라이브러리가 필요하다.


```python
import numpy as np
input_arr = np.array(fish_data)
target_arr = np.array(fish_target)
print(input_arr) # 49개의 행(샘플)과 2개의 열(특성)
```

    [[  25.4  242. ]
     [  26.3  290. ]
     [  26.5  340. ]
     [  29.   363. ]
     [  29.   430. ]
     [  29.7  450. ]
     [  29.7  500. ]
     [  30.   390. ]
     [  30.   450. ]
     [  30.7  500. ]
     [  31.   475. ]
     [  31.   500. ]
     [  31.5  500. ]
     [  32.   340. ]
     [  32.   600. ]
     [  32.   600. ]
     [  33.   700. ]
     [  33.   700. ]
     [  33.5  610. ]
     [  33.5  650. ]
     [  34.   575. ]
     [  34.   685. ]
     [  34.5  620. ]
     [  35.   680. ]
     [  35.   700. ]
     [  35.   725. ]
     [  35.   720. ]
     [  36.   714. ]
     [  36.   850. ]
     [  37.  1000. ]
     [  38.5  920. ]
     [  38.5  955. ]
     [  39.5  925. ]
     [  41.   975. ]
     [  41.   950. ]
     [   9.8    6.7]
     [  10.5    7.5]
     [  10.6    7. ]
     [  11.     9.7]
     [  11.2    9.8]
     [  11.3    8.7]
     [  11.8   10. ]
     [  11.8    9.9]
     [  12.     9.8]
     [  12.2   12.2]
     [  12.4   13.4]
     [  13.    12.2]
     [  14.3   19.7]
     [  15.    19.9]]
    


```python
print(input_arr.shape) # shape 메서드로 배열 구성 확인. 49행 2열
```

    (49, 2)
    

- 넘파이 배열로 준비는 마쳤다.
- 여기에서 랜덤으로 추출해보자.
- 아예 인덱스를 섞은 다음 input_arr와 target_arr에서 샘플을 선택하면 무작위로 훈련 세트를 나누는 셈이 될 것이다.
- 넘파이 arange() 함수를 사용해서 0부터 48까지 1씩 증가하는 인덱스를 만든다.
- 인덱스를 랜덤하게 섞는다.
- 넘파이에서 무작위 결과를 만드는 함수들은 실행할 때마다 다른 결과를 만들기 때문에 일정한 결과를 얻으려면 랜덤 시드(random seed)를 지정해줘야 한다.


```python
np.random.seed(42) # 일정한 결과를 얻기 위한 랜덤 시드(random seed)
index = np.arange(49) # 0부터 48까지 1씩 증가하는 인덱스 생성
np.random.shuffle(index) # 인덱스를 랜덤하게 섞기
```

- 잘 만들어졌는지 체크해보자


```python
print(index)
```

    [13 45 47 44 17 27 26 25 31 19 12  4 34  8  3  6 40 41 46 15  9 16 24 33
     30  0 43 32  5 29 11 36  1 21  2 37 35 23 39 10 22 18 48 20  7 42 14 28
     38]
    

- 랜덤하게 섞인 인덱스를 가지고 전체 데이터를 훈련 세트와 테스트 세트로 나누자.
- 넘파이에 배열 인덱싱(array indexing) 기능 이용


```python
print(input_arr[[1,3]]) # input_arr 에서 두 번째와 네 번째 샘플 선택하여 추출
```

    [[ 26.3 290. ]
     [ 29.  363. ]]
    

- 랜덤하게 35개의 샘플을 훈련 세트로 만들기


```python
train_input = input_arr[index[:35]]
train_target = target_arr[index[:35]]
```

- 만들어진 index의 첫 번째 값은 13임을 확인했다. 따라서, train_input의 첫 번째 원소는 input_arr의 열 네 번째 원소가 들어있을 것이다. 확인해보자.


```python
print(input_arr[13], train_input[0]) # 동일하다
```

    [ 32. 340.] [ 32. 340.]
    

- 이번에는 나머지 14개를 테스트 세트로 만들자


```python
test_input = input_arr[index[35:]]
test_target = target_arr[index[35:]]
```

- 데이터 세트들이 잘 섞였는 지 산점도 그래프로 확인


```python
import matplotlib.pyplot as plt

plt.scatter(train_input[:,0], train_input[:,1]) # 파란색이 훈련 세트
plt.scatter(test_input[:,0], test_input[:,1])  # 주황색이 테스트 세트
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```


    
![png](/images/numpy_01/output_75_0.png)
    

