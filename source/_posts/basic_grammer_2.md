---
title: "파이썬 기초 문법 2"
author: "HS"
date: '2022-03-22'
---

# 기초 문법 리뷰


```python
# 리스트
book_list = ["a", "b", "c"]
# append, extend, insert, remove, pop, etc

# 튜플
book_tuple = ("A", "B", "C")
# 수정 삭제가 불가능하다

# 딕셔너리
book_dictionary = {"책 제목" : ["오베", "셜록", "파운데이션]
                  "출판년도" : [2001, ]}
#keys(), values(), items(), get()
```

## 조건문 & 반복문



```python
if True:
  print("코드 실행")   # 들여쓰기 안하면 에러가 난다.
elif True:
  print("코드 실행")
else:
  print("코드 실행")
```

## for문
### for문의 기본 구조


```python
for 변수 in 리스트(또는 튜플, 문자열):
  수행할 문장1
  수행할 문장2
```

### 전형적인 for문


```python
test_list = ['one', 'two', 'three']
for i in test_list:
  print(i)
```

    one
    two
    three
    

### 다양한 for문의 사용


```python
a = [(1,2), (3,4), (5,6)]
for (first, last) in a:
  print(first + last)
```

    3
    7
    11
    

- 위 예는 a 리스트의 요솟값이 튜플이기 때문에 각각의 요소가 자동으로 변수에 대입된다.

### for문의 응용


```python
marks = [90, 25, 67, 45, 80]

number = 0
for mark in marks:
  number = number + 1
  if mark >= 60:
    print("%d번 학생은 합격입니다." % number)
  else:
    print("%d번 학생은 불합격입니다." % number)
```

    1번 학생은 합격입니다.
    2번 학생은 불합격입니다.
    3번 학생은 합격입니다.
    4번 학생은 불합격입니다.
    5번 학생은 합격입니다.
    

### for문과 continue
- while문 처럼 continue 사용가능하다. 즉 for문 맨 처음으로 돌아가게 된다.


```python
marks = [90, 25, 67, 45, 80]

number = 0
for mark in marks:
  number = number + 1
  if mark < 60:
    continue
  print("%d번 학생 축하합니다. 합격입니다. " % number)
```

    1번 학생 축하합니다. 합격입니다. 
    3번 학생 축하합니다. 합격입니다. 
    5번 학생 축하합니다. 합격입니다. 
    


```python
for i in range(3):
  print(i+1, "hel")
```

    1 hel
    2 hel
    3 hel
    


```python
book_list = ["프로그래밍 R", "혼자 공부하는 머신러닝"]
for book in book_list:
  print(book)
```

    프로그래밍 R
    혼자 공부하는 머신러닝
    


```python
strings01 = "Hello World"
for char in strings01:
  print(char)
```

    H
    e
    l
    l
    o
     
    W
    o
    r
    l
    d
    


```python
num_tuple = (1, 2, 3, 4)  # 튜플도 동일
for num in num_tuple:
  print(num)
```

    1
    2
    3
    4
    


```python
num_dict = {"A": 1, "B" : 2} # 딕셔너리는 뭔가 불안정
for num in num_dict:
  print(num)
```

    A
    B
    

## 반복문의 필요성



```python
product_name = ["요구르트", "우유"]
prices = [1000, 1500]
quantities = [5, 3]

name = product_name[0]
sales = prices[0] * quantities[0]
print(name + "의 매출액은 " + str(sales) + "원이다.")

name = product_name[1]
sales = prices[1] * quantities[1]
print(name + "의 매출액은 " + str(sales) + "원이다.")


```

    요구르트의 매출액은 5000원이다.
    우유의 매출액은 4500원이다.
    

- 반복문이 필요하다!


```python
product_name = ["요구르트", "우유"]
prices = [1000, 1500]
quantities = [5, 3]

for i in range(len(product_name)):
  name = product_name[i]
  sales = prices[i] * quantities[i]
  print(name + "의 매출액은 " + str(sales) + "원이다.")  
  # print도 반복문 안에 있음을 기억하자(들여쓰기)


```

    요구르트의 매출액은 5000원이다.
    우유의 매출액은 4500원이다.
    

- 만약, 항목의 개수를 모른다면???
- 모르는게 생기면 구글링을 해야한다
- 구글 검색 엔진: how to count list in python
- 그렇게 해서 len함수를 찾아 냈다.

- 반복문을 바로 작성할 필요가 없다. 그러면 헷갈린다. 하나씩 직접해보고, 패턴을 발견하고, 그리고 짜는 것이다.

## while문
- 얘도 반복문이다
- 조건식이 들어가는 것이 포인트(vs. for-loop는 정해진 범위가 포인트)



```python
count = 0   # 처음에 상수가 들어가야 한다.
while count < 5: # 여기 조건식이 True가 나와야 한다. False가 나오면 실행 중지.
  count = count + 1
  print(count, "안녕하세요..")
print("5를 초과했군요!")
```

    1 안녕하세요..
    2 안녕하세요..
    3 안녕하세요..
    4 안녕하세요..
    5 안녕하세요..
    5를 초과했군요!
    

- 조건식이 만족할 때까지 계속 실행되다가 만족하지 않을 때 while문은 끝이 난다.
- 두 번째 방식 : 숫자를 차감하면서 반복하는 방식


```python
count = 3   
while count > 0: 
  count = count - 1
  print(count, "안녕하세요..")
print("0 미만 이군요!")
```

    2 안녕하세요..
    1 안녕하세요..
    0 안녕하세요..
    0 미만 이군요!
    

### "열 번 찍어 안 넘어가는 나무 없다"


```python
treeHit = 0
while treeHit < 10:
  treeHit = treeHit +1 # treeHit += 1
  print("나무를 %d번 찍었습니다." % treeHit)
  if treeHit == 10:
    print("나무 넘어갑니다.")
```

    나무를 1번 찍었습니다.
    나무를 2번 찍었습니다.
    나무를 3번 찍었습니다.
    나무를 4번 찍었습니다.
    나무를 5번 찍었습니다.
    나무를 6번 찍었습니다.
    나무를 7번 찍었습니다.
    나무를 8번 찍었습니다.
    나무를 9번 찍었습니다.
    나무를 10번 찍었습니다.
    나무 넘어갑니다.
    

### while문 강제로 빠져나가기(break)
- 커피 자판기 예


```python
coffee = 10
money = 300
while money:
  print("돈을 받았으니 커피를 줍니다.")
  coffee = coffee -1
  print("남은 커피의 양은 %d개입니다." % coffee)
  if coffee == 0:
        print("커피가 다 떨어졌습니다. 판매를 중지합니다.")
        break
```

    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 9개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 8개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 7개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 6개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 5개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 4개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 3개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 2개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 1개입니다.
    돈을 받았으니 커피를 줍니다.
    남은 커피의 양은 0개입니다.
    커피가 다 떨어졌습니다. 판매를 중지합니다.
    

### while문의 맨 처음으로 돌아가기(continue)


```python
a = 0
while a < 10:
  a = a + 1
  if a % 2 == 0: continue # a가 짝수라면
  print(a)
```

    1
    3
    5
    7
    9
    

- continue는 while문 맨 처음으로 돌아가게 한다.(조건문: a<10)

- 개발자를 지향한다면, while문 공부를 좀 더 비중있게 다루는 게 좋다.
- 데이터 분석가를 지향한다면, while문을 쓸 일이 별로 없다. for-loop 공부를 좀 더 비중있게 하는 게 좋다.

## 사용자 정의 함수 (User-Defined Function)
- 이거 왜 쓸까?

### 클래스(Class)를 왜 쓸까?

- 코드의 반복성을 줄이기 위해서 사용하는 것이다.

### len() ---> 누군가가 만들었고, 우리는 그걸 그냥 쓰는 것이다.
- 리스트의 길이 구할 때 쓴다.
- 리스트의 전체 길이를 구하겠다!? -> 1회성? 나만 쓰는가?  


```python
def 함수명():
  # 코드 실행
  return 값

함수명()
```


```python
# 더하기 함수 만들기
def add(a, b):
  c = a + b
  return c

if __name__ == "__main__":
  a = 1
  b = 2
  c = add(a, b)
  print(c)


```

    3
    


```python
# 빼기 함수 만들기
def minu(a, b):
  c = a - b
  return c

minu(1, 2)
```




    -1




```python
# 곱하기 함수 만들기
def multi(a, b):
  c = a * b
  return c

multi(1, 2)
```




    2




```python
# 나누기 함수 만들기
def divis(a, b):
  c = a / b
  return c

divis(1, 2)
```




    0.5



jupyter notebook, .ipynb 확장자명
.py로 저장 (pycharm..)
- basic.py로 저장할 때, 예시


```python
# /user/local/bin/python
# -*- coding: utf-8 -*-

def divis(a, b):
  c = a / b
  return c

if __name__ == "__main__":
  a = 1
  b = 2
  c = divis(a, b)
  print(c)
```

## 파이썬 함수 주석 처리
- docstring 작업
- 나중에 프로젝트할 때 필요할 것이다.
- 코드 작성 마지막 단계에서 필히 추가해야할 내용이다.


```python
# /user/local/bin/python
# -*- coding: utf-8 -*-

def temp(content, letter):
  """content안에 있는 문자를 세는 함수입니다.                
  
  Args:
    content(str) : 탐색 문자열
    letter(str)  : 찾을 문자열

  Returns:
    int
  """
  print("함수 테스트")
  
  cnt = len([char for char in content if char == letter])

  return cnt

if __name__ == '__main__':
  help(temp)
```

    Help on function temp in module __main__:
    
    temp(content, letter)
        content안에 있는 문자를 세는 함수입니다.                
        
        Args:
          content(str) : 탐색 문자열
          letter(str)  : 찾을 문자열
        
        Returns:
          int
    
    

## 리스트 컴프리헨션
- for-loop를 한 줄로 처리
- 리스트 안에 for-loop를 쓸 수 있다.
- 어렵다.


```python
my_list = [[10], [20, 30]]
# print(my_list)

# 결과값 : [10, 20 ,30]으로 만들고 싶다.

flattened_list = []
for value_list in my_list:
  # print(value_list)
  for value in value_list:
    print(value)
    flattened_list.append(value)

print(flattened_list)
```

    10
    20
    30
    [10, 20, 30]
    


```python
my_list = [[10], [20, 30]]
flattened_list = [value for value_list in my_list for value in value_list]
print(flattened_list)
```

    [10, 20, 30]
    


```python
# 다른 예제
letters = []
for char in "helloworld":
  letters.append(char)
print(letters)
```

    ['h', 'e', 'l', 'l', 'o', 'w', 'o', 'r', 'l', 'd']
    


```python
letters2 = [char for char in "helloworld"]
print(letters2)
```

    ['h', 'e', 'l', 'l', 'o', 'w', 'o', 'r', 'l', 'd']
    

## 사용자 정의 함수 다시


```python
def mean_and_median(value_list):
  """숫자 리스트의 요소들의 평균과 중간값을 구하는 코드를 작성해라
  Args:
    value_list (iterable of int / float): A list of int numbers 
  
  Returns:
    tuple(float, float)
  """
  
  # 평균
  mean = sum(value_list) / len(value_list)

  # 중간값
  midpoint = int(len(value_list) / 2)
  if len(value_list) % 2 == 0:
    median = (value_list[midpoint - 1] + value_list[midpoint]) / 2
  else:
    median = value_list[midpoint]

  return mean, median

if __name__ == "__main__":
  value_list = [1, 1, 2, 2, 3, 4, 5]
  avg, median = mean_and_median(value_list)
  print("avg:", avg)
  print("median:", median)
```

    avg: 2.5714285714285716
    median: 2
    

- 데코레이터, 변수명 immutable or mutable, context manager 등의 내용은 점프 투 파이썬에 없다. 파이썬 코딩 도장에 있다.
