---
title: "클래스 (Class)"
author: "HS"
date: '2022-04-11'
categories: 'Python'
---
- 객체를 표현하는 문법
- 객체를 만들때 유용하다.
- 클래스 안에 속성(attribute)과 메서드(method)가 있다.
<!-- more-->
## 쉬운 비유
- 과자 틀이 클래스, 과자를 객체라고 생각하자.


## 클래스 만들기
- 클래스 이름은 대문자로 시작한다.
- 코드는 반드시 들여쓰기 해야한다.


```python
class Person: # 클래스 이름
  def greeting(self): # 메서드
    print('Hi') # 코드
```

## 만든 클래스 사용해보기


```python
ester = Person()
```

- ester가 Person의 인스턴스(instance)이다.
- 클래스는 특정 개념을 표현만 할 뿐 사용하려면 인스턴스를 생성해야 한다.
- 객체를 생성해야 한다는 소리다.

## 메서드 호출하기


```python
ester.greeting()
```

    Hi
    

- 이렇게 인스턴스를 통해 호출하는 메서드를 **인스턴스 메서드** 라고 한다.

## 사칙연산 클래스 만들기


```python
class Fourcal:
  pass
```


```python
a = Fourcal()
type(a)
```




    __main__.Fourcal




```python
class Fourcal:
  def setdata(self, first, second):
    self.first = first
    self.second = second
```


```python
a = Fourcal()
a.setdata(4, 2)
```

- setdata 메서드에는 총 3개의 매개변수(self, first, second)를 전달해줘야 할 것 같은데 왜 2개만 전달해줬을까?
- self에는 객체 a가 자동으로 전달되기 떄문이다.


```python
a = Fourcal()
a.setdata(4, 2)
print(a.first)
print(a.second)
```

    4
    2
    

- 더하기 기능 만들기


```python
class Fourcal:
  def setdata(self, first, second):
    self.first = first
    self.second = second
  def add(self):
    result = self.first + self.second
    return result
```


```python
a = Fourcal()
a.setdata(4, 2)
print(a.add())
```

    6
    

- 빼기,곱하기, 나누기 추가


```python
class Fourcal:
  def setdata(self, first, second):
    self.first = first
    self.second = second
  def add(self):
    result = self.first + self.second
    return result
  def mul(self):
    result = self.first * self.second
    return result
  def sub(self):
    result = self.first - self.second
    return result
  def div(self):
    result = self.first / self.second
    return result
```


```python
a = Fourcal()
b = Fourcal()
a.setdata(4, 2)
b.setdata(3, 8)
print(a.add())
print(a.mul())
print(a.sub())
print(a.div())

```

    6
    8
    2
    2.0
    

## 파이썬에서 흔히 보는 클래스
- int
- list
- dict


```python
a = int(7)
a
```




    7




```python
b = list(range(10))
b
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
c = dict(x=10, y=20)
c
```




    {'x': 10, 'y': 20}



# list 클래스에서 메서드 append 호출하기


```python
b.append(20)
b
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 20]



## type으로 객체(인스턴스)가 어떤 클래스인지 식별하기


```python
print(type(a))
print(type(b))
print(type(c))
print(type(ester))

```

    <class 'int'>
    <class 'list'>
    <class 'dict'>
    <class '__main__.Person'>
    

## 빈 클래스 만들기


```python
class Piano:
  pass
```

## 메서드 안에서 메서드 호출하기


```python
class Person:
  def greeting(self):
    print('Helu')

  def hello(self):
    self.greeting()

dexter = Person()
dexter.hello()
```

    Helu
    

## isinstance 함수
- 현재 인스턴스가 특정 클래스의 인스턴스인지 확인


```python
class Pineapple:
  pass

codi = Pineapple()
isinstance(codi, Pineapple)
```




    True



### isinstance 함수 활용
- 팩토리얼 함수를 만들기 위해
- n이 int 클래스의 인스턴스인지 확인하는데 활용되었다.


```python
def factorial(n):
  if not isinstance(n, int) or n < 0:
    return None
  if n == 1:
    return 1
  return n * factorial(n -1)
  
factorial(5)
```




    120



## 출처
- 파이썬 코딩도장 : 클래스와 메서드 만들기
https://dojang.io/mod/page/view.php?id=2372
- 점프 투 파이썬 : 클래스
https://wikidocs.net/28
