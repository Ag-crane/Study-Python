# SCS2013 Python Programming Midterm Exam (2022-Spring 2분반)

SCS2013 Python Programming 중간고사입니다. 

주어진 설명을 잘 읽고, 구체적인 지시사항이 있다면 그에 따라 구현하세요. 

코드를 완성한 후, **SCS2013_Mid_학번_이름.ipynb** 로 파일을 저장한 후 eclass의 과제제출을 통해 제출하세요. 

## P-1

string formatting을 사용하여 다음과 같은 결과를 얻을 수 있도록 코드를 작성하세요. 

**1-1**. `name, day, temperature, weather`의 정보를 사용해 아래와 같은 형태로 출력하세요. 
- `.format()`을 사용하여 포매팅합니다 - format() 함수의 입력값은 정해져 있습니다. 
- 주어진 변수 `name, day, temperature, weather`를 사용하세요. 값을 직접 출력하지 않습니다. 
- 문자열 내에는 작은 따옴표와 큰 따옴표가 포함되어 있습니다. 
- 첫 문장 이후 줄바꿈이 있습니다.
- 온도는 소수점 3자리까지 표현합니다. 

실행 결과: 
```
Hi "Peter"! Today is Thursday.
Today's weather is Sunny and the temperature is 26.900.
```


```python
# 1-1 
name = 'Peter'
day = 'Thursday'
temperature = 26.9
weather = 'Sunny'
'''
.format()을 사용하여 포매팅합니다 - format() 함수의 입력값은 정해져 있습니다.
주어진 변수 name, day, temperature, weather를 사용하세요. 값을 직접 출력하지 않습니다.
문자열 내에는 작은 따옴표와 큰 따옴표가 포함되어 있습니다.
첫 문장 이후 줄바꿈이 있습니다.
온도는 소수점 3자리까지 표현합니다.
'''

# 빈 칸을 채우세요: your code here
print('Hi "{B}"! Today is {D}.\nToday\'s weather is {C} and the temperature is {A:.3f}.  '.format(B=name, D=day, A=temperature, C=weather))
```

    Hi "Peter"! Today is Thursday.
    Today's weather is Sunny and the temperature is 26.900.  
    

**1-2**. `data`로 주어진 여러 회사들의 이름, 주식 개수, 가격에 관한 정보를 아래와 같은 형태로 출력하세요. 
- 포매팅 방법은 자유롭게 사용해도 됩니다: % operator, .format(), f-string 모두 가능.
- 다만 `data`를 사용해야 하며 값을 직접 출력하지 않습니다. 
- 반복문을 사용합니다. 
- 회사이름, 주식 개수, 가격은 모두 가운데 정렬된 14자리로 표현합니다. (회사 이름은 string, 주식 개수는 정수형이며, 가격은 소수점 2자리까지 표현합니다.) 

실행 결과: 
```
     AAPL            50           139.07    
     IBM             72           118.61    
     MSFT            13           225.95    
     GOOG            22          1901.05    
```

- (추가 선택사항) `data`를 출력하기 전에 `frame`에 주어진 정보 역시 가운데 정렬된 14자리로 표현하여 아래와 같이 만들어보세요. 

실행 결과:
```
   Company         Shares         Price     
     AAPL            50           139.07    
     IBM             72           118.61    
     MSFT            13           225.95    
     GOOG            22          1901.05    

```




```python
# 1-2
data = [('AAPL', 50, 139.07), ('IBM', 72, 118.61), ('MSFT', 13, 225.95), ('GOOG', 22, 1901.05)]
frame = ('Company', 'Shares', 'Price')

'''
반복문을 사용합니다.
회사이름, 주식 개수, 가격은 모두 가운데 정렬된 14자리로 표현합니다. (회사 이름은 string, 주식 개수는 정수형이며, 가격은 소수점 2자리까지 표현합니다.)
   Company         Shares         Price     
     AAPL            50           139.07    
     IBM             72           118.61    
     MSFT            13           225.95    
     GOOG            22          1901.05  
'''
# 필요한 코드를 작성하세요: your code here
for i in frame:
  print(f'{i:^14}',end="")
print()

for tup in data:
  print(f'{tup[0]:^14}{tup[1]:^14}{tup[2]:^14.2f}')


```

       Company        Shares        Price     
         AAPL           50          139.07    
         IBM            72          118.61    
         MSFT           13          225.95    
         GOOG           22         1901.05    
    

## P-2

문자열을 입력받아 다음의 두 가지를 구해 반환하는 함수 `get_Unique_Count`를 구현하세요. 
- 입력받은 문자열은 대소문자 구분 없이 중복을 체크합니다: a와 A는 같은 a로 취급
- 반환하는 항목은 두 개입니다
  - 첫번째: 중복된 문자를 제거한 문자열을 만들어 반환합니다. 
  - 두번째: 각 문자의 값과 그 문자가 몇 번 나타나는지 (횟수)를 key-value로 하는 딕셔너리를 만들어 반환합니다. 

실행 결과:
```
Original string:  Pythonprogramming
Unique string:  pythonrgami
Count dictionary:  {'p': 2, 'y': 1, 't': 1, 'h': 1, 'o': 2, 'n': 2, 'r': 2, 'g': 2, 'a': 1, 'm': 2, 'i': 1}
=====
Original string:  13a3bAa12cC
Unique string:  13ab2c
Count dictionary:  {'1': 2, '3': 2, 'a': 3, 'b': 1, '2': 1, 'c': 2}
```



```python
# get_Unique_Count 함수를 구현하세요: your code here
'''
 문자열을 입력받아 다음의 두 가지를 구해 반환하는 함수 get_Unique_Count를 구현하세요.

입력받은 문자열은 대소문자 구분 없이 중복을 체크합니다: a와 A는 같은 a로 취급
반환하는 항목은 두 개입니다
첫번째: 중복된 문자를 제거한 문자열을 만들어 반환합니다.
두번째: 각 문자의 값과 그 문자가 몇 번 나타나는지 (횟수)를 key-value로 하는 딕셔너리를 만들어 반환합니다.
 '''
def get_Unique_Count(str):
  newStr=""
  dct = {}
  for c in str.lower():
    if c not in newStr:
      newStr += c
      dct[c]=1
    else:
      dct[c]+=1
      
  return newStr, dct

```


```python
# 정의한 함수를 이용해 아래를 실행하여 결과를 확인하세요. 
str_1 = 'Pythonprogramming'
str_2 = '13a3bAa12cC'

uni_str_1, count_dict_1 = get_Unique_Count(str_1)
uni_str_2, count_dict_2 = get_Unique_Count(str_2)

print('Original string: ', str_1)
print('Unique string: ', uni_str_1)
print('Count dictionary: ', count_dict_1)
print('=====')
print('Original string: ', str_2)
print('Unique string: ', uni_str_2)
print('Count dictionary: ', count_dict_2)
```

    Original string:  Pythonprogramming
    Unique string:  pythonrgami
    Count dictionary:  {'p': 2, 'y': 1, 't': 1, 'h': 1, 'o': 2, 'n': 2, 'r': 2, 'g': 2, 'a': 1, 'm': 2, 'i': 1}
    =====
    Original string:  13a3bAa12cC
    Unique string:  13ab2c
    Count dictionary:  {'1': 2, '3': 2, 'a': 3, 'b': 1, '2': 1, 'c': 2}
    

## P-3

**3-1**. 하나의 정수를 입력받아 아래와 같은 패턴을 출력하는 함수 `print_pattern`을 반복문을 사용하여 구현하세요. 
- 입력받은 숫자부터 1까지 반복적으로 해당 숫자를 반복하여 출력합니다. 
- 반복 횟수는 숫자에 따라 다르며, 반복 사이에 공백이 있음에 유의하세요.

실행 결과: 
```
5 5 5 5 5 
4 4 4 4 
3 3 3 
2 2 
1 
```

**3-2**. 동일한 기능을 하는 함수 `print_pattern_rec`를 재귀함수로 구현하세요. 

실행 결과: 
```
5 5 5 5 5 
4 4 4 4 
3 3 3 
2 2 
1 
```


```python
# 3-1 print_pattern 함수를 구현하세요: your code here

def print_pattern(n):
  for i in range(n,0,-1):
    for j in range(i):
      print(i,end=" ")
    print()

```


```python
# 구현한 함수를 이용해 아래를 실행하여 결과를 확인하세요. 
num = 5
print_pattern(num)
```

    5 5 5 5 5 
    4 4 4 4 
    3 3 3 
    2 2 
    1 
    


```python
# print_pattern_rec 함수를 구현하세요: your code here

def print_pattern_rec(n):
  if n==1:
    print(1)
  else:
    for i in range(n):
      print(n,end=" ")
    print()
    print_pattern_rec(n-1)




```


```python
# 구현한 함수를 이용해 아래를 실행하여 결과를 확인하세요. 
num = 5
print_pattern_rec(num)
```

    5 5 5 5 5 
    4 4 4 4 
    3 3 3 
    2 2 
    1
    

## P-4

딕셔너리 `student_dict`가 주어질 때, 생년월일(`Birth`)의 '월'에 해당하는 값을 파악하여 계절을 판단하는 코드를 작성하고, 아래와 같은 결과를 출력하세요. 
- 키에 해당하는 값을 파악하여 `height`에 할당하세요 - 'cm'를 제외하고 소수점이 있는 형태로 받아옵니다.
- 딕셔너리 중 `Birth` key에 해당하는 value 값은 문자열('YYYY-MM-DD')의 형태로 주어집니다. 이 중에서 '월(MM)'에 해당하는 값을 파악하여 `b_month`에 할당하세요 - 문자열 슬라이싱 혹은 내장함수를 사용할 수 있습니다. 
- `b_month` 값에 따라 계절을 판단하여 `season`에 할당하세요 - 조건문을 사용합니다. 
  - Spring (3월-5월), Summer (6월-8월), Fall (9월-11월), 나머지는 Winter로 판단합니다. 
- 딕셔너리의 다른 정보들에 해당하는 값들과 `b_month`, `season`을 활용하여 다음과 같은 문자열 형태로 출력하세요. 
  - 키는 소수점 2자리로 표현합니다.


실행 결과:
```
Emma은 EE 소속이며, 태어난 계절은 Fall, 키는 163.50 입니다.
```


```python
student_dict = {'Name': 'Emma', 'Major': 'EE', 'Info': {'Age': 20, 'Birth': '2003-09-14', 'Height': '163.5cm'}}

# height를 구하는 코드를 작성하세요: your code here
height = float(student_dict['Info']['Height'][:-2])

# b_month를 구하는 코드를 작성하세요: your code here
b_month = student_dict['Info']['Birth'].split('-')[1]

# season을 구하는 코드를 작성하세요: your code here
m = int(b_month)
if 3<=m<=5:
  season='spring'
elif 6<=m<=8:
  season='summer'
elif 9<=m<=11:
  season='fall'
else:
  season='winter'

# 포매팅 출력하는 코드를 작성하세요.: your code here
print(f'''{ student_dict['Name'] }은 { student_dict['Major'] } 소속이며, 태어난 계절은 {season}, 키는 {height:.2f}입니다.''')

```

    Emma은 EE 소속이며, 태어난 계절은 fall, 키는 163.50입니다.
    

## P-5

사용자로부터 세 개의 정수를 입력 받아 (`a,b,c`라고 칭함) `a`가 `b`의 배수인지 확인하여 True/False로 답하는 코드와 `a`가 `c`-자릿수인지 확인하여 True/False로 답하는 코드를 작성하세요. 
- 연산자를 사용해 두가지를 확인하고 출력해야 합니다: 
- 첫번째: `a`가 `b`의 배수인지 T/F
- 두번째: `a`가 `c`-자릿수인지 T/F

실행 결과:
```
첫번째 숫자를 입력하세요 (0보다 큰 정수): 513
두번째 숫자를 입력하세요 (0보다 큰 정수): 7
세번째 숫자를 입력하세요 (0보다 큰 정수): 3
513은 7의 배수인가요? False
513은 3자리 숫자인가요? True
```


```python
# 필요한 코드를 작성하세요: your code here 

a = int(input("첫번째 숫자를 입력하세요(0보다 큰 정수): "))
b = int(input("두번째 숫자를 입력하세요(0보다 큰 정수): "))
c = int(input("세번째 숫자를 입력하세요(0보다 큰 정수): "))

print(f'{a}은 {b}의 배수인가요? {a%b==0}')
print(f'{a}은 {c}자리 숫자인가요? {10**(c-1)<=a<10**c}')

```

    첫번째 숫자를 입력하세요(0보다 큰 정수): 422
    두번째 숫자를 입력하세요(0보다 큰 정수): 2
    세번째 숫자를 입력하세요(0보다 큰 정수): 2
    422은 2의 배수인가요? True
    422은 2자리 숫자인가요? False
    

## P-6

정수의 시작값 `start`, 끝값 `end`, 또 다른 숫자 `num`을 입력 받아 시작값과 끝값 사이에 존재하는 `num`의 배수들의 합을 반환하는 함수 `get_sum`을 구현하세요. 
- 시작값, 끝값, 숫자 는 순서대로 argument로 주어집니다. 
- 만일 `num`에 해당하는 값이 인수로 주어지지 않으면 시작값과 끝값 사이에 존재하는 모든 "5의 배수"들의 합을 반환합니다. 
- 시작값과 끝값을 모두 포함하는 범위를 고려합니다. 

실행 결과:
```
60
50
```


```python
# get_sum 함수를 구현하세요: your code here 
def get_sum(start,end,num=5):
  sum=0
  for i in range(start,end+1):
    if i%num==0:
      sum+=i
  return sum


```


```python
# 구현한 함수를 이용해 아래를 실행하여 결과를 확인하세요. 
print(get_sum(5, 20, 3)) 
print(get_sum(5, 20))
```

    60
    50
    

## P-7 (추가 문제)

**P-6**와 비슷하게 시작값 `start` 과 끝값 `end` 사이에 존재하는 `num`의 배수들의 합을 반환하는 함수 `get_sum_ext`를 구현하세요. 이 함수는 `get_sum`과는 다르게 다양한 형태의, 임의의 개수의 입력에도 동작해야 합니다. 
- 매개변수가 한개만 들어오는 경우: 끝값 `end`에 해당합니다. 이 경우 시작값 `start`는 1로 두고, `num`은 5로 가정합니다. 
- 매개변수가 두개만 들어오는 경우: 첫번째 들어오는 값이 시작값 `start`, 두번째로 들어오는 값이 끝값 `end`에 해당합니다. 이 경우 `num`은 5로 가정합니다. 
- 매개변수가 세개 들어오는 경우: 첫번째 들어오는 값이 시작값 `start`, 두번째로 들어오는 값이 끝값 `end`, 세번째로 들어오는 값이 `num`에 해당합니다. 
- 이 외의 경우는 모두 'Invalid arguments'를 출력하고 0을 반환합니다. 
- 앞에서 구현한 `get_sum`을 사용할 수 있습니다. 


실행 결과:
```
5
50
60
Invalid arguments
0
```


```python
# get_sum_ext 함수를 구현하세요: your code here

def get_sum_ext(*args):

  if len(args)==1:
    start,end,num = 1, args[0], 5
  elif len(args)==2:
    start,end,num = args[0],args[1],5
  elif len(args)==3:
    start,end,num = args[0],args[1],args[2]
  else :
    print('Invlid arguments')
    return 0
  
  return get_sum(start,end,num)
```


```python
# 구현한 함수를 이용해 아래를 실행하여 결과를 확인하세요. 
print(get_sum_ext(5))
print(get_sum_ext(5, 20))
print(get_sum_ext(5, 20, 3))
print(get_sum_ext(5, 20, 3, 4))
```

    5
    50
    60
    Invlid arguments
    0
    

## P-8

다양한 단어들로 이루어진 리스트 `words`가 주어질 때, lambda 함수와 map, filter를 사용하여 다음과 같은 두개의 리스트를 얻을 수 있도록 코드를 구현하세요. 
- `lower_words` 리스트는 `words` 리스트에 있는 단어들을 모두 소문자로 바꾼 리스트입니다.
- `symmetric_words` 리스트는 `lower_words` 리스트에 있는 단어들 중 좌우 대칭인 단어들만 골라 만든 리스트입니다. 
  - 혹은 `words` 리스트에서 대/소문자 구분 없이 좌우 대칭을 확인하여도 됩니다.
  - 좌우 대칭인 단어는 앞으로 읽어도, 뒤로 읽어도 (역순으로) 동일안 단어를 의미합니다.
- lambda 함수와 `map`, `filter` 함수를 사용합니다.

실행 결과:
```
['noon', 'banana', 'melon', 'madam', 'refer', 'mango']
['noon', 'madam', 'refer']
```


```python
words = ['Noon', 'baNAna', 'meLon', 'madam', 'Refer', 'mango']

# lower_words를 구하는 코드를 작성하세요: your code here 
lower_words = list(map(lambda x:x.lower(),words))


# symmetric_words를 구하는 코드를 작성하세요: your code here 
symmetric_words=list(filter(lambda x:x[0:]==x[-1::-1], lower_words))


```


```python
# 아래를 실행하여 결과를 확인하세요. 
print(lower_words)
print(symmetric_words)
```

    ['noon', 'banana', 'melon', 'madam', 'refer', 'mango']
    ['noon', 'madam', 'refer']
    

## P-9

임의의 개수의 문자열들을 입력인수로 받아, 사용자로부터 입력받은 문자가 각 문자열에 어느 위치(인덱스)에 존재하는 지 구하고, 각 문자열과 그 위치를 출력하는 함수 `print_position`를 구현하세요. 
- 임의의 개수의 문자열들을 입력값으로 받아옵니다. 
- 위치를 확인하고자 하는 문자(혹은 문자열)를 사용자로부터 입력받습니다. 
- 각 문자열에 해당 문자가 어느 위치에 존재하는 지 구하고 각 문자열과 그 위치를 아래와 같은 형태로 출력합니다. 
- 문자가 처음으로 나타난 위치를 구하고, 만일 해당 문자가 존재하지 않는 경우에는 -1으로 표현하도록 합니다.

실행 결과:
```
위치를 확인하고 싶은 문자를 입력하세요: m
Dobby is free: position of m is -1
Fear of a name only increaes fear of the thing itself: position of m is 12
Python Proramming Midterm Exam: position of m is 12
```


```python
# print_position 함수를 구현하세요: your code here 

def print_position(*args):

  c = input("위치를 확인하고 싶은 문자를 입력하세요: ")
  
  for str in args:
    print(f'{str}: position of {c} is {str.find(c)}')


```


```python
# 구현한 함수를 이용해 아래를 실행하여 결과를 확인하세요. 
print_position('Dobby is free', 'Fear of a name only increaes fear of the thing itself', 'Python Proramming Midterm Exam')
```

    위치를 확인하고 싶은 문자를 입력하세요: m
    Dobby is free: position of m is -1
    Fear of a name only increaes fear of the thing itself: position of m is 12
    Python Proramming Midterm Exam: position of m is 12
    

## P-10

정수를 연속으로 사용자로부터 입력 받아 홀수와 짝수를 구별하여 두 개의 리스트를 만들고 오름차순으로 정렬해 반환하는 함수 `get_odd_even` 함수를 구현하세요. 사용자로부터 0을 입력받으면 함수가 종료됩니다. (0은 리스트에 포함시키지 않습니다)
```
숫자를 입력하세요 (0을 입력하면 종료): -5
숫자를 입력하세요 (0을 입력하면 종료): 2022
숫자를 입력하세요 (0을 입력하면 종료): -25
숫자를 입력하세요 (0을 입력하면 종료): 4
숫자를 입력하세요 (0을 입력하면 종료): 62
숫자를 입력하세요 (0을 입력하면 종료): 0
Odd inputs:  [-25, -5]
Even inputs:  [4, 62, 2022]
```


```python
# get_odd_even 함수를 구현하세요: your code here

def get_odd_even():
  odd = []
  even = []

  while True:
    n = int(input('숫자를 입력하세요 (0을입력하면 종료): '))
    if n==0:
      break
    else:
      if n%2==0:
        even.append(n)
      else:
        odd.append(n)
  
  odd.sort()
  even.sort()
  return odd, even

```


```python
# 구현한 함수를 이용해 아래를 실행하여 결과를 확인하세요. 
odd, even = get_odd_even()
print('Odd inputs: ', odd)
print('Even inputs: ', even)
```

    숫자를 입력하세요 (0을입력하면 종료): 2022
    숫자를 입력하세요 (0을입력하면 종료): -5
    숫자를 입력하세요 (0을입력하면 종료): -25
    숫자를 입력하세요 (0을입력하면 종료): 64
    숫자를 입력하세요 (0을입력하면 종료): 0
    Odd inputs:  [-25, -5]
    Even inputs:  [64, 2022]
    
