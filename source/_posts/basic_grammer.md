---
title: "파이썬 기초 문법"
author: "HS"
date: '2022-03-21'
---

# Hello World



```python
print("Hello, World!")
```

    Hello, World!
    

# 주석 처리
- 코드 작업 시, 특정 코드에 대해 설명
- 사용자 정의 함수 작성 시, 클래스 작성 시..(도움말 작성..)



```python
# 한 줄 주석 처리
"""
여러 줄 주석 처리 시 (큰따옴표도 가능, 통일만 되면)
"""

print("Hello")
```

    Hello
    

# 변수 ( Scalar)
- 객체(object)로 구현이 됨
  + 하나의 자료형(Type)을 가진다. (이것만 기억!)
  + 클래스로 정의가 됨.
    - 다양한 함수들이 존재 함.

## int
- int 정수를 표현하는 데 사용함.


```python
# 데이터 전처리...
# 데이터 전처리를 잘해야! 분석도 잘함. 예측 모형도 잘 만듬.
# 데이터 전처리를 잘하기 위해서는 기초문법이 중요함.

num_int = 1
print(num_int)

print(type(num_int))
```

    1
    <class 'int'>
    

## float
- 실수를 표현하는데 사용한다.


```python
num_float = 0.2
print(num_float)
print(type(num_float))
```

    0.2
    <class 'float'>
    

## bool
- True와 False로 나타내는 Boolean 값을 표현하는 데 사용한다.



```python
bool_true = True
print(bool_true)
print(type(bool_true))

```

    True
    <class 'bool'>
    

## None
- Null을 나타내는 자료형으로 None이라는 한 가지 값만 가집니다.


```python
none_x = None
print(none_x)
print(type(none_x))
```

    None
    <class 'NoneType'>
    

# 사칙연산
- 정수형 사칙 연산


```python
a = 13
b = 47
print('a + b = ', a + b)
print(a - b )
print(a * b)
print(a / b) # 실수형을 반환한다!!!
print(a // b) # 나머지는 버린다.
print(a % b)  # 나머지만 가져온다.
print(a ** b) # a를 b제곱한다.
```

    a + b =  60
    -34
    611
    0.2765957446808511
    0
    13
    22664052024539238871968220999332552715703774239747717
    

## 실수형 사칙연산


```python
a = 13.0
b = 47.0
print('a + b = ', a + b)
print(a - b )
print(a * b)
print(a / b) # 실수형을 반환한다!!!
print(a // b) # 나머지는 버린다.
print(a % b)  # 나머지만 가져온다.
print(a ** b) # a를 b제곱한다.
```

    a + b =  60.0
    -34.0
    611.0
    0.2765957446808511
    0.0
    13.0
    2.2664052024539239e+52
    

# 논리형 연산자
- Bool 형은 True와 False 값으로 정의
- AND / OR


```python
x = 5 > 4
# print(x)
y = 3 > 4
# print(y)

print(x and x)
print(x and y)
print(y and x)
print(y and y)
print("----")
print(x or x)
print(x or y)
print(y or x)
print(y or y)

```

    True
    False
    False
    False
    ----
    True
    True
    True
    False
    

## 비교 연산자
- 부등호를 의미합니다.
- 비교 연산자를 True와 False값을 도출

## 논리 & 비교 연산자 응용


```python
var = input("입력하여 주세요..")
print(type(var))
```

    입력하여 주세요123
    <class 'str'>
    

- input은 문자열로 만들어버린다.
- 형변환을 해준다.
- 문자열, 정수, 실수 등등등


```python
var = int("1")
print(type(var))
```

    <class 'int'>
    


```python
var = int(input("숫자를 입력하여 주세요"))
print(type(var))
```

    숫자를 입력하여 주세요12345
    <class 'int'>
    


```python
num1 = int(input("숫자를 입력하여 주세요...")) # 10
num2 = int(input("숫자를 입력하여 주세요...")) # 3
num3 = int(input("숫자를 입력하여 주세요...")) # 5
num4 = int(input("숫자를 입력하여 주세요...")) # 7

var1 = num1  >= num2 # True
var2 = num3 < num4 # True
print(var1 and var2)
print(var1 or var2)
```

    숫자를 입력하여 주세요...10
    숫자를 입력하여 주세요...3
    숫자를 입력하여 주세요...5
    숫자를 입력하여 주세요...7
    True
    True
    

# 변수 (Non Scalar)
- 문자열을 입력



```python
print("'Hello, World!'")
print('"Hello, World!"')
```

    'Hello, World!'
    "Hello, World!"
    


```python
print("Hello world")
```

    Hello world
    

- 섞이면 안 된다.

## string 연산자
- 덧셈 연산자를 써보자.


```python
str1 = "Hello "
str2 = "World! "

print(str1 + str2)
```

    Hello World! 
    

- 곱셈 연산자를 사용해본다.



```python
greeting = str1 + str2
print(greeting * 4)
```

    Hello World! Hello World! Hello World! Hello World! 
    

## Indexing
- 문자열 인덱싱은 각각의 문자열 안에서 범위를 지정하여 특정 문자를 추출한다.



```python
greeting = "Hello Kaggle!"
print(greeting[6])
print(greeting[10])
```

    K
    l
    

- 0부터 시작해서 6번째가 "K"이다. 공백도 포함해서

# 슬라이싱
- 범위를 지정하고 데이터를 가져온다.


```python
greeting

print(greeting[:])
print(greeting[6:])
print(greeting[:6])
print(greeting[3:8]) # 끝은 n-1이 범위로 지정된다.
print(greeting[0:9:2]) # 여기서 2는 두 칸씩 뛰라는 소리
```

    Hello Kaggle!
    Kaggle!
    Hello 
    lo Ka
    HloKg
    


```python
# greeting[13] # 스트링 인덱스가 범위 밖에 있다는 에러 메세지
```

## 문자열을 바꾸려면
- 바꾸고 싶은 부분을 기준으로 나누고 원하는 문자를 삽입한다.


```python
a = "pithon"
a[:1]
a[2:]
a[:1] + 'y' + a[2:]
```




    'python'



## 문자열 포매팅
- 문자열 안의 특정한 값을 바꿔야 할 경우가 있을 때 사용하는 기법.


```python
"I eat %d apples." % 3

```




    'I eat five apples.'




```python
"I eat %s apples." % "five"
```




    'I eat five apples.'



- 숫자를 넣기 위해서는 %d
- 문자열을 넣기 위해서는 %s


```python
number = 3
"I eat %d apples." % number
```




    'I eat 3 apples.'



- 숫자를 바로 대입하나 위 처럼 숫자 값을 나타내는 변수를 대입하나 결과는 같다.


```python
number = 10
day = "three"
"I ate %d apples. so I was sick for %s days." %(number, day)
```




    'I ate 10 apples. so I was sick for three days.'



위 처럼 2개 이상의 값을 넣으려면 마지막 % 다음 괄호 안에 콤마로 구분하여 각각의 값을 넣어 주면 된다.

## 문자열 포맷 코드
- 정수와 문자열 외에도 다양한 것을 대이할 수 있다.
- %s 는 문자열
- %c 는 문자 1개(character)
- %d 는 정수(integer)
- %f 는 부동소수(floating-point)
- %o 는 8진수
- %x 는 16진수
- %% 는 Literal % (문자 % 자체)


```python
"I have %s apples." % 3

```




    'I have 3 apples.'




```python
"rate is %s" % 2.345
```




    'rate is 2.345'



- 흥미롭게도 %s 포맷 코드는 어떤 형태의 값이든 변환해 넣을 수 있다. 왜냐하면 % 뒤에 있는 값을 문자열로 바꾸기 때문이다.

### 포매팅 연산자 %d와 %를 같이 쓸때는 %%를 쓴다.


```python
"Error is %d%%." % 98
# %d%로 쓰면 'incomplete format'이란 에러가 뜬다.
```




    'Error is 98%.'



## 포맷 코드와 숫자 함께 사용하기
- 포맷 코드를 숫자와 함께 사용하면 더욱 유용하다
1. 정렬과 공백


```python
"%10s" % "hi"
```




    '        hi'



- %10s는 전체 길이가 10개인 문자열 공간에서 대입되는 값을 오른쪽으로 정렬하고 그 앞의 나머지는 공백으로 남겨 두라는 의미다.


```python
"%-10sjane" % 'hi'
```




    'hi        jane'



- hi를 왼쪽으로 정렬하고 나머지는 공백으로 채웠음을 볼 수 있다.

2. 소수점 표현하기



```python
"%0.4f" % 3.42134234
```




    '3.4213'



- 3.42134234를 소수점 네 번째 자리까지만 나타내고 싶은 경우에는 위와 같이 사용한다. '.' 뒤의 숫자 4는 소수점 뒤에 나올 숫자의 개수를 의미한다.


```python
"%10.4f" %3.42134234
```




    '    3.4213'



- 위 예는 숫자 3.42134234를 소수점 네 번째 자리까지만 표시하고 전체 길이가 10개인 문자열 공간에서 오른쪽으로 정렬하는 예를 보여준다.

## format 함수를 사용한 포맷팅
- 문자열의 format 함수를 사용하면 좀 더 발전된 스타일로 문자열 포맷을 지정할 수 있다.


```python
"I eat {0} apples".format(3)
```




    'I eat 3 apples'



- {0} 부분이 숫자 3으로 바뀌었다.


```python
number = 3
"I eat {0} apples".format(number)
```




    'I eat 3 apples'



- {0} 항목이 number 변수 값인 3으로 바뀌었다.


```python
number = 10
day = "three"
"I ate {0} apples. so I was sick for {1} days.".format(number, day)
```




    'I ate 10 apples. so I was sick for three days.'



- 2개 이상의 값을 넣을 경우 문자열의 {0}, {1}과 같은 인덱스 항목이 format 함수의 입력값으로 순서에 맞게 바뀐다. 


```python
"I ate {number} apples. so I was sick for {day} days.".format(number=10, day=3)
```




    'I ate 10 apples. so I was sick for 3 days.'



- name=value와 같은 형태의 입력값이 있어야만 한다.


```python
"I ate {0} apples. so I was sick for {day} days.".format(10, day=3)
```




    'I ate 10 apples. so I was sick for 3 days.'



- 위와 같이 인덱스 항목과 name=value 형태를 혼용하는 것도 가능하다.



```python
"{0:<10}".format("hi")
```




    'hi        '



- :<10 표현식을 사용하면 치환되는 문자열을 왼쪽으로 정렬하고 문자열의 총 자릿수를 10으로 맞출 수 있다.


```python
"{0:>10}".format("hi")
```




    '        hi'



- 위 예문은 오른쪽 정렬


```python
"{0:^10}".format("hi")
```




    '    hi    '



- 가운데 정렬은 :^ 기호를 사용한다.


```python
"{0:=^10}".format("hi")
```




    '====hi===='



- 정렬할 때 공백 대신 지정한 문자 값으로 채워 넣는 것도 가능하다. 채워 넣을 문자 값은 정렬 문자 <, >, ^ 바로 앞에 넣어야 한다.


```python
"{0:!<10}".format("hi")
```




    'hi!!!!!!!!'




```python
y = 3.42134234
"{0:0.4f}".format(y)
```




    '3.4213'



- 위 예는 format 함수를 사용해 소수점을 4자리까지만 표현하는 방법을 보여 준다.


```python
"{0:10.4f}".format(y)
```




    '    3.4213'



- 위 예는 자릿수를 10으로 맞춰준 것이다.

## f 문자열 포매팅
- 다음과 같이 문자열 앞에 f 접두사를 붙이면 f 문자열 포매팅 기능을 사용할 수 있다.
- f 문자열 포매팅은 표현식(변수와 +, -같은 수식을 함께 사용하는 것)을 지원한다.


```python
name = '홍길동'
age = 30
f'나의 이름은 {name}입니다. 나이는 {age}입니다.'
```




    '나의 이름은 홍길동입니다. 나이는 30입니다.'




```python
age = 30
f'나는 내년이면 {age+1}살이 된다.'
```




    '나는 내년이면 31살이 된다.'



- 딕셔너리는 f 문자열 포매팅에서 다음과 같이 사용할 수 있다.


```python
d = {'name':'홍길동', 'age':30}
f'나의 이름은 {d["name"]}입니다. 나이는 {d["age"]}입니다.'
```




    '나의 이름은 홍길동입니다. 나이는 30입니다.'



- 정렬은 다음과 같이 할 수 있다.


```python
f'{"hi":<10}' #왼쪽 정렬
f'{"hi":>10}' #오른쪽 정렬
f'{"hi":^10}' #가운데 정렬

```




    '    hi    '



- 공백 채우기


```python
f'{"hi":=^10}'
```




    '====hi===='



- 소수점 표현


```python
y = 3.42134234
f'{y:0.4f}'
```




    '3.4213'



## 문자열 관련 함수들
- 문자열 내장 함수

### count함수
- 문자 개수 세기


```python
a = "hobby"
a.count('b') #b의 개수를 돌려준다.
```




    2



### find함수
- 위치 알려주기1


```python
a = "python is the best choice"
a.find('b') # 14
a.find('k') # -1 
```




    -1



- 문자열 중 문자 b가 처음으로 나온 위치가 14라는 뜻
- 만약 k처럼 문자가 없으면 -1을 반환한다.

### index함수
- 위치 알려주기2



```python
a = "Life is too short"
a.index('t')
```




    8



- find함수와 마찬가지로 문자 t가 맨 처음으로 나온 위치를 반환한다.
- 만약 찾는 문자열이 존재하지 않는다면 오류를 발생시킨다.

### join 함수
- 문자열 삽입


```python
",".join('abcd')
```




    'a,b,c,d'



- abcd 문자열의 각각 ','를 삽입한다.

### upper 함수 / lower 함수
- 소문자를 대문자로 바꾸기
- 대문자를 소문자로 바꾸기


```python
a = "hi"
a.upper()
```




    'HI'



### lstrip 함수 / rstrip 함수 / strip 함수
- 왼쪽 공백 지우기
- 오른쪽 공백 지우기
- 양쪽 공백 지우기


```python
a = " hi "
a.lstrip()
```




    'hi '



### replace 함수
- 문자열 바꾸기


```python
a = "Life is too short"
a.replace("Life", "Your leg") #a.replace(바꾸고 싶은 문자열, 바꿀 문자열)
```




    'Your leg is too short'



### split 함수
- 문자열 나누기


```python
a = "Life is too short"
a.split()
b = "a:b:c:d"
b.split(':')
```




    ['a', 'b', 'c', 'd']



- a.split() 처럼 괄호안에 아무 값도 넣어 주지 않으면 공백을 기준으로 문자열을 나눈다.
- 만약 b.split(':') 처럼 괄호 안에 특정 값이 있을 경우에는 그걸 구분자로 한다. 

# 리스트
- 시퀀스 데이터 타입
- 데이터에 순서가 존재하냐! 슬라이싱이 가능해야 함.
- 대괄호('[값1, 값2, 값3]')


```python
a = [] # 빈 리스트 생성
a_func = list() # 빈 리스트 생성
b = [1] # 숫자가 요소가 될 수 있다.
c = ['apple'] # 문자열도 요소가 될 수 있다.
d = [1, 2, ['apple']] # 리스트 안에 또 다른 리스트를 요소로 넣을 수 있다.

print(a)
print(a_func)
print(b)
print(c)
print(d)

print(type(d))
```

    []
    []
    [1]
    ['apple']
    [1, 2, ['apple']]
    <class 'list'>
    

## 리스트 슬라이싱


```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# print(a)
print(a[0]) 
print(a[6:])
print(a[:5])
print(a[3:5])
print(a[4:7])
print(a[2:8])
print(a[1:9:3])
```

    1
    [7, 8, 9, 10]
    [1, 2, 3, 4, 5]
    [4, 5]
    [5, 6, 7]
    [3, 4, 5, 6, 7, 8]
    [2, 5, 8]
    


```python
a = [["apple", "banana", "cherry"], 1] # 중첩 리스트
print(a[0])
print(a[0][1])
print(a[0][0][4]) # 애플의 e
print(a[0][0][-1]) # 애플의 e
print(a[0][2][2]) # 체리의 e
print(a[0][2][-4]) # 체리의 e

```

    ['apple', 'banana', 'cherry']
    banana
    e
    e
    e
    e
    


```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(a[::-1]) # 역순
print(a[::2])

```

    [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
    [1, 3, 5, 7, 9]
    

## 리스트 연산자



```python
a = ["john", "evan"]
b = ["alice", "sarah"]

c = a + b
print(c)
d = b + a
print(d)
```

    ['john', 'evan', 'alice', 'sarah']
    ['alice', 'sarah', 'john', 'evan']
    


```python
c = a * 3
d = b * 0
print("a * 3 = ", c)
print("b * 0 = ", d) 
```

    a * 3 =  ['john', 'evan', 'john', 'evan', 'john', 'evan']
    b * 0 =  []
    

## 리스트 길이 구하기
- 리스트 길이를 구하기 위해서는 len 함수를 사용한다


```python
a = [1, 2, 3]
len(a)
```




    3



## 리스트 수정 및 삭제


```python
a = [0, 1, 2]
a[1] = "b"
print(a)
```

    [0, 'b', 2]
    

### 리스트 값 추가하기


```python
a = [100, 200, 300]
a.append(400)
print(a)
```

    [100, 200, 300, 400]
    

- a를 저장해주지 않았는데도 append메서드를 사용했더니 자동저장되었다. 파이썬에 이런게 은근 많다. 모두 알려고 하지 말고 만나는대로 습득하는 수밖에 없다.


```python
a.append([500, 600])
print(a) # 원하는 답이 안 나옴
```

    [100, 200, 300, 400, [500, 600]]
    


```python
a = [100, 200, 300]

a.extend([500, 600])
print(a)
```

    [100, 200, 300, 500, 600]
    


```python
a = [ 0, 1, 2]
# a.insert(인덱스번호, 넣고자하는 값)
a.insert(1, 100)
print(a)
```

    [0, 100, 1, 2]
    

### 리스트 값 삭제하기


```python
a = [4, 3, 2, 1, "A"]
a.remove(1) # 리스트에서 첫번째로 나오는 값을 삭제(인덱스 번호가 아니다)
print(a)
a.remove("A")
print(a)
```

    [4, 3, 2, 'A']
    [4, 3, 2]
    


```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

del a[1] # 인덱스 번호
print(a)

del a[1:5]
print(a) # 3, 4, 5, 6이 지워짐
```

    [1, 3, 4, 5, 6, 7, 8, 9, 10]
    [1, 7, 8, 9, 10]
    

### pop 함수
- 리스트의 맨 마지막 요소를 돌려주고 그 요소는 삭제한다.


```python
b = ["a", "b", "c", "d"]
x = b.pop()
print(x)
print(b)
```

    d
    ['a', 'b', 'c']
    

### 그 외 메서드


```python
a = [0, 1, 2, 3]
print(a)

a.clear()
print(a)
```

    [0, 1, 2, 3]
    []
    


```python
a = ["a", "a", "b", "b"]
print(a.index("a"))
print(a.index("b"))
```

    0
    2
    


```python
a = [1, 4, 5, 2, 3]
b = [1, 4, 5, 2, 3]

a.sort()
print("sort(): ", a)

# 내림차순, sort()
b.sort(reverse=True)
print("sort(reverse=True): ", b)
```

    sort():  [1, 2, 3, 4, 5]
    sort(reverse=True):  [5, 4, 3, 2, 1]
    

- 내림차순 같은 옵션을 알아내는 방법은 구글링이다. 


```python
c = [4, 3, 2, 'a']
# c.sort() 
```

### reverse 함수
- 리스트 뒤집기
- 리스트를 역순으로 


```python
a = ['a', 'b', 'c']
a.reverse()
print(a)
```

    ['c', 'b', 'a']
    

### index 함수
- 위치 반환


```python
a = [1, 2, 3]
a.index(3) # 3의 인덱스값은 2이다.
```




    2



### extend
- 리스트 확장
- extend(x)에서 x에는 리스트만 올 수 있다.
- a.extend([4, 5])는 a += [4, 5]와 동일하다.


```python
a = [1, 2, 3]
a.extend([4, 5])
print(a)
b = [6, 7]
a.extend(b)
print(a)
```

    [1, 2, 3, 4, 5]
    [1, 2, 3, 4, 5, 6, 7]
    

# 튜플
- List와 비슷하다.
- 슬라이싱, 인덱싱 등등
- (vs 리스트) : 튜플은 수정 삭제가 안된다.


```python
tuple1 = (0) # 끝에 콤마(,)를 붙이지 않을 때 --> int
tuple2 = (0,) # 끝에 콤마 붙일 때 --> tuple
tuple3 = 0, 1, 2 # 괄호를 생략해도 무방하다.
print(type(tuple1)) 
print(type(tuple2)) 
print(type(tuple3)) 
```

    <class 'int'>
    <class 'tuple'>
    <class 'tuple'>
    


```python
a = (0, 1, 2, 3, 'a')
print(type(a))

# del a[4] -> 튜플은 수정이 안된다.
# a[1] = "b" -> 튜플은 수정이 안된다.
```

    <class 'tuple'>
    

## 튜플 인덱싱 및 슬라이싱 하기


```python
a = (0, 1, 2, 3, 'a')
print(a[1])
print(a[3])
print(a[4])
```

    1
    3
    a
    

## 더하기 곱셈 연산자 사용


```python
t1 = (0, 1, 2, 3)
t2 = (4, 5, 6 ,7)
print(t1 + t2)
print(t1 * 3)
print(t2 * 0)

```

    (0, 1, 2, 3, 4, 5, 6, 7)
    (0, 1, 2, 3, 0, 1, 2, 3, 0, 1, 2, 3)
    ()
    

# 딕셔너리

- key-value값으로 나뉨.


```python
dict_01 = {'teacher' : 'evan',
           'class' : 601,
           'student' : 24,
           '학생이름' : ['A', 'Z']}
print(dict_01)
print(dict_01['teacher'])
print(dict_01['class'])
print(dict_01['학생이름'])
# print(dict_01['선생님'])
```

    {'teacher': 'evan', 'class': 601, 'student': 24, '학생이름': ['A', 'Z']}
    evan
    601
    ['A', 'Z']
    


```python
print(dict_01.keys())
```

    dict_keys(['teacher', 'class', 'student', '학생이름'])
    


```python
print(dict_01.values())
```

    dict_values(['evan', 601, 24, ['A', 'Z']])
    


```python
dict_01.items() # 튜플 형태로 묶이더라
```




    dict_items([('teacher', 'evan'), ('class', 601), ('student', 24), ('학생이름', ['A', 'Z'])])




```python
print(dict_01.get("teacher")) # get메서드
print(dict_01.get("선생님"))
print(dict_01.get("class"))
# print(dict_01['선생님']) # get을 써주는 이유. 키 값이 없을 때 None을 떨궈주면서 다음 줄을 실행시켜준다.
print(dict_01.get("students"))
print(dict_01.get("선생님", "없어용")) # None말고 지정한 값 떨궈주는 방법
```

    evan
    None
    601
    None
    없어용
    

# 조건문 & 반복문
## 조건문
- 일상에서 조건문 언제쓸까요?



```python
weather = "비"
if weather == "비": # 조건식 True가 나오면 
  print("우산을 가져간다.")
else:
  print("우산을 가져가지 않는다.") 
```

    우산을 가져간다.
    

- 등급표를 만들어보자
- 60점 이상 합격 / 그외는 불합격
- 숫자는 아무거나 써도 상관없음


```python
score = 61
if score >= 60 :
  print("합격")
else:
  print("불합격")
```

    합격
    


```python
score = int(input("점수를 입력하세요...")) # input은 문자열로 인식을 하니까 정수형으로 형변환

if score >= 60 :
  print("합격")
else:
  print("불합격")
```

    점수를 입력하세요...70
    합격
    

- 등급으로 나눠보자
- 90점 이상은 A등급
- 80점 이상은 B등급
- 나머지는 F등급
- if-elif-else


```python
score = int(input("점수를 입력해 주세요: "))

if score >= 90:
  print("A등급")
elif score >= 80:
  print("B등급")
else:
  print("F등급")
```

    점수를 입력해 주세요: 95
    A등급
    

## 반복문
- 안녕하세요! 10번 반복하세요.


```python
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
print("안녕하세요!")
```

- 2번째 과제 : 안녕하세요! 789256번 반복하세요.


```python
# 789... 뭐시기 반복하기
for i in range(3):
  print(i + 1, "안녕하세요!")
```

    1 안녕하세요!
    2 안녕하세요!
    3 안녕하세요!
    


```python
count = range(3)
print(count)

for n in count:
  print(n)
```

    range(0, 3)
    0
    1
    2
    


```python
count = range(50)
print(count)

for n in count:
  print(str(n + 1) + "번째")
  if (n + 1) == 5:
    print("그만")
    break
  print("슈팅")
```

    range(0, 50)
    1번째
    슈팅
    2번째
    슈팅
    3번째
    슈팅
    4번째
    슈팅
    5번째
    그만
    


```python
a = "hello"

for x in a:
  if x == "l":
    break
  print(x)
```

    h
    e
    

- 반복문 작성 방식은 다양하다.
- zip, range, enumerate, len 등등


```python
alphabets = ['A', 'B', 'c']
for index, value in enumerate(alphabets):
  print(index, value)
```

    0 A
    1 B
    2 c
    
