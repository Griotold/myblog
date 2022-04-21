---
title: "클래스 3 비공개속성"
author: "HS"
date: '2022-04-21'
categories: 'Python'
---

# 비공개 속성(Private attribute)
<!-- more-->
## 비공개 속성 사용하기
- 비공개 속성(private attribute) : 클래스 밖에서는 접근할 수 없고 클래스 안에서만 사용할 수 있는 속성
- 속성 앞에 밑줄 두개로 시작한다.


```python
# Person 클래스에 지갑 속성 __wallet 추가
class Person:
  def __init__(self, name, age, address, wallet):
    self.name = name
    self.age = age
    self.address = address
    self.__wallet = wallet  # 변수 앞에 밑줄 두개

leesin = Person('리신', 35, '아이오니아 어딘가', 10000)
# leesin.__wallet 에러 발생
# 클래스 밖에서 비공개 속성을 접근하면 에러 발생
```


```python
# pay 메서드 만들기
class Person:
  def __init__(self, name, age, address, wallet):
    self.name = name
    self.age = age
    self.address = address
    self.__wallet = wallet
  
  def pay(self, amount):
    self.__wallet -= amount # 비공개 속성은 클래스 안에서만 접근 가능
    print('이제 {0}원 남았네요.'.format(self.__wallet))

leesin = Person('리신', 35, '아이오니아 어딘가', 10000)
leesin.pay(3000)
```

    이제 7000원 남았네요.
    

## 비공개 메서드
- 속성뿐만 아니라 메서드도 동일하다.


```python
class Person:
  def __greeting(self):
    print('Hi')

  def hello(self):
    self.__greeting() # 클래스 안에서는 비공개 메서드를 호출할 수 있다.
  
  lux = Person('럭스', 21, '데마시아 궁전', 2000)
  # lux.__greeting()
  # 클래스 바깥에서는 비공개 메서드를 호출할 수 없다.
```

## 출처
- 파이썬 코딩 도장: 34.3 비공개 속성 사용하기
https://dojang.io/mod/page/view.php?id=2374
