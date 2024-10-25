# SCS2013 Python Programming Midterm Exam (2022-Fall 1분반)

SCS2013 Python Programming 중간고사입니다. 

주어진 설명을 잘 읽고, 구체적인 지시사항이 있다면 그에 따라 구현하세요. 

코드를 완성한 후, **SCS2013_a_midterm_학번_이름.ipynb** 로 파일을 저장한 후 eclass의 과제제출을 통해 제출하세요. 

## P-1 (15pts)

string formatting을 사용하여 `data`로 주어진 여러 물품들의 물품 명, 물품 개수, 가격, 회사 명에 관한 정보를 아래와 같은 형태로 출력하세요. 
- 포매팅 방법은 자유롭게 사용해도 됩니다: % operator, .format(), f-string 모두 가능. 
- 값을 직접 출력하는 것이 아니라, 반복문을 사용하여 `data`에 접근해야 합니다. 
- 물품 명과 회사 명은 **오른쪽 정렬된 10자리**로 표현합니다. (물품 명과 회사 명은 string으로 표현)
- 물품 개수와 가격은 **가운데 정렬된 10자리**로 표현합니다. (물품 개수는 integer, 가격은 소수점 3자리의 float로 표현)

실행 결과: 
```
  Computer    10     203.920        Dell
  Sneakers    13      13.500        Nike
      Jean    6       25.000         ABC
       Pen   123      1.253       SCS123
```

- (추가 사항: + 3pts) `frame`에 주어진 정보들('Product', 'Counts', 'Price', 'Company')도 포매팅을 사용하여 아래와 같이 정렬된 형태로 표현해보세요. 'Product'와 'Company'는 오른쪽 정렬된 10자리이며, 'Counts'와 'Price'는 가운데 정렬 10자리입니다.

실행 결과: 
```
***Product!!Counts!!--Price---+++Company
  Computer    10     203.920        Dell
  Sneakers    13      13.500        Nike
      Jean    6       25.000         ABC
       Pen   123      1.253       SCS123
```



```python
# P-1
frame = ('Product', 'Counts', 'Price', 'Company')
sales = [('Computer', 10, 203.92, 'Dell'), 
         ('Sneakers', 13, 13.5, 'Nike'), 
         ('Jean', 6, 25, 'ABC'), 
         ('Pen', 123, 1.2533, 'SCS123')]

# your code here:
# # option: printing values in frame
# print(f'{frame[0]:*>10}{frame[1]:!^10}{frame[2]:-^10}{frame[3]:+>10}')

# # printing values in sales
# for val in sales:
#   print(f'{val[0]:>10}{val[1]:^10}{val[2]:^10.3f}{val[3]:>10}')

# 교수님 풀이
for product, count, price, company in sales:    # 각 튜플이 각 변수에 저장됨
  print(f'{product:>10s}{count:^10d}{price:^10.3f}{company:>10s}')   # 변수 타입 지정



```

      Computer    10     203.920        Dell
      Sneakers    13      13.500        Nike
          Jean    6       25.000         ABC
           Pen   123      1.253       SCS123
    

## P-2 (15pts)

**임의의 개수**의 문장을 입력받아 다음과 같은 작업을 수행하는 함수 `check_sentences` 함수를 구현하세요. 
- 임의의 개수의 (영어) 문장 (string) 을 입력받습니다. 
- 각 문장에 대해 다음을 확인하고 수행합니다:
  - 문장이 시작 문자만 대문자로 시작할 수 있도록 수정합니다.
  - 문장이 온점 (.) 물음표 (?) 느낌표 (!) 로 끝나는 지 확인하고, 그렇지 않은 경우 항상 온점 (.) 으로 끝날 수 있도록 수정합니다. 
- 수정된 각 문장들을 원소로 하는 **리스트**를 만들어 반환합니다.

실행 결과:
```
sentence_lst1 = check_sentences('hello everyone', 'Hello, Everyone!', 'hello World.', 'how aRe You?')
print(sentence_lst1)
>>>
['Hello everyone.', 'Hello, everyone!', 'Hello world.', 'How are you?']
```
```
sentence_lst2 = check_sentences('I\'m good, Thank you!', 'have a Nice day')
print(sentence_lst2)
>>>
["I'm good, thank you!", 'Have a nice day.']
```


```python
# P-2
# your code here:
def check_sentences(*strs):
  lst = ['.','?','!']
  return_lst = []

  for st in strs:
    new_str = st.capitalize()
    if new_str[-1] not in lst:    
      new_str+='.'
    return_lst.append(new_str)
  return return_lst

# lst를 굳이 만들어줄 필요 없이 not in ['.','?','!'] 이렇게 쓰면 된다
# 한번만 쓸거니까!

```


```python
# check your code:
sentence_lst1 = check_sentences('hello everyone', 'Hello, Everyone!', 'hello World.', 'how aRe You?')
print(sentence_lst1)

sentence_lst2 = check_sentences('I\'m good, Thank you!', 'have a Nice day')
print(sentence_lst2)
```

    ['Hello everyone.', 'Hello, everyone!', 'Hello world.', 'How are you?']
    ["I'm good, thank you!", 'Have a nice day.']
    

## P-3 (10pts)

사용자로부터 하나의 정수를 입력 받아 **3의 거듭제곱**인지 확인하는 코드를 구현하세요. 
- 사용자로부터 하나의 숫자를 입력받고, 그 숫자가 3의 거듭제곱인지 아닌지 확인하여 3의 거듭제곱인 경우 'Power of Three!'를 출력하세요.
- 반복문을 써도 되고, 다른 방법을 사용해도 됩니다. (배운 내용에 한하여 사용할 수 있으며, 'math'는 사용하면 안됩니다.)
- 만일 사용자가 정수를 입력하지 않았거나, 양수를 입력하지 않은 경우 'Wrong Input!' 문장을 출력하세요.

실행 결과:
```
Enter a positive integer: >>> 27
Power of Three!
```
```
Enter a positive integer: >>> 25
```
```
Enter a positive integer: >>> -14
Wrong Input!
```
```
Enter a positive integer: >>> 2.5
Wrong Input!
```
```
Enter a positive integer: >>> abc
Wrong Input!
```


```python
# P-3
# your code here:

n = int(input("Enter a positive integer: >>> "))
if type(n)!=int or n<=0:
  print('Wrong Input')

while n%3==0 :
  n=n/3

if n==1:
  print('Power of Three!')

# abc 입력시 에러나옴... 예외처리 안함

# try:
#   n = int(input("Enter a positive integer: >>> "))
#   if n<=0:
#     raise      # 에러를 강제로 발생시킴 => except로 넘어감
# except:
#   print('Wrong Input!')

# try - except 없이 raise 사용하는 경우
# n = int(input("Enter a positive integer: >>> "))    
# if n<=0:
#   raise Exception('negative integer')

```

    Enter a positive integer: >>> abc
    Wrong input
    

## P-4 (15pts)

다양한 단어와 숫자들로 이루어진 리스트 `lst`가 주어질 때, `lambda` 함수와 `map()` 혹은 `filter()`를 사용하여 다음의 두 작업을 구현하세요. 

- **(a)** `symmetric_lst`는 `lst`의 원소들 중 **좌우 대칭**인 원소들만 골라 만들어진 리스트입니다. 
  * 좌우 대칭인 단어는 정 방향으로 읽어도 역 방향으로 읽어도 동일한 단어를 의미합니다. 
  * 이를 확인하기 위해서는 원소들을 string으로 바꾸어 체크하는 것이 좋습니다. 

- **(b)** `short_lst`는 `lst`의 원소들 중 길이가 4 이하인 원소들만 골라 만들어진 리스트입니다.
  * hint: 숫자의 경우에도 string으로 바꾸면 길이를 쉽게 체크할 수 있습니다.

실행 결과:
```
print(symmetric_lst)
>>> 
['Noon', 'madam', 'Refer', 121, 12321]
```
```
print(short_lst)
>>> 
['Noon', 121, 123]
```


```python
# P-4
lst = ['Noon', 'baNAna', 'meLon', 'madam', 'Refer', 'mango', 121, 123, 12321]

# (a) your code here:
symmetric_lst = list( filter( lambda x:str(x).lower()[0:]==str(x).lower()[-1::-1], lst) )

```


```python
# P-4
lst = ['Noon', 'baNAna', 'meLon', 'madam', 'Refer', 'mango', 121, 123, 12321]

# (b) your code here: 
short_lst = list( filter( lambda x:len(str(x))<=4, lst ) )

```


```python
# check your code:
print(symmetric_lst)
print(short_lst)
```

    ['Noon', 'madam', 'Refer', 121, 12321]
    ['Noon', 121, 123]
    

## P-5 (20pts)

사용자로부터 이름과 나이를 입력받아 각각 리스트에 저장하여 반환하는 함수 `get_info` 를 구현하세요. 
- 이 함수는 함수 호출 시 입력값이 필요하지 않습니다. 
- 함수가 실행되는 동안 사용자로부터 이름을 입력받습니다. 
- 만일 사용자가 'quit' 혹은 'Q'를 입력하면 함수를 종료합니다. 
- 적절한 이름이 입력된 경우 사용자로부터 나이를 입력받으며, 나이가 양수인 정수로 입력되지 않으면 'Wrong information!'을 출력합니다.
- 'quit' 혹은 'Q'가 입력되기 전까지 **반복하여** 위와 같이 이름과 나이를 입력받습니다.
- 입력받은 이름과 나이를 리스트로 만들어 반환합니다. 

실행 결과 (예시):
```
name_lst, age_lst = get_info()
>>> 
Enter a Name (enter quit or Q to exit): >>> Alice
Enter the age of Alice: >>> 10
Enter a Name (enter quit or Q to exit): >>> Bob
Enter the age of Bob: >>> 32
Enter a Name (enter quit or Q to exit): >>> Peter
Enter the age of Peter: >>> -13
Wrong information!
Enter a Name (enter quit or Q to exit): >>> John
Enter the age of John: >>> 28
Enter a Name (enter quit or Q to exit): >>> Julia
Enter the age of Julia: >>> 53
Enter a Name (enter quit or Q to exit): >>> Q
```
```
print(name_lst, age_lst)
>>>
['Alice', 'Bob', 'John', 'Julia'] [10, 32, 28, 53]
```


```python
def get_info():
  while True:
    name = input('Enter a Name (enter quit or Q to exit): >>> ')
    if name=='quit' or 'Q':
      break
    age = input('Enter the age of John: >>> ')
    if age<=0:
      print('Wrong information!')
```


```python
# P-5
'''
사용자로부터 이름과 나이를 입력받아 각각 리스트에 저장하여 반환하는 함수 get_info 를 구현하세요.
이 함수는 함수 호출 시 입력값이 필요하지 않습니다.
함수가 실행되는 동안 사용자로부터 이름을 입력받습니다.
만일 사용자가 'quit' 혹은 'Q'를 입력하면 함수를 종료합니다.
적절한 이름이 입력된 경우 사용자로부터 나이를 입력받으며, 나이가 양수인 정수로 입력되지 않으면 'Wrong information!'을 출력합니다.
'quit' 혹은 'Q'가 입력되기 전까지 반복하여 위와 같이 이름과 나이를 입력받습니다.
입력받은 이름과 나이를 리스트로 만들어 반환합니다.
'''
# your code here:
def get_info():
  name_lst = []
  age_lst = []
  while True:
    name = input("Enter a Name (enter quit or Q to exit): >>> ")
    if name=='quit' or name=='Q':      # name in ['quit','Q']
      break
    else:
      age = int(input(f"Enter the age of {name}: >>> "))
      if type(age)!=int or age<=0:
        print('Wrong information!')
      else: 
        name_lst.append(name)
        age_lst.append(age)
  
  return name_lst, age_lst


```


```python
# check your code:
name_lst, age_lst = get_info()
print(name_lst, age_lst)
```

    Enter a Name (enter quit or Q to exit): >>> quit
    [] []
    

## P-6 (15pts)

* **(a)** 하나의 정수를 입력받아 아래와 같은 삼각형 패턴을 출력하는 함수 `print_pattern`을 **반복문**을 사용하여 구현하세요.
  * 각 줄의 패턴은 가운데 정렬된 20자리로 출력하여야 삼각형 패턴 출력이 가능합니다. (혹은 다른 방법을 사용해도 됩니다.)

  실행 결과:
  ```
  print_pattern(5)
  >>>
         +          
        +++         
       +++++        
      +++++++       
     +++++++++        
  ```

* **(b)** 동일한 기능을 하는 함수 `print_pattern_recur`를 **재귀함수**로 구현하세요.
  
  실행 결과:
  ```
  print_pattern_recur(5)
  >>>
         +          
        +++         
       +++++        
      +++++++       
     +++++++++        
  ```  

* **(c)** 하나의 정수를 입력받아 아래와 같은 패턴을 출력하는 함수 `print_shape`을 구현하세요. 
  * 반복문 혹은 재귀함수 중 아무거나 사용하여도 됩니다. 
  * 반복문 버전과 재귀함수버전을 모두 구현한 경우 추가점수 (+5pts)
  
  실행 결과:
  ```
  print_shape(5)
  >>>
  +++++
  ++++
  +++
  ++
  +
  +
  ++
  +++
  ++++
  +++++  
  ```



```python
# P-6
# (a) your code here:
def print_pattern(n):
  for i in range(1,n+1):
    s=(2*i-1)*'+'
    print(f'{s:^20}')

```


```python
# P-6
# (a) check your code:
print_pattern(5)
```

             +          
            +++         
           +++++        
          +++++++       
         +++++++++      
    


```python
# P-6
# (b) your code here:
def print_pattern_recur(n):
  if n==1:
    s='+'
    print(f"{s:^20}")
  elif n>1:
    print_pattern_recur(n-1)
    s='+'*(2*n-1)
    print(f"{s:^20}")

# # 다른 풀이
# def print_pattern_recur(n):
#   if n>0:
#     print_pattern_recur(n-1)
#     s='+'*(2*n-1)
#     print(f"{s:^20}")

```


```python
# P-6
# (b) check your code:
print_pattern_recur(5)
```

             +          
            +++         
           +++++        
          +++++++       
         +++++++++      
    


```python
# P-6
# (c) your code here:


# def print_shape(n):
#   for i in range(n,0,-1):
#     print("+"*i)
#   for i in range(1,n+1):
#     print("+"*i)

# 재귀함수 이용 *못풀었음!!!
# Tip : 만들려고 하는 모양(n=5)이 이전의 모양(n=4)에서 뭐가 추가된 형태인지?
# 재귀함수 앞, 뒤에 추가
def print_shape(n):

  if n>0:                 # 초기조건 if n==0: return 이거보다 간편한 방법
    print(n*'+')
    print_shape(n-1)
    print(n*'+')
  

  


  

  

```


```python
# P-6
# (c) check your code:
print_shape(5)
```

    +++++
    ++++
    +++
    ++
    +
    +
    ++
    +++
    ++++
    +++++
    

## P-7 (10pts)

주어진 리스트 `lst`의 원소값들 중 **세번째로 큰** 원소값을 찾는 코드를 구현하세요. 
- 리스트 `lst`에는 중복된 값이 포함될 수 있음에 유의하세요. 
- 항상 서로 다른 세 개 이상의 값이 `lst`에 있다고 가정합니다.
- 중복된 값이 있어도 세번째로 큰 원소값을 찾을 수 있어야 합니다. 

실행 결과:
```
lst = [5,7,15,21,21,5,4,7]
>>>
Third largest value is: 7
```



```python
# P-7
lst = [5,7,15,21,21,5,4,7]

# your code here:

# new_lst=[]
# maxNum=0
# while len(new_lst)<3:
#   maxNum = max(lst)
#   if maxNum not in new_lst:
#     new_lst.append(maxNum)
#   lst.remove(maxNum)

# print(f'Third largest value is: {new_lst[2]}')


# 교수님풀이 ;;;

new_lst = list(set(lst))   # 집합으로 만들어 중복제거 후 다시 리스트로

new_lst.remove(max(new_lst))
new_lst.remove(max(new_lst))
print(f'Third largest value is: {max(new_lst)}')
```

    Third largest value is: 7
    
