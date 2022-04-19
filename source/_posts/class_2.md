---
title: "클래스 2 생성자와 속성"
author: "HS"
date: '2022-04-19'
categories: 'Python'
---
## 생성자(constructor)
<!-- more-->

```python
# 기존의 만든 FourCal 클래스
class FourCal:
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

- 객체에 초깃값을 설정해야 할 필요가 있을 때는 생성자를 구현하는 것이 안전한 방법이다.
- 생성자란 객체가 생성될 때 자동으로 호출되는 메서드를 의미한다.
- 생성자를 한 번 추가해보자.


```python
class FourCal:
  # 생성자 부분
  def __init__(self, first, second):
    self.first = first
    self.second = second
  
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

- init 매서드는 setdata메서드와 이름만 다르고 모든 게 동일하다. 
- 객체가 생성되는 시점에 자동으로 호출되는 차이만 있을 뿐이다.


```python
a = FourCal(4, 2)
print(a.first)
print(a.second)
print(a.add())
print(a.div())

```

    4
    2
    6
    2.0
    

## 클래스 속성 사용하기


```python
class Person:
  bag = []

  def put_bag(self, stuff):
    self.bag.append(stuff)

james = Person()
james.put_bag('book')

maria = Person()
maria.put_bag('열쇠')

print(james.bag)
print(maria.bag)
```

    ['book', '열쇠']
    ['book', '열쇠']
    

- 제임스 가방에는 책을 마리아 가방에는 열쇠를 넣었는데 두 가방 모두 두 개의 소품이 드가있다.
- 클래스 속성은 클래스에 속해 있으며 모든 인스턴스에서 공유한다.
- 클래스 속성에 접근할 때는 클래스 이름으로 접근하는 것이 더 명확하다.


```python
class Person:
  bag = []

  def put_bag(self, stuff):
    Person.bag.append(stuff) # 클래스 이름으로 클래스 속성에 접근
```

## 속성, 메서드를 찾는 순서
- 보통 인스턴스, 클래스 순으로 찾는다.


```python
james.__dict__
Person.__dict__
```




    mappingproxy({'__dict__': <attribute '__dict__' of 'Person' objects>,
                  '__doc__': None,
                  '__module__': '__main__',
                  '__weakref__': <attribute '__weakref__' of 'Person' objects>,
                  'bag': [],
                  'put_bag': <function __main__.Person.put_bag>})



## 속성 사용 하기
- init 메서드 안에서 self.속성에 값을 할당한다.
- 속성은 init 메서드에서 만든다는 점과 self에 점을 붙인 뒤 값을 할당한 다는 점이 중요하다.


```python
class Person:
  def __init__(self):
    self.hello = '안녕하세요.'

  def greeting(self):
    print(self.hello)

james = Person()
james.greeting()
```

    안녕하세요.
    

- init 메서드에서 self.hello에 '안녕하세요'를 넣었다.
- init 메서드는 인스턴스를 만들 때 호출되는 메서드이다.
- init 메서드는 initialize를 줄인 말로 인스턴스를 초기화시킨다.
- 특히 앞뒤로 밑줄 두개가 붙은 메서드는 스페셜 메서드(special method) 또는 매직 메서드(magic method)라고 부르며, 파이썬이 자동으로 호출해주는 메서드이다.

## 인스턴스(객체)를 만들 때 값 받기
- init 메서드에서 self 다음에 값을 받을 매개변수를 지정한다.
- 매개변수를 self.속성에 넣어준다.
- 속성에 접근할 때는 "self.속성"의 형식으로 사용해야한다.


```python
class Person:
  def __init__(self, name, age, address):
    self.hello = '안녕하세요.'
    self.name = name
    self.age = age
    self.address = address

  def greeting(self):
    print('{0} 저는 {1}입니다.'.format(self.hello, self.name)) # 속성에 접근할 때

karina = Person('카리나', 23, '경기도 수원시 팔달구 지동')
karina.greeting()
```

    안녕하세요. 저는 카리나입니다.
    

## 클래스 밖에서 속성에 접근할 때
- 클래스 안에서는 "self.속성" 형식이었다.
- 밖에서 속성에 접근할 때는 "인스턴스.속성" 형식으로 접근한다.
- 인스턴스 속성 : 인스턴스를 통해 접근하는 속성


```python
print('이름:', karina.name)
print('나이:', karina.age)
print('주소:', karina.address)
```

    이름: 카리나
    나이: 23
    주소: 경기도 수원시 팔달구 지동
    

## 위치 인수와 키워드 인수
- 위치 인수의 경우, *args를 사용.
- 매개변수에서 값을 가져오려면 args[숫자]의 형식으로 사용.


```python
class Person:
  def __init__(self, *args):
    self.name = args[0]
    self.age = args[1]
    self.address = args[2]

winter = Person(*['김민정', 22, '부산광역시 중구 남포동'])

print('이름:', winter.name)
print('나이:', winter.age)
print('주소:', winter.address)

```

    이름: 김민정
    나이: 22
    주소: 부산광역시 중구 남포동
    

- 키워드 인수의 경우, **kwargs 사용
- 매개변수에서 값을 가져오려면 "kwargs['속성']"의 형식으로 사용.


```python
class Person:
  def __init__(self, **kwargs):
    self.name = kwargs['name']
    self.age = kwargs['age']
    self.address = kwargs['address']

ningning = Person(**{'name': '닝이줘', 'age': 21, 'address': '헤이룽장성 하얼빈시'})

print('이름:', ningning.name)
print('나이:', ningning.age)
print('주소:', ningning.address)
```

    이름: 닝이줘
    나이: 21
    주소: 헤이룽장성 하얼빈시
    

## 인스턴스를 생선한 후에 속성 추가하기
- 인스턴스를 만든 후에도 속성을 추가할 수 있다.
- "인스턴스.속성 = 값"
- 이렇게 추가한 속성은 해당 인스턴스에만 생성된다. 


```python
# 빈 클래스 만든 뒤 속성 추가하기
class Person:
  pass

giselle = Person()
giselle.name = '우치나가 애리'
print('이름:', giselle.name)

```

    이름: 우치나가 애리
    

## 특정 속성만 허용, 다른 속성은 제한
- slots에 허용할 속성 이름을 리스트로 넣어주면 된다.


```python
class Person:
  __slots__ = ['name', 'age']

samira = Person()
samira.name = '사미라'
samira.age = 27
# samira.address = '슈리마국 아마크라시'
# 허용되지 않은 속성은 추가할 때 에러가 발생한다.

print('이름:', samira.name)
print('나이:', samira.age)

```

    이름: 사미라
    나이: 27
    

## 출처
- 05-1 클래스 - 점프 투 파이썬
https://wikidocs.net/28
- 파이썬 코딩 도장 : 34.2 속성 사용하기
https://dojang.io/mod/page/view.php?id=2373
