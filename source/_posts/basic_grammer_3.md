---
title: "파이썬 기초 문법 3"
author: "HS"
date: '2022-03-23'
---


# 클래스
## 클래스를 만드는 목적!
- 코드의 간결화
- 코드를 재사용
- 여러 라이브러리 --> 클래스로 구현이 됨
  + list 클래스, str 클래스
  + 객체로 씀
  + 변수명으로 정의!
- 여러 클래스들이 모여서 하나의 라이브러리가 됨.
  + 장고 / 웹개발 / 머신러닝 / 시각화/ 데이터 전처리
- 어렵다. 그러나 왜 쓰는지를 기억해야 한다. 모든 웹개발은 클래스로 구현된다. 지금 단계에서 클래스를 구현하는건 말도 안 된다.


```python
class Person: # class 대문자소문자소문자~:

  # class attribute    # 있어도 되고 없어도 되고
  country = "korean"

  # instance attribute
  def __init__(self, name, age): # 무조건 있어야 함.
    self.name = name
    self.age = age

if __name__ == "__main__":
  kim = Person("kim", 100)
  lee = Person("lee", 100)

  # access class attribute
  print("kim은 {}".format(kim.__class__.country))
  print("lee은 {}".format(kim.__class__.country))
```

    kim은 korean
    lee은 korean
    

## instance 메서드 생성
- list.appen(), list.extend()


```python
class Person: # class 대문자소문자소문자~:

  # class attribute    # 있어도 되고 없어도 되고
  country = "korean"

  # instance attribute
  def __init__(self, name, age): # 무조건 있어야 함.
    self.name = name
    self.age = age


  # instance method 정의
  def singing(self, songtitle):
    return "{} {}을 노래합니다.".format(self.name, songtitle)
if __name__ == "__main__":
  kim = Person("kim", 100)
  lee = Person("lee", 100)

  # access class attribute
  print("kim은 {}".format(kim.__class__.country))
  print("lee은 {}".format(kim.__class__.country))

  # call instance method
  print(kim.singing("A"))
  print(lee.singing("B"))
```

    kim은 korean
    lee은 korean
    kim A을 노래합니다.
    lee B을 노래합니다.
    

## 클래스 상속(inheritance)
- 부모님 유산...
  + 부모님 집 (냉장고, 세탁기, TV, etc) # 부모 클래스 instance method, attribute
  + 사용은 같이 함
- 여러분, 돈을 모음
  + 개인 노트북 구매 ( 여러분 각자 방에 비치) # 자식 클래스 instance method, attribute 추가 확장
  + 노트북은 내 거고, 추가 가전 제품을 구매해서 확장!


```python
class Parent:
  
  # instance attribute # init constructor
  def __init__(self, name, age):
    self.name = name
    self.age = age

  # instance method 정의
  def whoAmI(self):
    print("I am Parent!!")

  def singing(self, songtitle):
    return "{} {}을 노래합니다.".format(self.name, songtitle)
  
  def dancing(self):
    return "{} 현재 춤을 춥니다.".format(self.name)

class Child(Parent):
  def __init__(self, name, age):
    # super() function
    super().__init__(name, age) # 지금이야 두 줄이지 원래는 엄청 긴 줄
    print("Child Class is ON")

  def whoAmI(self):
    print("I am child")

  def studying(self):
    print("I am Fast Runner")

if __name__ == "__main__":
  child_kim = Child("kim", 15)
  parent_kim = Parent("kim", 45)
  print(child_kim.dancing())   # 자식은 춤을 춘다는 코드가 없는데 부모의 코드를 물려 받았다.
  print(child_kim.singing("연애")) # 마찬가지
  # print(parent_kim.studying()) # AttributeError: 'Parent' object has no attribute 'studying'
  child_kim.whoAmI()
  parent_kim.whoAmI()
```

    Child Class is ON
    kim 현재 춤을 춥니다.
    kim 연애을 노래합니다.
    I am child
    I am Parent!!
    

- AttributeError: 'Parent' object has no attribute 'studying'
- Parent 클래스에 studying 속성이 없더라.
- 부모는 자식의 물건을 쓰지 않는다. 


```python
class TV:
  def __init__(self):
    self.__maxprice = 500

  def sell(self):
    print("Selling Price: {}".format(self.__maxprice))

  def setMaxPrice(self, price):
    self.__maxprice = price

if __name__ == "__main__":
  tv = TV()
  tv.sell()

  # change price
  # 안 바뀌는 코드의 예시
  tv.__maxprice = 1000
  tv.sell()

  # setMaxprice
  # 값을 바꿀 수 있다!? 외부의 입력값을 업데이트 할 수 있다!
  tv.setMaxPrice(1000)
  tv.sell()
```

    Selling Price: 500
    Selling Price: 500
    Selling Price: 1000
    

## 클래스 내부에 조건문
- init constructor에 조건문을 써보자!


```python
class Employee:

  # init constructor
  # name, salary
  def __init__(self, name, salary = 0):
    self.name = name

    # 조건문 추가
    if salary > 0:
      self.salary = salary
    else:
      self.salary = 0
      print("급여는 0원이 될 수 없다!. 다시 입력하셈!")

  def update_salary(self, amount):
    # self.salary = self.salary + amount
    self.salary += amount

  def weekly_salary(self):
    return self.salary / 7

if __name__ == "__main__":
  emp01 = Employee("hs", -50000)
  print(emp01.name)
  print(emp01.salary)
  # emp01.salary = emp01.salary + 1500
  emp01.salary += 1500
  print(emp01.salary)
  emp01.update_salary(3000)
  print(emp01.salary)
  weekly_salary = emp01.weekly_salary()
  print(weekly_salary)

```

    급여는 0원이 될 수 없다!. 다시 입력하셈!
    hs
    0
    1500
    4500
    642.8571428571429
    

## 클래스 Docstring



```python
class Person:
  """
  사람을 표현하는 클래스

  ...

  Attributes
  ----------
  name : str
    name of the person

  age : int
    age of the person


  Methods
  ----------

  info(additional=""):
    Prints the person's name and age

  """

  def __init__(self, name, age):
    """
    Constructs all the neccessary attributes for the person object

    Parameters
    ----------
      name : str
        name of the person

      age : int
        age of the person
    """

    self.name = name
    self.age = age

  def info(self, additional=None):
    """
    귀찮음... 


    Parameters
    ----------
      additional : str, optional
        more info to be displayed (Default is None) / A, B, C 


    Returns
    -------
      None

    """

    print(f'My name is {self.name}. I am {self.age} years old. ' + additional)

if __name__ == "__main__":
  person = Person("Evan", age = 20)
  person.info("나의 직장은 00이야")
  help(Person)
                  
```

    My name is Evan. I am 20 years old. 나의 직장은 00이야
    Help on class Person in module __main__:
    
    class Person(builtins.object)
     |  Person(name, age)
     |  
     |  사람을 표현하는 클래스
     |  
     |  ...
     |  
     |  Attributes
     |  ----------
     |  name : str
     |    name of the person
     |  
     |  age : int
     |    age of the person
     |  
     |  
     |  Methods
     |  ----------
     |  
     |  info(additional=""):
     |    Prints the person's name and age
     |  
     |  Methods defined here:
     |  
     |  __init__(self, name, age)
     |      Constructs all the neccessary attributes for the person object
     |      
     |      Parameters
     |      ----------
     |        name : str
     |          name of the person
     |      
     |        age : int
     |          age of the person
     |  
     |  info(self, additional=None)
     |      귀찮음... 
     |      
     |      
     |      Parameters
     |      ----------
     |        additional : str, optional
     |          more info to be displayed (Default is None) / A, B, C 
     |      
     |      
     |      Returns
     |      -------
     |        None
     |  
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |  
     |  __dict__
     |      dictionary for instance variables (if defined)
     |  
     |  __weakref__
     |      list of weak references to the object (if defined)
    
    
