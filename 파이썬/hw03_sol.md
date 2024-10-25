# SCS2013 Python Programming Homework 3 (100pts)

About Functions!

## HW 3-1. Function (30pts)

Instruction:

1. (**10pt**) 과거의 값과 현재의 값을 비교해 몇 퍼센트가 증감했는지 계산하는 함수 `change_ratio` 함수를 구현하세요. 
- 함수는 두개의 숫자(과거값, 현재값)를 입력으로 받습니다.
- 변화율(퍼센트)을 계산하여 반환합니다. (변화율은 과거 값 대비 현재 값이 얼만큼 바뀌었는지 그 비율을 의미합니다)

실행 결과 (example):
```
print(change_ratio(20,25))
print(change_ratio(25,20))
>>
25.0
-20.0
```

2. (**20pt**) 1에서 구현한 `change_ratio` 함수를 사용하여 여러 해에 걸친 값의 증감 변화율의 평균을 계산하는 함수 `avg_change_ratio` 함수를 구현하세요. 
- n년 동안의 과거 값과 현재 값이 각각 리스트로 주어집니다.
- 함수는 두개의 리스트를 입력으로 받습니다. 
- 1) 각 해의 변화율을 계산하고 모아 리스트를 만들고 
- 2) n년 동안의 평균 변화율을 계산합니다.
- 3) 각 해의 변화율 리스트와 평균 변화율을 모두 반환합니다.

실행 결과 (example):
```
lst_1 = [20, 25, 40]
lst_2 = [25, 40, 50]

lst_ratio, average_ratio = avg_change_ratio(lst_1, lst_2)
print('List of ratio: ', lst_ratio)
print('Average ratio: ', average_ratio)
>>
List of ratio:  [25.0, 60.0, 25.0]
Average ratio:  36.666666666666664
```


```python

```


```python
# 1
# your code here


# solution
def change_ratio(old, new):
  ratio = (new - old)/old * 100
  return ratio
```


```python
# check your function 
print(change_ratio(20,25))
print(change_ratio(25,20))
```

    25.0
    -20.0
    


```python
# 2
# your code here
# solution
def avg_change_ratio(lst_old, lst_new):
  lst_ratio = []

  for i in range(len(lst_old)):
    lst_ratio.append(change_ratio(lst_old[i], lst_new[i]))

  avg_ratio = sum(lst_ratio)/len(lst_ratio)

  return lst_ratio, avg_ratio
```


```python
# check your function
lst_1 = [20, 25, 40]
lst_2 = [25, 40, 50]

lst_ratio, average_ratio = avg_change_ratio(lst_1, lst_2)
print('List of ratio: ', lst_ratio)
print('Average ratio: ', average_ratio)
```

    List of ratio:  [25.0, 60.0, 25.0]
    Average ratio:  36.666666666666664
    

## HW 3-2. Functions (20pt)

Instruction: 

학생들에 대한 나이(age), 과목(course), 점수(score)에 대한 정보를 담고 있는 3개의 딕셔너리 `age_dct`, `course_dct`, `score_dct`가 다음과 같이 주어질 때, 학생들의 정보를 출력하는 `show_info` 함수를 구현하세요.

- **아래의 함수 코드 중 빈 부분을 작성하세요.**
- 함수는 학생의 이름(string)을 입력으로 받습니다. 
- 함수는 출력하고 싶은 정보(age, course, score)와 해당 딕셔너리를 원하는 갯수만큼 keyword 형태로 입력받습니다.
  - 즉, 함수를 정의할 때 "**" 를 사용합니다.
  - 예를 들어, 'Carlos'의 나이와 과목 정보를 출력하고자 한다면 함수의 호출은 `show_info('Carlos', age=age_dct, course=course_dct)`로 이루어집니다. 
  - 'Patrick'의 과목, 점수 정보를 출력하고자 한다면 `show_info('Patrick', course=course_dct, score=score_dct)`로 호출하여 사용할 수 있습니다.

- 이 함수는 호출 시 입력 받은 딕셔너리 중에서 해당 학생의 정보를 아래와 같이 출력합니다. 

실행 결과 (1)
```
show_info('Carlos', age=age_dct, course=course_dct)
>>>
=====
Name: Carlos
age: 20
course: Python_02
=====
```

실행 결과 (2)
```
show_info('Patrick', course=course_dct, score=score_dct)
>>>
=====
Name: Patrick
course: Capstone
score: 75
=====
```



```python
age_dct = {'Carlos': 20, 'Patrick': 18, 'Drake': 27}
course_dct = {'Patrick': 'Capstone', 'Carlos': 'Python_02', 'Drake': 'Python_01'}
score_dct = {'Carlos': 30, 'Drake': 100, 'Patrick': 75}
```


```python
def show_info(name, **info):
  print('=====')
 
  # solution
  print(f'Name: {name}')

  # solution
  for key in info.keys():
    print(f"{key}: {info[key][name]}")

  print('=====')
```


```python
# check your function
show_info('Carlos', age=age_dct, course=course_dct)
show_info('Patrick', course=course_dct, score=score_dct)
```

    =====
    Name:Carlos
    age: 20
    course: Python_02
    =====
    =====
    Name:Patrick
    course: Capstone
    score: 75
    =====
    

## HW 3-3. Lambda Function (30pts)

Instruction:

1. (**15pt**) `lambda` 함수, `map()`, `filter()`를 사용하여 아래 리스트 `student_lst`에서 주소 ('address')에 해당하는 값이 'unknown'인 사람의 정보를 삭제한 리스트 `new_lst`를 만들어보세요.

실행 결과:
```
print(new_lst)
>>>
[{'name': 'Harry Potter', 'father': 'James Potter', 'address': 'Hogwarts School of Witchcraft and Wizardry'}, {'name': 'Cooper Garg', 'father': 'Kamal Garg', 'address': 'Dongguk University'}]

```

2. (**15pt**) lambda 함수를 사용하여 다양한 단어들로 이루어진 리스트 `words`에서 있는 단어들을 모두 대문자로 바꾼 리스트 `upper_words`를 만들어보세요. 

실행 결과:
```
print(upper_words)
>>>
['BANANA', 'MELON', 'MADAM', 'REFER', 'MANGO', 'KOREA']
```


```python
# 1
student_lst = [{'name': 'Harry Potter', 'father': 'James Potter', 'address': 'Hogwarts School of Witchcraft and Wizardry'}, 
               {'name': 'Emma Stone', 'father': 'Andrew Stone', 'address': 'Unknown'},
               {'name': 'Cooper Garg', 'father': 'Kamal Garg', 'address': 'Dongguk University'},
               {'name': 'Carol Steven', 'father': 'Jacob Steven', 'address': 'Unknown'}
               ]

# solution
new_lst = list(filter(lambda x:x['address'] != 'Unknown', student_lst))
print(new_lst)

```

    [{'name': 'Harry Potter', 'father': 'James Potter', 'address': 'Hogwarts School of Witchcraft and Wizardry'}, {'name': 'Cooper Garg', 'father': 'Kamal Garg', 'address': 'Dongguk University'}]
    


```python
# 2
words = ['baNAna', 'meLon', 'madam', 'Refer', 'mango', 'KORea']

# your code here
# solution
upper_words = list(map(lambda x:x.upper(), words))
print(upper_words)
```

    ['BANANA', 'MELON', 'MADAM', 'REFER', 'MANGO', 'KOREA']
    

## HW 3-4. Recursion Function (20pts)

Instruction: 

아래와 같이 1개의 루트 노드로 시작하여 모든 노드가 2개의 하위 노드를 가지는 구조를 "포화 이진 트리"라고 부릅니다. **재귀함수**를 사용하여 깊이 n을 가지는 포화 이진 트리의 총 노드 개수를 계산하는 함수 `binary_tree`를 작성하세요. 

- 함수는 포화 이진 트리의 깊이를 입력으로 받고, 해당 포화 이진 트리의 총 노드 개수를 계산하여 반환합니다.

ex) 
```
                   o
              
          o                  o

     o         o        o         o
     

  o    o    o    o    o    o    o    o
```
- 깊이 0에서는 루트 노드 1개로 총 1개의 노드가 존재
- 깊이 1에서는 루트 노드 1개 + 하위 노드 2개로 총 3개의 노드가 존재
- 깊이 2에서는 깊이 1로부터 하위 노드가 4개 추가되어 총 7개의 노드가 존재 

실행 결과:
```
print(binary_tree(0))
print(binary_tree(1))
print(binary_tree(2))
print(binary_tree(3))
print(binary_tree(4))
print(binary_tree(5))
>>>
1
3
7
15
31
63
```


```python
# your code here:
# solution
def binary_tree(depth):
  if depth == 0:
    return 1
  elif depth == 1:
    return 3
  else:
    leaf_num = binary_tree(depth-1)-binary_tree(depth-2)
    total_num = binary_tree(depth-1) + 2*leaf_num
    # print(f'Total node at depth {depth}: {total_num}')
    return total_num

# another solution
def binary_tree(depth):
  if depth == 0:
    return 1
  else:
    total_num = binary_tree(depth-1)*2 + 1
    return total_num
```


```python
# check your function
print(binary_tree(0))
print(binary_tree(1))
print(binary_tree(2))
print(binary_tree(3))
print(binary_tree(4))
print(binary_tree(5))
```

    1
    3
    7
    15
    31
    63
    


```python

```
