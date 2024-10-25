# SCS2013 Python Programming Homework 1 (100pts)

About Variables, Data Types, basic Operators, and Strings!


## HW 1-1. Variables (변수) (15pts)

Instruction:
1. **(5pt)** `name`, `age`, `speed`, `answer` 변수를 생성하고 각각 string, int, float, boolean 타입의 값 (Eric, 74, 13.5, False) 을 할당하세요.

  - Create variables `name`, `age`, `speed`, `answer` and assign string, int, float, boolean values (Eric, 74, 13.5, False) respectively.

2. **(5pt)** type() 함수를 통해 각 변수의 자료형을 확인하고 출력하세요.
  - Check and print data type of each variable by using type().
  
3. **(5pt)** 생성한 변수를 f-string 포매팅을 사용해 다음의 문장으로 출력하세요. (줄바꿈에 유의하세요)
  - Print following sentence by using f-string and all the variables you created above. (Note that we have a line break)

  ```
  Hello Eric, you are 74 years old. We heard that you run 13.5km per hour. Is that true? 
  False
  ```


```python
# your code here
# 1


# 2


# 3


```


```python
# solution
# 1
name = "Eric"
age = 74
speed = 13.5
answer = False

# 2
print(type(name), type(age), type(speed), type(answer))

# 3
print("Hello {}, you are {} years old. We heard that you run {}km per hour. Is that true? \n{}".format(name, age, speed, answer))
```

    <class 'str'> <class 'int'> <class 'float'> <class 'bool'>
    Hello Eric, you are 74 years old. We heard that you run 13.5km per hour. Is that true? 
    False
    

## HW 1-2. Mathematical operators (20pts)

Instruction: 
1. **(5pt)** $20$ 나누기 $4$ 의 결과를 저장하는 변수 `a`를 선언하세요. (모든 결과는 출력해주세요)

  * **note**: 값이 5인가요 5.0 인가요? type()을 출력해보세요.
  * Create a variable `a` and set it equal to $20$ divided by $4$ (note: Is the value 5 or 5.0? Please check by using type())

2. **(5pt)** $24$를 $7$로 나눈 **나머지를** 저장하는 변수 `b`를 선언하세요.
  * Create a variable `b` and set it equal to the remainder from dividing $24$ by $7$

2. **(10pt)** $1 + 3 \times 2^4$ 를 계산하여 저장하는 변수 `c`를 선언하세요. 
  * Create a variable `c` and set it equal to the value of $1 + 3 \times 2^4$

**Hint**: You need to use mathematical operators (`* - / + % **`) for this to work.



```python
# your code here
# 1


# 2


# 3


```


```python
# solution
# 1
a = 20 / 4

# 2
b = 24 % 7

# 3
c =  1 + 3 * 2 ** 4

print('1: the value of a is ', a)
print('type of a', type(a))
print('2: the value of b is ', b)
print('3: the value of c is ', c)
```

    1: the value of a is  5.0
    type of a <class 'float'>
    2: the value of b is  3
    3: the value of c is  49
    

## HW 1-3. Comparison, Logical operators (20pts)

1. **(5pt)** 아래 코드의 `x`,`y`,`z`를 사용하여 계산을 하고자 하는데 `x`와 `y`는 계산 불가한 `string` 형태입니다. 이후의 연산이 가능하도록 두 변수를 `int` 형태로 변환하세요.
  * From variables `x`,`y`,`z` below, `x` and `y` are `string` type. Cast them into `int` type for further mathmatical operations.

2. **(6pt)** $\frac{x+y}{z}$ 를 계산하여 `result`에 저장하여 값이 $1$보다 작은지 확인하세요. (각 결과는 출력하세요)
  * Compute $\frac{x+y}{z}$ and set the resulting value to a variable `result`. Check if `result` is less than $1$

3. **(3pt)** `result`의 값이 $30$ 이상인지 확인하세요.
  * Check if `result` is greater than or equal to $30$

4. **(3pt)** `result`의 값이 $9$의 배수인지 확인하세요.
  * Check if `result` is a multiple of $9$

4. **(3pt)** `result`의 값이 $22$인지 확인하세요.
  * Check if `result` is equal to $22$


```python
x = "11"
y = "33"
z = 2

# your code here
#===============================
# 1


# 2


# 3


# 4


# 5


#===============================
```


```python
x = "11"
y = "33"
z = 2

# solution
# 1
x=float(x)
y=float(y)

# 2
result = (x+y)/z
print(result)
print(result < 1)

# 3
print(result >= 30)

# 4
print(result % 9 == 0)

# 5
print(result == 22)
```

    22.0
    False
    False
    False
    True
    

## HW 1-4. Strings (25pts)
아래에 `sentence`에 저장된 문장에는 오타와 문법적 오류가 존재합니다. indexing, slicing, string method를 통해 해결해보세요. (**note**: `sentence`의 내용 자체가 수정되어야 합니다.)

`sentence` below contains typos and grammar issues. Correct them with indexing, slicing, and string methods. (**note**: `sentence` itself should be modified accordingly.)

1. **(5pt)** 'too'는 오타이므로 o를 제거해야합니다. slicing과 +를 사용해 제거하세요. (매 과정마다 결과를 출력하세요)
  *  'too' is a typo. Use slicing and + operator to remove 'o' from the word.

2. **(5pt)** ourself 는 ourselves로 교체되어야 합니다. replace()를 사용해 교체하세요.
  * Replace 'ourself' with 'ourselves with replace()'

3. **(5pt)** 영문장은 대문자로 시작해야 합니다. capitalize() 를 사용해 수정하세요.
  * English sentence should start with a capital letter. Capitalize `sentence` with capitalize()

4. **(5pt)** 문장의 마지막에 마침표가 없습니다. 마침표를 추가하세요.
  * Punctuation is missing at the end of `sentence`. Add one.

5. **(5pt)** 문장이 몇개의 단어로 이루어졌는지 구하세요. (단어의 기준: 공백)
  * Count the number of words in the `sentence`. (words are sepererated with space) 

올바른 문장 결과: 
```It is not in the stars to hold our destiny but in ourselves.```


```python
sentence = "it is not in the stars too hold our destiny but in ourself"

# your code here
#===============================
# 1


# 2


# 3


# 4


# 5


#===============================
```


```python
sentence = "it is not in the stars too hold our destiny but in ourself"

# solution
# 1
sentence = sentence[:25]+sentence[26:]
print(sentence)

# 2
sentence = sentence.replace('ourself', 'ourselves')
print(sentence)

# 3
sentence = sentence.capitalize()
print(sentence)

# 4
sentence = sentence + '.'
print(sentence)

# 5
print(len(sentence.split()))
```

    it is not in the stars to hold our destiny but in ourself
    it is not in the stars to hold our destiny but in ourselves
    It is not in the stars to hold our destiny but in ourselves
    It is not in the stars to hold our destiny but in ourselves.
    13
    

## HW 1-5. Strings (20pts)

다음의 `my_str`의 문자열을 slicing을 사용하여 3개의 문자열로 분리하고, 정렬 (alignment) 하여 출력하세요. 

1. **(5pt)** `str_a`, `str_b`, `str_c`는 휴대폰 번호의 앞3자리, 중간 4자리, 끝 4자리를 문자열의 형태로 가지도록 만드세요: 직접 값을 할당하는 것이 아니라 `my_str`을 slicing하여 가져와야 합니다. 
  * Separate `my_str` into 3 strings: `str_a` has the first 3 numbers, `str_b` has the middle 4 numbers, `str_c` has the last 4 numbers (by using slicing)

2. **(5pt)** `str_a`는 전체 길이 7로 출력하되 왼쪽 정렬하고 빈 공간은 `@`로 채웁니다. 
  * Print `str_a`: it should be left aligned and blank space filled with '@', with total length $7$

3. **(5pt)** `str_b`는 전체 길이 7로 출력하되 가운데 정렬하고 빈 공간은 `!`로 채웁니다. 
  * Print `str_b`: it should be middle aligned and blank space filled with '!', with total length $7$

4. **(5pt)** `str_c`는 전체 길이 7로 출력하되 오른쪽 정렬하고 빈 공간은 `&`로 채웁니다.
  * Print `str_c`: it should be right aligned and blank space filled with '&', with total length $7$

실행 결과: 
```
010@@@@
!2468!!
&&&1357
```




```python
my_str = '010-2468-1357'

# your code here
#===============================
# 1


# 2


# 3


# 4


#===============================
```


```python
my_str = '010-2468-1357'

# solution 
# 1
str_a = my_str[:3]
str_b = my_str[4:8]
str_c = my_str[9:]

print(str_a, str_b, str_c)

# 2
print(f'{str_a:@<7}')

# 3
print(f'{str_b:!^7}')

# 4
print(f'{str_c:&>7}')
```

    010 2468 1357
    010@@@@
    !2468!!
    &&&1357
    
