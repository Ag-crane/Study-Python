# SCS2013 Python Programming Homework 2 (100pts)

About List/Tuple/Dictionaries, Conditional (If-else), Loop (For, While) Statements

## HW 2-1. List, if, loop statements (30pts)

Instruction: 

1. **(10pt)** 아래의 `random.randint(0,50)`은 $0$부터 $50$ 사이의 임의의 정수를 생성하는 코드입니다. `for`문을 사용하여 총 100개의 랜덤한 정수를 생성하고 이를 원소로 하는 리스트 `random_lst`를 생성하세요.
  * for 문, `random.randint(0,50)`과 list 관련 함수를 사용합니다.
  
    **(EN)** `random.randint(0,50)` below is a code that generates random integer of value between 0 and 50. Use the `for` statement to generate a list `random_lst` with $100$ random integers.
    * please use `for` statement, `random.randint(0,50)`and list-related functions.
   
2. **(10pt)** List의 정렬 함수 `.sort()`를 사용하지 않고, **반복문을 사용하여** `random_lst`를 내림차순으로 정렬하는 코드를 작성하세요. 
  * 내림차순 정렬: 큰 수부터 작은 수로 배치하는 것.
  * 반복문을 사용합니다.

    **(EN)** Without using the list sorting function .sort(), write a code that sorts random_lst in `descending order` with loop statements.
    * Descending order: Sort from large to small numbers.
    * Use loop statements.
3. **(10pt)** 반복문과 조건문을 사용하여, 정렬된 `random_lst` 리스트에서 $7$의 배수들만 모아 출력하세요. 
  * 2에서 사용하지 않은 반복문 문법을 사용합니다. (2에서 `for`를 사용했다면 `while`을 사용해 3을 구현하세요)
  * $0$은 $7$의 배수에서 제외합니다.

    **(EN)** Print `multiples of 7` from the sorted `random_lst` list using loop and conditional statements. 
    * Do not use the loop statement you've already used in 2. (If you used `for` in 2, use `while` to implement 3)

    * $0$ is excluded from the multiple of $7$.
  

**실행 결과** | Result:
```
# 1
print(random_lst)
>>> [46, 16, 3, 36, 9, 6, 22, 24, 45, 37, 15, 37, 20, 0, 3, 15, 46, 10, 21, 21, 1, 7, 30, 26, 27, 42, 45, 41, 29, 25, 33, 31, 8, 3, 46, 42, 18, 21, 21, 39, 47, 31, 0, 48, 0, 27, 43, 49, 23, 38, 1, 1, 17, 18, 29, 33, 14, 47, 49, 34, 19, 13, 15, 49, 50, 45, 0, 45, 4, 24, 34, 14, 39, 23, 20, 4, 25, 5, 17, 6, 20, 12, 40, 33, 1, 11, 9, 1, 13, 25, 48, 1, 3, 40, 26, 39, 21, 38, 30, 21]

# 2 
print('A list after sorting in descending order: ', random_lst)
>>> A list after sorting in descending order:  [50, 49, 49, 49, 48, 48, 47, 47, 46, 46, 46, 45, 45, 45, 45, 43, 42, 42, 41, 40, 40, 39, 39, 39, 38, 38, 37, 37, 36, 34, 34, 33, 33, 33, 31, 31, 30, 30, 29, 29, 27, 27, 26, 26, 25, 25, 25, 24, 24, 23, 23, 22, 21, 21, 21, 21, 21, 21, 20, 20, 20, 19, 18, 18, 17, 17, 16, 15, 15, 15, 14, 14, 13, 13, 12, 11, 10, 9, 9, 8, 7, 6, 6, 5, 4, 4, 3, 3, 3, 3, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0]

# 3
Numbers that are multiple of 7 in the list:
49	
49	
49	
42	
42	
21	
21	
21	
21	
21	
21	
14	
14	
7		
```


```python
import random 

test_val = random.randint(0,50)
print('Random generated number: ', test_val)
```

    Random generated number:  21
    


```python
import random

# 1
random_lst = []

######### your code here #########
for i in range(100):
  random_lst.append(random.randint(0,50))

print(random_lst)
```

    [21, 36, 41, 0, 39, 19, 7, 28, 27, 10, 16, 41, 47, 23, 24, 24, 19, 35, 50, 3, 2, 5, 42, 20, 11, 49, 15, 38, 36, 7, 35, 46, 5, 23, 28, 37, 7, 8, 45, 25, 18, 29, 27, 1, 1, 1, 31, 29, 43, 14, 24, 18, 50, 11, 11, 27, 42, 3, 42, 48, 1, 45, 36, 18, 32, 21, 12, 30, 7, 23, 43, 0, 8, 24, 23, 13, 22, 49, 50, 37, 45, 36, 14, 21, 18, 27, 19, 31, 35, 49, 23, 21, 47, 19, 13, 24, 39, 37, 21, 47]
    


```python
# 2
######### your code here #########

for i in range(100) :
  sublst = random_lst[i:]
  x = sublst.index(max(sublst))
  temp = random_lst[i]
  random_lst[i] = max(sublst)
  random_lst[x+i] = temp
  

print('A list after sorting in descending order: ', random_lst)
```

    A list after sorting in descending order:  [50, 50, 50, 49, 49, 49, 48, 47, 47, 47, 46, 45, 45, 45, 43, 43, 42, 42, 42, 41, 41, 39, 39, 38, 37, 37, 37, 36, 36, 36, 36, 35, 35, 35, 32, 31, 31, 30, 29, 29, 28, 28, 27, 27, 27, 27, 25, 24, 24, 24, 24, 24, 23, 23, 23, 23, 23, 22, 21, 21, 21, 21, 21, 20, 19, 19, 19, 19, 18, 18, 18, 18, 16, 15, 14, 14, 13, 13, 12, 11, 11, 11, 10, 8, 8, 7, 7, 7, 7, 5, 5, 3, 3, 2, 1, 1, 1, 1, 0, 0]
    


```python
# 3
print('Numbers that are multiple of 7 in the list:')

######### your code here #########
lst=[]
i=0
while True:
  if (random_lst[i] % 7 == 0) and (random_lst[i]!=0):
    print(random_lst[i],end=" ")
  i+=1
  if i==100:
    break
  


```

    Numbers that are multiple of 7 in the list:
    49 49 49 42 42 42 35 35 35 28 28 21 21 21 21 21 14 14 7 7 7 7 


```python
import random

# 1
random_lst = []

######### your code here #########
# solution
for i in range(100):
  random_lst.append(random.randint(0,50))

print(random_lst)
```

    [46, 16, 3, 36, 9, 6, 22, 24, 45, 37, 15, 37, 20, 0, 3, 15, 46, 10, 21, 21, 1, 7, 30, 26, 27, 42, 45, 41, 29, 25, 33, 31, 8, 3, 46, 42, 18, 21, 21, 39, 47, 31, 0, 48, 0, 27, 43, 49, 23, 38, 1, 1, 17, 18, 29, 33, 14, 47, 49, 34, 19, 13, 15, 49, 50, 45, 0, 45, 4, 24, 34, 14, 39, 23, 20, 4, 25, 5, 17, 6, 20, 12, 40, 33, 1, 11, 9, 1, 13, 25, 48, 1, 3, 40, 26, 39, 21, 38, 30, 21]
    


```python
# 2
# solution
for i in range(99):
  for j in range(i+1, 100):
    if random_lst[i] < random_lst[j]:
      temp_val = random_lst[i]
      random_lst[i] = random_lst[j]
      random_lst[j] = temp_val

print('A list after sorting in descending order: ', random_lst)
```

    A list after sorting in descending order:  [50, 49, 49, 49, 48, 48, 47, 47, 46, 46, 46, 45, 45, 45, 45, 43, 42, 42, 41, 40, 40, 39, 39, 39, 38, 38, 37, 37, 36, 34, 34, 33, 33, 33, 31, 31, 30, 30, 29, 29, 27, 27, 26, 26, 25, 25, 25, 24, 24, 23, 23, 22, 21, 21, 21, 21, 21, 21, 20, 20, 20, 19, 18, 18, 17, 17, 16, 15, 15, 15, 14, 14, 13, 13, 12, 11, 10, 9, 9, 8, 7, 6, 6, 5, 4, 4, 3, 3, 3, 3, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0]
    


```python
# 3
print('Numbers that are multiple of 7 in the list:')

######### your code here #########
# solution
i=0
while i < len(random_lst):
  if random_lst[i] % 7 == 0 and random_lst[i] > 0:
    print(f'{random_lst[i]}\t')

  i += 1
```

    Numbers that are multiple of 7 in the list:
    49	
    49	
    49	
    42	
    42	
    21	
    21	
    21	
    21	
    21	
    21	
    14	
    14	
    7	
    

## HW 2-2. Vending Machine (자판기) (45pts)

Instruction:


1. **(10pt)** 자판기에 있는 음료에 관한 딕셔너리 `dict_drink`를 생성하세요:
* 음료의 종류를 key로 가집니다. 
* 해당 음료의 남은 개수와 하나당 가격을 리스트로 만들어 value로 가집니다.
* `orange juice`는 총 5개 남아있고 각 1300원입니다.
* `coke`는 총 0개 남아있고 각 800원입니다.

    **(EN)** Make a dictionary `dict_drink` that stores the information of different drinks in a vending machine:
    * Each type of drink is a key. 
    * The number of the drink left in the vending machine and the price of the drink is the value.
    * `orange juice` has 5 left and costs 1300won.
    * `coke` has 0 left and costs 800won.
  
**실행 결과** | Result:
  ```
  print(dict_drink)
  >>> {'orange juice': [5, 1300], 'coke': [0, 800]}
  ```

    


```python
# 1
######### your code here #########

dict_drink = {'orange juice': [5, 1300], 'coke': [0, 800]}

print(dict_drink)
```

    {'orange juice': [5, 1300], 'coke': [0, 800]}
    

2. **(15pt)** `for`문을 사용하여 `dict_drink`의 내용을 다음과 같이 출력하세요: 

    **(EN)** Use `for` loop to print the items in `dict_drink`: 
  ```
  orange juice: 1300 won, 5 left.
  coke: 800 won, 0 left.
  ```




```python
# 2
######### your code here #########
for key in dict_drink:
  print(f'{key}: {dict_drink[key][1]} won. {dict_drink[key][0]} left.')

```

    orange juice: 1300 won. 5 left.
    coke: 800 won. 0 left.
    

3. **(20pt)** 다음과 같이 이용자가 마시고자 하는 음료와 가진 돈의 액수가 tuple 형태인 `user_choice`로 주어질 때, e.g., `user_choice = ('coke', 1000)`
* 3-1 (5pt): 원하는 음료를 `user_drink` 변수에 저장하고, 가진 돈의 액수를 `user_money`에 저장하세요. 
* 3-2 (15pt): 다음의 조건들을 체크하고 구현합니다:
  * 사용자가 원하는 음료가 자판기에 존재하지 않거나, 혹은 개수가 없다면 다음을 출력합니다:
  ```
  {음료} is not available!
  ```
  * 자판기에 존재하는 음료이면서 지불할 돈이 충분하다면 `dict_drink`에서 해당 음료의 개수를 감소시키고, 얼마를 거슬러주어야 하는지 계산하여 다음과 같이 출력합니다:
  ```
  Here you are: {음료}
  Please take {거스름돈} won
  ```

  * 지불할 돈이 충분하지 않다면 다음을 출력합니다:
  ```
  Not enough money for {음료}
  ```

* 2에서 구현한 코드를 사용하여 사용자의 이용 후 적절하게 `dict_drink`가 수정되었는지 확인해봅니다. 

    **(EN)** When the selected drink and the paid amount by a customer is given in `user_choice`, e.g., `user_choice = ('coke', 1000)`
  * 3-1 (5pt): Save the selected drink in `user_drink`, and the paid amount in `user_money`.
  * 3-2 (15pt): Implement a code with instructions below:
    * If the selected drink is not in the option (orange juice and coke) or has 0 left, print the following:
    ```
    {drink} is not available!
    ```
    * If the selected drink is in the option and the paid amount is enough to buy the drink, reduce the number of the drink left in `dict_drink`, and calculate the change and print as follows:
    ```
    Here you are: {drink}
    Please take {change} won
    ```

    * If the customer did not pay enough:
    ```
    Not enough money for {drink}
    ```

  * With the code you programmed on 2, check if the values of `dict_drink` is well modified as planned.


**실행 결과** | Result: in case of `user_choice = ('coke', 1000)` 
```
coke is not available!
orange juice: 1300 won, 5 left
coke: 800 won, 0 left
``` 

실행 결과 | Result: in case of `user_choice = ('orange juice', 1500)`
```
Here you are: orange juice
Please take 200 won
orange juice: 1300 won, 4 left
coke: 800 won, 0 left
``` 

실행 결과 | Result: in case of `user_choice = ('water', 500)` 
```
water is not available!
orange juice: 1300 won, 5 left
coke: 800 won, 0 left
```

실행 결과 | Result: in case of `user_choice = ('orange juice', 600)` 
```
Not enough money for orange juice
orange juice: 1300 won, 5 left
coke: 800 won, 0 left
```


```python
# 3
user_choice = ('coke', 1000)
# user_choice = ('orange juice', 1500)
# user_choice = ('orange juice', 1300)
# user_choice = ('orange juice', 600)
# user_choice = ('water', 500)

######### your code here #########
# 3-1 get user_drink and user_money
user_drink = user_choice[0]
user_money = user_choice[1]

'''
사용자가 원하는 음료가 자판기에 존재하지 않거나, 혹은 개수가 없다면 다음을 출력합니다:

{음료} is not available!
자판기에 존재하는 음료이면서 지불할 돈이 충분하다면 dict_drink에서 해당 음료의 개수를 감소시키고, 얼마를 거슬러주어야 하는지 계산하여 다음과 같이 출력합니다:

Here you are: {음료}
Please take {거스름돈} won
지불할 돈이 충분하지 않다면 다음을 출력합니다:

Not enough money for {음료}
'''
# 3-2 check conditions: 
if (user_drink not in dict_drink.keys()) or (dict_drink[user_drink][0]==0):
  print(f'{user_drink} is not available!')
elif user_money>=dict_drink[user_drink][1]:
  dict_drink[user_drink][0]-=1
  change = user_money - dict_drink[user_drink][1]
  print(f'Here you are: {user_drink}')
  print(f'Please take {change} won')
else:
  print('Not enough money for {user_drink}')
# check dictionary using the code you implemented in #2
for key in dict_drink:
  print(f'{key}: {dict_drink[key][1]} won. {dict_drink[key][0]} left.')


```

    coke is not available!
    orange juice: 1300 won. 5 left.
    coke: 800 won. 0 left.
    


```python
# 1
# solution
dict_drink = {'orange juice':[5,1300], 'coke':[0,800]}
print(dict_drink)
```

    {'orange juice': [5, 1300], 'coke': [0, 800]}
    


```python
# 2
# solution 
for (key, value) in dict_drink.items():
  print(f'{key}: {value[1]} won, {value[0]} left.')
```

    orange juice: 1300 won, 5 left.
    coke: 800 won, 0 left.
    


```python
# 3 
# user_choice = ('coke', 1000)
# user_choice = ('orange juice', 1500)
# user_choice = ('orange juice', 1300)
user_choice = ('orange juice', 600)
# user_choice = ('water', 500)

######### your code here #########
# 3-1 get user_drink and user_money
# solution
user_drink = user_choice[0]
user_money = user_choice[1]

# 3-2 check conditions: 
# solution
if user_drink not in dict_drink.keys() or dict_drink[user_drink][0] <= 0:
  print(f'{user_drink} is not available!')
elif user_money >= dict_drink[user_drink][1]:
  print('Here you are:', user_drink)
  dict_drink[user_drink][0] -= 1
  print(f'Please take {user_money - dict_drink[user_drink][1]} won')
else:
  print(f'Not enough money for {user_drink}')

# check dictionary using the code you implemented in #2
for (key, value) in dict_drink.items():
  print(f'{key}: {value[1]} won, {value[0]} left')
```

    Not enough money for orange juice
    orange juice: 1300 won, 5 left
    coke: 800 won, 0 left
    

## HW 2-3. List, Dictionary, Loop, If (25pts)

Instruction:

리스트 `lst_A`가 주어질 때, 각 *원소의 값*과 그 *원소가 나타난 횟수*를 key-value로 하는 딕셔너리 `dict_count`를 생성하세요. 
* 리스트는 다양한 자료형을 원소로 포함할 수 있습니다.
* 반복문과 조건문을 사용하며, 딕셔너리에 새로운 key-value를 추가하거나 기존의 값을 수정할 수 있어야 합니다.

    **(EN)** Given the list `lst_A`, create a dictionary `dict_count` where the key-value pair takes *the value of each element in `lst_A`* and *the number of occurrences of the element in `lst_A`*.
    * The list can contain multiple data types as elements.
    * Use loop and conditional statements, and the dictionary should be editable (e.g., add key-pair)

**실행 결과** | Result: 
```
Original list: [True, 10, 3, 'a', 3, 'b', 'a', '10', 'hello', True, 'True']
Count dictionary: {True: 2, 10: 1, 3: 2, 'a': 2, 'b': 1, '10': 1, 'hello': 1, 'True': 1}
```


```python
lst_A = [True,10,3,'a',3,'b','a','10','hello',True,'True']

dict_count = {}

######### your code here #########
for i in lst_A:
  dict_count[i]=lst_A.count(i)

print('Original list:', lst_A)
print('Count dictionary:', dict_count)
```

    Original list: [True, 10, 3, 'a', 3, 'b', 'a', '10', 'hello', True, 'True']
    Count dictionary: {True: 2, 10: 1, 3: 2, 'a': 2, 'b': 1, '10': 1, 'hello': 1, 'True': 1}
    


```python
lst_A = [True,10,3,'a',3,'b','a','10','hello',True,'True']

dict_count = {}

######### your code here #########
# solution
for val in lst_A:
  if val in dict_count.keys():
    dict_count[val] += 1
  else:
    dict_count[val] = 1

print('Original list:', lst_A)
print('Count dictionary:', dict_count)
```

    Original list: [True, 10, 3, 'a', 3, 'b', 'a', '10', 'hello', True, 'True']
    Count dictionary: {True: 2, 10: 1, 3: 2, 'a': 2, 'b': 1, '10': 1, 'hello': 1, 'True': 1}
    
