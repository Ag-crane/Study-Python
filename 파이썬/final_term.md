# SCS2013 Python Programming Final Exam (2022-Fall 1분반)

SCS2013 Python Programming 기말고사입니다. 

주어진 설명을 잘 읽고, 구체적인 지시사항이 있다면 그에 따라 구현하세요. 

코드를 완성한 후, **SCS2013_a_final_학번_이름.ipynb** 로 파일을 저장한 후 eclass의 과제제출을 통해 제출하세요. 

## P-1 (10 pt) [Function]


임의의 자연수를 입력받아 그 숫자가 **소수 (prime number) 인지 확인**하는 함수 `check_prime` 함수를 구현하세요. 

* 임의의 정수 (1보다 큰 자연수라고 가정합니다) 를 입력받습니다. 
* 그 숫자가 prime number인지 확인하여 True/False를 반환합니다. 
* Prime number란 1과 자기 자신만을 약수로 가지는 수를 의미합니다.  
  * e.g., $2, 3, 5, 7, 11, 13, 17, ... $

* Implement a function `check_prime` that check whether the given integer (greater than 1) is a prime number or not (return True/False)

실행 결과: 
```
num1 = 2
num2 = 17
num3 = 15

print(f'{num1} is Prime number? -> {check_prime(num1)}')
print(f'{num2} is Prime number? -> {check_prime(num2)}')
print(f'{num3} is Prime number? -> {check_prime(num3)}')
>>>
2 is Prime number? -> True
17 is Prime number? -> True
15 is Prime number? -> False
```


```python
# P-1
# your code here:
# n>!
def check_prime(n):
  count=0
  for i in range(1,n+1):
    if n%i==0:
      count+=1
  return count==2



```


```python
# check your code:
num1 = 2
num2 = 17
num3 = 15

print(f'{num1} is Prime number? -> {check_prime(num1)}')
print(f'{num2} is Prime number? -> {check_prime(num2)}')
print(f'{num3} is Prime number? -> {check_prime(num3)}')
```

    2 is Prime number? -> True
    17 is Prime number? -> True
    15 is Prime number? -> False
    

## P-2 (20 pt) [Class, Inheritance]

**(a) [10 pt]** Class를 이용하여 계좌 클래스 `Account`를 완성하세요. (완성해야 하는 부분들은 bold 처리된 함수들입니다: Need to complete methods that are made bold below)

class `Account`:
* **생성자 (constructor)**:
  * **계좌 소유주 이름, 계좌 잔고, 계좌 번호를 입력으로 받아 생성**
  * `holder_name`: 계좌 소유주 이름 
  * `balance`: 계좌 잔고
  * `acc_number`: 계좌 번호

  * `acc_type`: 계좌의 종류 (항상 **1**의 값을 갖도록 설정) 
    * (for `Account` class, this variable always has value of 1)

* `display()` method:
  * 계좌 정보를 출력

* **`deposit(amount)` method**: 
  * 입력으로 받은 `amount`의 돈을 계좌 잔고에 입금
  * 다음과 같이 계좌 번호와 입금한 금액을 출력한 후 `display()` 함수를 호출하여 계좌 정보를 출력 (정보 출력의 형태는 꼭 똑같이 않아도 되며, 정보가 잘 출력되기만 하면 됨)
  * 입금이 성공적으로 이루어지면 True를 반환
  * Deposit given `amount` to the balance of the account, and call `display()` method for displaying account's information. Return True if the deposit is successfully done.
  
  예시 결과:
  ```
  +++++
  Acc num: 49, Amount deposited: 222 won
  Normal Account - Name: James, Acc num: 49, Balance: 522 won
  +++++
  ```

* **`withdraw(amount)` method**:
  * 입력으로 받은 `amount`의 돈을 계좌 잔고에서 출금
  * 다음과 같이 계좌 번호와 출금한 금액을 출력한 후, `display()` 함수를 호출하여 계좌 정보를 출력
  * 잔고가 부족하다면 메세지를 출력: e.g., "Insufficient balance to withdraw"
  * 출금이 성공적으로 이루어짐을 알리는 True/False를 반환
  * Withdraw given `amount` from the balance of the account, and call `display()` method for displaying account's information. Return True if the withdraw is successfully done.

  예시 결과:
  ```
  +++++
  Acc num: 94, Amount withdrawn: 150 won
  Normal Account - Name: Peter, Acc num: 94, Balance: 450 won
  +++++
  ```


```python
# P-2 Account
class Account():
  # your code here: constructor
  def __init__(self, holder_name, balance, acc_number):
    self.holder_name = holder_name
    self.balance = balance
    self.acc_number = acc_number
    self.acc_type = 1

  # your code here: deposit

  def deposit(self, amount):
    self.balance += amount
    print(f'Acc num: {self.acc_number}, Amount deposited: {amount} won')
    self.display()
    return True

  # your code here: withdraw

  def withdraw(self, amount):
    if self.balance >= amount:
      self.balance -= amount
      print(f'Acc num: {self.acc_number}, Amount withdrown: {amount} won')
      self.display()
      return True
    else:
      print("Insufficient balance to withdraw")
      return False


  def display(self):
    print(f'Normal Account - Name: {self.holder_name}, Acc num: {self.acc_number}, Balance: {self.balance} won')
```

**(b) [10 pt]** `Account`클래스를 상속받는 child class 예금 계좌 `SavingAccount`를 완성하세요. (완성해야 하는 부분들은 bold 처리된 함수들입니다.)

class `SavingAccount`:
* `Account`를 상속
* **생성자 (constructor)**:
  * **계좌 소유주 이름, 계좌 잔고, 계좌 번호, 금리, 인출 수수료를 입력으로 받아 생성**
  * `holder_name`: 계좌 소유주 이름
  * `balance`: 계좌 잔고
  * `acc_number`: 계좌 번호
  * `rate`: 예금 금리 (rate of interest)
  * `w_fee`: 인출 수수료 (withdraw fee)

  * `acc_type`: 계좌의 종류 (항상 **2**의 값을 갖도록 설정)
    * (for `SavingAccount` class, this variable always has value of 2)

* `display()` method:
  * 계좌 정보를 출력

* `deposit(amount)` method: 
  * `Account`의 `deposit`과 동일

* **`withdraw(amount)` method**:
  * 입력으로 받은 `amount`만큼의 돈 외에도 인출 수수료 `w_fee`만큼의 돈을 추가로 출금
  * 그 외에는 `Account`의 `withdraw`와 동일
  * Need to withdraw `amount` with a fee `w_fee`

  예시 결과:
  ```
  +++++
  Acc num: 22, Amount withdrawn: 215 won
  Saving Account - Name: Emma, Acc num: 22, Balance: 185 won
  +++++
  ```

* **`interest()` method**:
  * 계좌 잔고와 예금 금리에 해당하는 예금 이자를 계산: balance $\times$ rate (예금 이자는 `round` 함수를 통해 정수로 변환하여 반영)
  * 계산한 예금 이자만큼 계좌 잔고가 증가해야 함 
  * 다음과 같이 계좌 번호와 예금 이자 금액을 출력한 후, `display()` 함수를 호출하여 계좌 정보를 출력
  * 예금 이자 반영이 성공적으로 이루어지면 True를 반환
  * Compute amount of interest of the saving account (balance $\times$ rate) and increase the balance as amount of the interest. Call `display()` method for displaying account's information and return True if the interest update is successfully done.


```python
# P-2 (b)

# your code here (complete the class format)
class SavingAccount(Account):
  # your code here: constructor
  def __init__(self, holder_name, balance, acc_number, rate, w_fee):
    super().__init__(holder_name, balance, acc_number)
    self.rate = rate
    self.w_fee = w_fee
    self.acc_type = 2
  # your code here: withdraw
  def withdraw(self,amount):
    amount2 = amount + self.w_fee 
    super(amount2)

  # your code here: interest
  def interest(self):
    interest = self.balance * round(self.rate)
    self.balance += interest
    print(f'Acc num: 22, Amount interest: {interest} won')
    display()
    return True

    
  def display(self):
    print(f'Saving Account - Name: {self.holder_name}, Acc num: {self.acc_number}, Balance: {self.balance} won')
```

## P-3 (15 pt) [Class]

Class를 이용하여 은행 클래스 `Bank`를 완성하세요. (완성해야 하는 부분들은 bold 처리된 함수들입니다.)

class `Bank`:
* **생성자 (constructor)**
  * **예금 금리, 인출 수수료를 입력으로 받아 생성**
  * `rate`: 예금계좌의 예금 금리 (입력이 없는 경우 0.02를 기본으로 가짐)
  * `w_fee`: 예금계좌의 인출 수수료 (입력이 없는 경우 15를 기본으로 가짐)

  * `users`: 계좌를 개설한 고객들의 이름 리스트 (초기값은 empty list로 초기화)
  * `accounts`: 보유하고 있는 계좌 "객체" 들의 리스트 (초기값은 empty list로 초기화)
  * `users` and `accounts` are lists of users and accounts of the bank (initially set to empty lists). `rate` has default value 0.02 and `w_fee` has default value of 15 if they are not given.

  예시 결과:
  ```
  bank = Bank()
  ```

* `display()` method:
  * 총 고객 수, 총 계좌 개수를 출력
  * 각 계좌의 `display()`함수를 이용해 각 계좌 정보를 출력

  예시 결과:
  ```
  bank.display()
  >>>
  === Bank Information ===
  User list: total 2 users
  Account list: total 2 accounts
  -----
  Normal Account - Name: James, Acc num: 72, Balance: 100 won
  Saving Account - Name: Emma, Acc num: 33, Balance: 550 won
  ==========
  ```

* `search_account(acc_number)` method:
  * 입력으로 받은 계좌 번호 `acc_number`를 가진 계좌가 은행에 존재하는 지 확인
  * `acc_number`가 `self.accounts`에 속한 계좌들의 계좌 번호에 해당하면 해당 계좌 객체를 반환
  * 그렇지 않으면 False를 반환
  * A method that searches given `acc_number` already exists in the bank system, and return the account object if it exists, or False if it does not exist

* `interest()` method:
  * 보유하고 있는 계좌들 중 예금 계좌 (`SavingAccount`)에 해당하는 계좌들의 예금 이자를 계산하여 업데이트하는 함수 
  * 예금 계좌들에 대해 해당 계좌의 `interest()` 함수를 호출하여 예금 이자를 반영 
  * Update interest of all saving accounts of the bank by calling `interest()` method of the saving account
  
  예시 결과:
  ```
  bank.interest()
  bank.display()
  >>>
  +++ Interest +++
  Acc num: 33, Amount of interest: 11 won
  Saving Account - Name: Emma, Acc num: 33, Balance: 561 won
  +++++
  === Bank Information ===
  User list: total 2 users
  Account list: total 2 accounts
  -----
  Normal Account - Name: James, Acc num: 72, Balance: 100 won
  Saving Account - Name: Emma, Acc num: 33, Balance: 561 won
  ==========
  ```

* **`create_account()` method**: 
  * 새로운 계좌를 생성하는 함수 
  * 사용자로부터 고객 이름 (`holder_name`)을 입력 받음
    * 입력받은 고객이 `self.users` 리스트에 없는 경우 새롭게 추가 
  * 사용자로부터 처음 입금하고자 하는 금액 (`balance`)을 입력 받음 (0보다 큰 정수여야 함)
  * 랜덤 계좌 번호 (`acc_number`) 생성
    * 1과 100 사이의 범위에서 랜덤 정수값으로 생성
    * 생성되는 계좌 번호는 이미 존재하는 다른 계좌 번호들과 중복되어서는 안됨 (`self.search_account()`를 활용하여 체크 가능)

  * 어떤 종류의 계좌를 개설하고자 하는지 (`acc_type`)를 사용자로부터 입력으로 받음
    * 입력 값이 1이면 Normal 계좌인 `Account`를 생성하고, 
    * 입력 값이 2이면 Saving 계좌인 `SavingAccount`를 생성 
    * 계좌가 생성된 후에는 `self.accounts` 리스트에 생성한 계좌 객체를 추가

  * 새롭게 생성된 계좌 객체를 반환
  * Create a new account and return the new account. Take `holder name` (if `holder_name` is not in the `self.users` add the new user), `balance`, and `acc_type` (create `Account` or `SavingAccount` accordingly and add the new account to the `self.accounts`) from the user input. Create a random `acc_number` as a random integer in range of $[1,100)$ and need to check it should be unique (not duplicated with the existing acc_numbers: use `search_account()` for this purpose). 

  예시 결과:
  ```
  Acc1 = bank.create_account()
  Acc2 = bank.create_account()
  bank.display()
  >>>
  === Create new account ===
  Enter your full name: James
  Welcome to our bank!
  Enter amount to be deposited at new account: 100
  What type of account do you want to open? 
  1 (Normal), 2 (Saving): 1
  New account is created
  ==========
  Normal Account - Name: James, Acc num: 72, Balance: 100 won
  === Create new account ===
  Enter your full name: Emma
  Welcome to our bank!
  Enter amount to be deposited at new account: 550
  What type of account do you want to open? 
  1 (Normal), 2 (Saving): 2
  New account is created
  ==========
  Saving Account - Name: Emma, Acc num: 33, Balance: 550 won
  === Bank Information ===
  User list: total 2 users
  Account list: total 2 accounts
  -----
  Normal Account - Name: James, Acc num: 72, Balance: 100 won
  Saving Account - Name: Emma, Acc num: 33, Balance: 550 won
  ==========
  ```
    

* **`transaction(account)` method**: 
  * 거래 (deposit, withdraw, transfer) 를 수행하는 함수 
  * 거래를 실행하고자 하는 계좌 `account` 를 입력변수로 가짐 

  * 입력변수로 받은 `account`가 보유하고 있는 유효한 계좌인 경우에 대해 거래를 수행
    * 사용자로부터 원하는 거래의 종류를 입력받음 
    * 1: Deposit (입금), 2: Withdraw (출금), 3: Transfer (송금)
    * 입금/출금의 경우, 원하는 금액을 사용자로부터 입력 받고 (0보다 큰 정수 형태로 입력 받아야 함) 해당 계좌의 거래에 맞는 함수를 실행함 (`account`가 가진 `deposit` 혹은 `withdraw` 함수를 호출)
    * 송금의 경우, 송금하고자 하는 대상 계좌 번호와 원하는 금액을 사용자로부터 입력 받아야 하며, 대상 계좌가 `self.accounts`에 존재하는 계좌인지 `self.search_account()` 함수를 이용해 확인
    * 송금이 가능한 계좌인 경우, `account`에서는 출금을, 대상 계좌에서는 입금을 수행하여 송금을 실행함
    * 거래가 성공적으로 이루어짐을 알리는 True/False를 반환

  * Perform transaction (deposit, withdraw, transfer) of the given `account`. Take transaction type from the user input (1: deposit, 2: withdraw, 3: transfer). In case of deposit/withdraw, take `amount` from the user input and call the corresponding method of the account. In case of transfer, take destination acc_number and `amount` from the user input, and check the destination account is in `self.accounts` (use `search_account()`), and withdraw from the `account` and deposit to the destination account. Return True if the transaction is successfully done.

  예시 결과 (deposit):
  ```
  bank.transaction(Acc1)
  >>>
  Hi James! What do you want to do? 
  1 (Deposit), 2 (Withdraw), 3 (Transfer): >> 1
  Enter amount to be deposited: >> 330
  +++ Deposit +++
  Acc num: 72, Amount deposited: 330 won
  Normal Account - Name: James, Acc num: 72, Balance: 430 won
  +++++
  Transaction success!
  ```

  예시 결과 (withdraw):
  ```
  bank.transaction(Acc2)
  >>>
  Hi Emma! What do you want to do? 
  1 (Deposit), 2 (Withdraw), 3 (Transfer): >> 2
  Enter amount to be withdrawn: >> 250
  +++ Witdraw +++
  Acc num: 33, Amount withdrawn: **265** won
  Saving Account - Name: Emma, Acc num: 33, Balance: 285 won
  +++++
  Transaction success!
  ```

  예시 결과 (transfer):
  ```
  bank.transaction(Acc1)
  bank.display()
  >>>
  Hi James! What do you want to do? 
  1 (Deposit), 2 (Withdraw), 3 (Transfer): >> 3
  Enter destination account number to transfer: >> 33
  Enter amount to be transferred to: >> 130
  +++ Witdraw +++
  Acc num: 72, Amount withdrawn: 130 won
  Normal Account - Name: James, Acc num: 72, Balance: 300 won
  +++++
  +++ Deposit +++
  Acc num: 33, Amount deposited: 130 won
  Saving Account - Name: Emma, Acc num: 33, Balance: 415 won
  +++++
  Transaction success!
  === Bank Information ===
  User list: total 2 users
  Account list: total 2 accounts
  -----
  Normal Account - Name: James, Acc num: 72, Balance: 300 won
  Saving Account - Name: Emma, Acc num: 33, Balance: 415 won
  ==========
  ```
    


```python
# P-3 Bank

class Bank():
  # your code here: constructor




  def display(self):
    print('=== Bank Information ===')
    print(f'User list: total {len(self.users)} users')
    print(f'Account list: total {len(self.accounts)} accounts')
    print('-----')

    for account in self.accounts:
      account.display()
    print('==========')

  def search_account(self, acc_number):
    for account in self.accounts:
      if account.acc_number == acc_number:
        return account  
    return False


  # your code here: create_account
  def create_account(self):
    print('=== Create new account ===')
    
    # holder_name


    # balance


    # acc_number, create account (type)   
    

    new_account.display()
    return new_account 


  # your code here: transaction
  def transaction(self, account):



  def interest(self):
    for account in self.accounts:
      if account.acc_type == 2:
        account.interest()
    return True
```


```python
# test your code:
bank = Bank()
Acc1 = bank.create_account()
Acc2 = bank.create_account()
bank.display()
```

    === Create new account ===
    Enter your full name: James
    Welcome to our bank!
    Enter amount to be deposited at new account: 100
    What type of account do you want to open? 
    1 (Normal), 2 (Saving): 1
    New account is created
    ==========
    Normal Account - Name: James, Acc num: 72, Balance: 100 won
    === Create new account ===
    Enter your full name: Emma
    Welcome to our bank!
    Enter amount to be deposited at new account: 550
    What type of account do you want to open? 
    1 (Normal), 2 (Saving): 2
    New account is created
    ==========
    Saving Account - Name: Emma, Acc num: 33, Balance: 550 won
    === Bank Information ===
    User list: total 2 users
    Account list: total 2 accounts
    -----
    Normal Account - Name: James, Acc num: 72, Balance: 100 won
    Saving Account - Name: Emma, Acc num: 33, Balance: 550 won
    ==========
    


```python
# test your code: 
bank.transaction(Acc1)
bank.display()
```

    Hi James! What do you want to do? 
    1 (Deposit), 2 (Withdraw), 3 (Transfer): 1
    Enter amount to be deposited: 330
    +++ Deposit +++
    Acc num: 72, Amount deposited: 330 won
    Normal Account - Name: James, Acc num: 72, Balance: 430 won
    +++++
    Transaction success!
    === Bank Information ===
    User list: total 2 users
    Account list: total 2 accounts
    -----
    Normal Account - Name: James, Acc num: 72, Balance: 430 won
    Saving Account - Name: Emma, Acc num: 33, Balance: 550 won
    ==========
    


```python
# test your code: 
bank.transaction(Acc2)
bank.display()
```

    Hi Emma! What do you want to do? 
    1 (Deposit), 2 (Withdraw), 3 (Transfer): 2
    Enter amount to be withdrawn: 250
    +++ Witdraw +++
    Acc num: 33, Amount withdrawn: 265 won
    Saving Account - Name: Emma, Acc num: 33, Balance: 285 won
    +++++
    Transaction success!
    === Bank Information ===
    User list: total 2 users
    Account list: total 2 accounts
    -----
    Normal Account - Name: James, Acc num: 72, Balance: 430 won
    Saving Account - Name: Emma, Acc num: 33, Balance: 285 won
    ==========
    


```python
# test your code: 
bank.transaction(Acc1)
bank.display()
```

    Hi James! What do you want to do? 
    1 (Deposit), 2 (Withdraw), 3 (Transfer): 3
    Enter destination account number to transfer: 33
    Enter amount to be transferred to: 130
    +++ Witdraw +++
    Acc num: 72, Amount withdrawn: 130 won
    Normal Account - Name: James, Acc num: 72, Balance: 300 won
    +++++
    +++ Deposit +++
    Acc num: 33, Amount deposited: 130 won
    Saving Account - Name: Emma, Acc num: 33, Balance: 421 won
    +++++
    Transaction success!
    === Bank Information ===
    User list: total 2 users
    Account list: total 2 accounts
    -----
    Normal Account - Name: James, Acc num: 72, Balance: 300 won
    Saving Account - Name: Emma, Acc num: 33, Balance: 421 won
    ==========
    

## P-4 (10 pt) [File I/O]

파일 이름의 리스트와 타겟 문자열을 입력 받아 **타겟 문자열을 내용에 포함하는 ".txt" 파일들을 찾아내는** 함수 `FindFiles` 함수를 구현하세요. 

* 현재 폴더에 있는 모든 파일의 리스트와 타겟 문자열을 입력 변수로 가집니다. 
  * 이 파일들은 다양한 확장자를 가질 수 있습니다. 
* 파일들 중 **".txt" 확장자를 갖는 파일들**을 파악하고, 
* 해당 파일의 내용을 열어 **타겟 문자열이 포함**되어 있는지 판단합니다.
* **타겟 문자열을 포함한 ".txt" 파일들의 이름의 리스트를 반환**합니다. 

* eclass에 첨부한 "logInfo.txt", "test1.txt", "test2.txt", "test3.txt", "test5.ipynb" 파일을 업로드하여, 현재 폴더의 파일 리스트가 다음과 같이 확인되어야 합니다. (colab 기본환경에서 구현한다고 가정할 때의 결과입니다)
```
import os
file_lst = os.listdir('./')
print(file_lst)
>>>
['.config', 'logInfo.txt', 'test2.txt', 'test3.txt', 'test1.txt', 'test5.ipynb', 'sample_data']
```

실행 결과: 
```
target_str1 = 'com'
target_str2 = 'you'
target_str3 = 'answer'
print(f'txt files including \"{target_str1}\" -> {FindFiles(file_lst,  target_str1)}')
print(f'txt files including \"{target_str2}\" -> {FindFiles(file_lst,  target_str2)}')
print(f'txt files including \"{target_str3}\" -> {FindFiles(file_lst,  target_str3)}')
>>>
txt files including "com" -> ['logInfo.txt', 'test1.txt']
txt files including "you" -> ['test2.txt', 'test3.txt', 'test1.txt']
txt files including "answer" -> ['test2.txt']
```



```python
# upload logInfo.txt, test1.txt, test2.txt, test3.txt, test5.ipynb files
from google.colab import files
_ = files.upload() 
```



     <input type="file" id="files-7785ebdb-bc85-438e-9722-133da0b5241a" name="files[]" multiple disabled
        style="border:none" />
     <output id="result-7785ebdb-bc85-438e-9722-133da0b5241a">
      Upload widget is only available when the cell has been executed in the
      current browser session. Please rerun this cell to enable.
      </output>
      <script>// Copyright 2017 Google LLC
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//      http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

/**
 * @fileoverview Helpers for google.colab Python module.
 */
(function(scope) {
function span(text, styleAttributes = {}) {
  const element = document.createElement('span');
  element.textContent = text;
  for (const key of Object.keys(styleAttributes)) {
    element.style[key] = styleAttributes[key];
  }
  return element;
}

// Max number of bytes which will be uploaded at a time.
const MAX_PAYLOAD_SIZE = 100 * 1024;

function _uploadFiles(inputId, outputId) {
  const steps = uploadFilesStep(inputId, outputId);
  const outputElement = document.getElementById(outputId);
  // Cache steps on the outputElement to make it available for the next call
  // to uploadFilesContinue from Python.
  outputElement.steps = steps;

  return _uploadFilesContinue(outputId);
}

// This is roughly an async generator (not supported in the browser yet),
// where there are multiple asynchronous steps and the Python side is going
// to poll for completion of each step.
// This uses a Promise to block the python side on completion of each step,
// then passes the result of the previous step as the input to the next step.
function _uploadFilesContinue(outputId) {
  const outputElement = document.getElementById(outputId);
  const steps = outputElement.steps;

  const next = steps.next(outputElement.lastPromiseValue);
  return Promise.resolve(next.value.promise).then((value) => {
    // Cache the last promise value to make it available to the next
    // step of the generator.
    outputElement.lastPromiseValue = value;
    return next.value.response;
  });
}

/**
 * Generator function which is called between each async step of the upload
 * process.
 * @param {string} inputId Element ID of the input file picker element.
 * @param {string} outputId Element ID of the output display.
 * @return {!Iterable<!Object>} Iterable of next steps.
 */
function* uploadFilesStep(inputId, outputId) {
  const inputElement = document.getElementById(inputId);
  inputElement.disabled = false;

  const outputElement = document.getElementById(outputId);
  outputElement.innerHTML = '';

  const pickedPromise = new Promise((resolve) => {
    inputElement.addEventListener('change', (e) => {
      resolve(e.target.files);
    });
  });

  const cancel = document.createElement('button');
  inputElement.parentElement.appendChild(cancel);
  cancel.textContent = 'Cancel upload';
  const cancelPromise = new Promise((resolve) => {
    cancel.onclick = () => {
      resolve(null);
    };
  });

  // Wait for the user to pick the files.
  const files = yield {
    promise: Promise.race([pickedPromise, cancelPromise]),
    response: {
      action: 'starting',
    }
  };

  cancel.remove();

  // Disable the input element since further picks are not allowed.
  inputElement.disabled = true;

  if (!files) {
    return {
      response: {
        action: 'complete',
      }
    };
  }

  for (const file of files) {
    const li = document.createElement('li');
    li.append(span(file.name, {fontWeight: 'bold'}));
    li.append(span(
        `(${file.type || 'n/a'}) - ${file.size} bytes, ` +
        `last modified: ${
            file.lastModifiedDate ? file.lastModifiedDate.toLocaleDateString() :
                                    'n/a'} - `));
    const percent = span('0% done');
    li.appendChild(percent);

    outputElement.appendChild(li);

    const fileDataPromise = new Promise((resolve) => {
      const reader = new FileReader();
      reader.onload = (e) => {
        resolve(e.target.result);
      };
      reader.readAsArrayBuffer(file);
    });
    // Wait for the data to be ready.
    let fileData = yield {
      promise: fileDataPromise,
      response: {
        action: 'continue',
      }
    };

    // Use a chunked sending to avoid message size limits. See b/62115660.
    let position = 0;
    do {
      const length = Math.min(fileData.byteLength - position, MAX_PAYLOAD_SIZE);
      const chunk = new Uint8Array(fileData, position, length);
      position += length;

      const base64 = btoa(String.fromCharCode.apply(null, chunk));
      yield {
        response: {
          action: 'append',
          file: file.name,
          data: base64,
        },
      };

      let percentDone = fileData.byteLength === 0 ?
          100 :
          Math.round((position / fileData.byteLength) * 100);
      percent.textContent = `${percentDone}% done`;

    } while (position < fileData.byteLength);
  }

  // All done.
  yield {
    response: {
      action: 'complete',
    }
  };
}

scope.google = scope.google || {};
scope.google.colab = scope.google.colab || {};
scope.google.colab._files = {
  _uploadFiles,
  _uploadFilesContinue,
};
})(self);
</script> 


    Saving logInfo.txt to logInfo.txt
    Saving test5.ipynb to test5.ipynb
    Saving test3.txt to test3.txt
    Saving test2.txt to test2.txt
    Saving test1.txt to test1.txt
    


```python
# check files in current directory
import os
file_lst = os.listdir('./')
print(file_lst)
```

    ['.config', 'test1.txt', 'test5.ipynb', 'test3.txt', 'test2.txt', 'logInfo.txt', 'sample_data']
    


```python
# P-4
# your code here:

def FindFiles(lst,target_str):
  txt_lst = list(filter(lambda x: x[-4:]=='.txt',lst))
  result=[]
  for txt_file in txt_lst:
    with open(txt_file, mode='r') as f:
      if target_str in f.read().lower():
        result.append(txt_file)
  return result

```


```python
# test your code:
target_str1 = 'com'
target_str2 = 'you'
target_str3 = 'answer'
print(f'txt files including \"{target_str1}\" -> {FindFiles(file_lst,  target_str1)}')
print(f'txt files including \"{target_str2}\" -> {FindFiles(file_lst,  target_str2)}')
print(f'txt files including \"{target_str3}\" -> {FindFiles(file_lst,  target_str3)}')
```

    txt files including "com" -> ['test1.txt', 'logInfo.txt']
    txt files including "you" -> ['test1.txt', 'test3.txt', 'test2.txt']
    txt files including "answer" -> ['test2.txt']
    

## P-5 (15 pt) [Regular Expression]

정규표현식 (regular expression)을 사용하여 다음의 코드를 구현하세요. 

**(a) [7.5 pt]** "logInfo.txt" 파일 내에 있는 텍스트를 읽어들여 **".com" 도메인을 가진 이메일 주소를 모두** 찾습니다. 
* 이메일 주소는 @ 앞부분은 알파벳소문자와 숫자를 포함할 수 있고 (공백없이), @ 뒷부분에는 알파벳 소문자로만 이루어져 있으며, 마지막에 ".com", ".edu", ".net"과 같이 도메인으로 구성되어 있습니다. 
* 그 중 ".com" 도메인을 가진 이메일 주소를 모두 찾아 모은 리스트 `com_list` 를 출력합니다. 

실행 결과:
```
print(com_list)
>>>
['cbkwcq@nzfwhmfsiwk.com', 'hitpzg@dqfqbihwkcln.com', 'xvjq@ozpoyvodxrcw.com', 'xvjq@ozpoyvodxrcw.com']
```


```python
# P-5 (a)
# your code here:
import re

with open("logInfo.txt",mode='r') as f:
  txt = f.read()
com_list = re.findall(r'\w+@[a-z]+\.com',txt)
print(com_list)
```

    ['cbkwcq@nzfwhmfsiwk.com', 'hitpzg@dqfqbihwkcln.com', 'xvjq@ozpoyvodxrcw.com', 'xvjq@ozpoyvodxrcw.com']
    

**(b) [7.5 pt]** 사용자로부터 입력받은 **비밀번호의 유효성을 검증**하여 True/False를 알려주는 코드를 구현하세요. 

* 사용자로부터 비밀번호를 입력받습니다. 
* 유효한 비밀번호는 다음의 조건을 만족해야 합니다. 
  * 대문자가 한 개 이상, 소문자가 한 개 이상, 숫자가 한 개 이상 포함되어야 합니다. 
  * 다음의 특수문자 `$#@*!` 중 한 개 이상 포함되어야 합니다. 
  * 총 길이는 8글자 이상 15글자 이하여야 합니다. 
* 유효성을 체크하여 Valid password인지 Invalid password인지 출렵합니다. 

실행 결과: 
```
Input your password: >>> ABCde12345
Invalid password!
```
```
Input your password: >>> ABCde12345@!
Valid password!
```
```
Input your password: bcde12345@!
Invalid password!
```
```
Input your password: >>> bc12345*E
Valid password!
```



```python
# P-5 (b)
import re 
# get password from user
passwd = input('Input your password: ')

# your code here
check1 = len(re.findall(r'[A-Z]',passwd)) >= 1
check2 = len(re.findall(r'[a-z]',passwd)) >= 1
check3 = len(re.findall(r'[0-9]',passwd)) >= 1
check4 = len(re.findall(r'[$#@*!]',passwd)) >= 1
check5 = 8 <= len(passwd) <= 15
if all([check1,check2,check3,check4,check5]):
  print('Valid password!')
else:
  print('Invalid password!')


```

    Input your password: bc12345*E
    Valid password!
    

## P-6 (20 pt) [NumPy/Pandas]

**(a) [5 pt]** 임의의 정수를 입력받아 랜덤 배열 ndarray를 생성하는 함수 `create_randarr` 함수를 구현하세요. 

* 임의의 정수 $n$을 입력변수로 가집니다. (자연수라고 가정합니다) 
* $0$과 $123$ 사이의 랜덤 정수를 $4n^2$개 만큼 뽑아 $n \times 4n$ 크기의 ndarray를 만들어 반환합니다. 

실행 결과: (예시)
```
my_arr = create_randarr(3)
print(my_arr)
>>>
[[  6  24  65 120  18 115  69  76 102  99 117  64]
 [ 71  85  53  44  24  49 107 106  59  76  67  41]
 [ 61  40   5  62   1  26  71  20  72  13  63  21]]
```

**(b) [5 pt]** (a)에서 만든 배열의 부분배열을 만들고 계산하는 코드를 구현하세요. 

* 홀수번째 row와 짝수번째 column만을 선택하여 부분 배열을 만듭니다. 
* 부분 배열의 row에 대하여 평균과 표준편차를 계산하여 출력합니다. (첫번째 축 방향으로 연산을 수행)

실행 결과: (예시)
```
Subarray: 
[[ 24 120 115  76  99  64]
 [ 40  62  26  20  13  21]]
Along row: mean [32.  91.  70.5 48.  56.  42.5]
Along row: std [ 8.  29.  44.5 28.  43.  21.5]
```



```python
# P-6 (a)
import numpy as np

# your code here:
def create_randarr(n):
  size = 4*n*n
  return np.random.randint(0,124,size).reshape(n, 4*n)


```


```python
# test your code:
my_arr = create_randarr(3)
print(my_arr)
```

    [[105  38 112  63   1 105  65 105  24  44   4  68]
     [ 45  37  24  89  46  71  33  56  40 118  73 114]
     [ 79  44  52  67  97   7  82  62   4  41  20  35]]
    


```python
# P-6 (b)
# your code here:
Subarray = my_arr[0::2,1::2]
print('Subarray:\n',Subarray)
print('Along row: mean',Subarray.mean(axis=0))
print('Along row: std',Subarray.std(axis=0))

```

    Subarray:
     [[ 38  63 105 105  44  68]
     [ 44  67   7  62  41  35]]
    Along row: mean [41.  65.  56.  83.5 42.5 51.5]
    Along row: std [ 3.   2.  49.  21.5  1.5 16.5]
    

**(c) [5 pt]** 주어진 시험 데이터 `exam_data`을 활용하여 아래와 같은 DataFrame을 생성하세요. 

실행 결과:
```
print(exam_df)
>>>
          name  score  attempts P/F
S1      Andrew     42         1   P
S2   Katherine     90         3   F
S3       David     26         2   P
S4       James      0         1   F
S5       Emily     79         3   F
S6     Michael     20         3   P
S7     Matthew     55         1   P
S8       Laura      0         1   F
S9       Kevin     98         2   F
S10       Coby     66         1   P
```

**(d) [5 pt]** `exam_df`에서 'P/F'의 값이 'P'인 row들을 모아 출력하세요. 

실행 결과:
```
        name  score  attempts P/F
S1    Andrew     42         1   P
S3     David     26         2   P
S6   Michael     20         3   P
S7   Matthew     55         1   P
S10     Coby     66         1   P
``` 



```python
from IPython.core.oinspect import indent
# P-6 (c)
import pandas as pd
exam_data  = {'name': ['Andrew', 'Katherine', 'David', 'James', 'Emily', 'Michael', 'Matthew', 'Laura', 'Kevin', 'Coby'],
        'score': [42, 90, 26, 0, 79, 20, 55, 0, 98, 66],
        'attempts' : [1, 3, 2, 1, 3, 3, 1, 1, 2, 1],
        'P/F': ['P', 'F', 'P', 'F', 'F', 'P', 'P', 'F', 'F', 'P']}

# your code here:
index = ['S'+str(i+1) for i in range(10)]
column = list(exam_data.keys())
data = list(exam_data.values())
data = np.array(data).T

exam_df = pd.DataFrame(data,index,column)

print(exam_df)

```

              name score attempts P/F
    S1      Andrew    42        1   P
    S2   Katherine    90        3   F
    S3       David    26        2   P
    S4       James     0        1   F
    S5       Emily    79        3   F
    S6     Michael    20        3   P
    S7     Matthew    55        1   P
    S8       Laura     0        1   F
    S9       Kevin    98        2   F
    S10       Coby    66        1   P
    


```python
# P-6 (d)
print('Who passed the exam? ')

# your code here:
new_df = exam_df[ exam_df['P/F'] == 'P' ]
print(new_df)

```

    Who passed the exam? 
            name score attempts P/F
    S1    Andrew    42        1   P
    S3     David    26        2   P
    S6   Michael    20        3   P
    S7   Matthew    55        1   P
    S10     Coby    66        1   P
    

## P-7 (10 pt) [Random]

랜덤 모듈을 사용하여 랜덤한 **주사위 실행 결과**를 만드는 함수 `RollDice` 함수를 구현하세요. 
* 주사위를 던지는 횟수를 입력변수로 가집니다. 
* 주사위는 1~6 사이의 정수가 uniform random하게 나오는 일반적인 주사위라고 가정합니다. 
* 주사위를 실행하여 관찰된 숫자들로 구성된 리스트를 반환합니다.

실행 결과:
```
print(RollDice(3))
print(RollDice(5))
print(RollDice(10))
>>>
[5, 6, 4]
[3, 4, 1, 6, 3]
[3, 6, 3, 4, 3, 5, 3, 4, 5, 3]
```





```python
# P-7
import random

# your code here:
def RollDice(n):
  lst=[]
  for i in range(n):
    lst.append(random.randint(1,6))
  return lst

```


```python
# test your code:
print(RollDice(3))
print(RollDice(5))
print(RollDice(10))
```

    [6, 5, 1]
    [5, 3, 6, 6, 6]
    [6, 5, 2, 3, 6, 5, 5, 4, 1, 6]
    
