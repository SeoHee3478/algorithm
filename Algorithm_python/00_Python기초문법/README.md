# 🍒1. 변수와 출력함수

## 🍕변수명 정하기

1) 영문과 숫자, _로 이루어진다

2) 대소문자로 구분한다.

3) 문자나, _로 시작한다.

4) 특수문자를 사용하면 안된다.(&, % 등)

5) 키워드를 사용하면 안된다.(if, for 등)

## 🍕한꺼번에 변수를 선언하고 값을 할당하는 방법

```python
a, b, c = 3,2,1
```

## 🍕값 교환

```python
a, b = 10, 20
print(a, b) // 10 20
a, b = b, a 
print(a, b) // 20 10
```

## 🍕변수 타입

```python
a = 12345
print(a) # 12345
print(type(a)) #int (a의 타입이 출력되는 함수 type())

a = 12.12345
print(a) # 12.12345
print(type(a)) #float (실수형, 8바이트까지만 출력되므로 소수점이 끝까지 나오지 않음)

a = 'student' #홑따옴표, 쌍따옴표 다 같음
print(a)
print(type(a)) #str (문자형)

 
```

## 🍕출력방식

```python
print("number")
a,b,c = 1,2,3
print(a,b,c) # 1 2 3 (자동적으로 띄어쓰기 되어서 출력됨)
print("number", a,b,c) # number 1 2 3
print(a,b,c, sep=', ') # 1, 2, 3 (3개의 변수를 sep으로 구분해주는 것임!)
print(a,b,c, sep=',') # 1,2,3
print(a,b,c, sep='\n')
# 1
# 2
# 3
print(a) # print에는 기본적으로 \n값이 들어있음
print(a, end=' ')
print(b, end=' ')
print(c)
# 1 2 3 이렇게 출력 됨!(end=' '는 print에 기본적으로 들어있는 \n을 없애줌)
```
<br/>

-----

<br/>

# 🍒2. 변수 입력과 연산자

```python
a = input("숫자를 입력하세요 : ")
print(a) #입력받은 숫자를 출력해줌

a, b = input("숫자를 입력하세요 : ").split() #띄워쓰기로 분리해서 입력한 값을 받음
a = int(a) # str형-> int형으로 변경
b = int(b)

a,b = map(int, input("숫자를 입력하세요 : ").split())
#map함수를 이용해서 a, b 한번에 int형으로 변경하기

print(a/b) #나눈값
print(a//b) # 몫
print(a%b) #나머지
print(a**b) #거듭제곱 a의 b제곱의 값 출력

a = 4.3
b = 5
c = a + b
print(type(c)) #c는 float 실수형으로 바뀜, 타입이 다른 것끼리 연산하면 더 큰 범위의 형으로 변환!

```

<br/>

-----

<br/>

# 🍒3. 조건문 if(분기, 중첩)

```python
if x==7:
	print("Lucky") 
#Python에서 띄어쓰기도 문법이다. 기본적으로 4칸 띄어써야 if문 안에 속함

[중첩]
x = 15
if x>=10:
	if x%2==1:
		print("10이상의 홀수")

[논리연산자로 중첩 조건문 사용]
if x>0 and x<10:
	print("10보다 작은 자연수")

[부등호 중첩해서 사용, python만 가능]
if 0<x<10:
	print("10보다 작은 자연수")

[분기문]
if x>0:
	print("양수")
else:
	print("음수")

[다중 If문]
if x>=90:
	print('A')
elif x>=80:
	print('B')
elif x>=70:
	print('C')
elif x>=60:
	print('D')
else:
	print('F')

```

<br/>

-----

<br/>

# 🍒4. 반복문(for, while)

```python
[for문]
a = range(10) #range는 순차적으로 정수 리스트를 만드는 것
print(list(a))
#[0,1,2,3,4,5,6,7,8,9]

a = range(1, 11)
print(list(a))
#[1,2,3,4,5,6,7,8,9,10]

for i in range(10):
	print("hello") # hello를 10번 출력함
	print(i) #0부터 9까지 출력함

for i in range(10,0,-1):
	print(i) #10부터 0까지 1씩 작아지면서 출력

for i in range(10,0,-2):
	print(i) #10부터 0까지 2씩 작아지면서 출력

[while문]
i = 1
while i<=10:
	print(i)
	i=i+1
#1부터 10까지 증가하면서 출력

i=10
while i>=1:
	print(i)
	i=i-i
#10부터 1까지 감소하면서 출력

[break문]
while True:
	print(i)
	if i==10: #10이 되면 무한 반복을 멈추게 함
		break
	i+=1 

for i in range(1,11):
	if i%2==0:
		continue #짝수는 그냥 지나감
	print(i)
#홀수만 출력함

for i in range(1,11)
	print(i)
	if i==5:
		break
else:
	print(11)
#for else 구문: 정상적으로 동작하면 else까지 출력함, 중간에 멈추게 되면 else를 출력하지 않음

```

<br/>

-----

<br/>

# 🍒5. 반복문을 이용한 문제 풀이

<aside>
📌 1) 1부터 N까지 홀수 출력하기<br/>
2) 1부터 N까지 합 구하기<br/>
3) N의 약수 출력하기<br/>

</aside>

## 🍕1) 1부터 N까지 홀수 출력하기

```python
n = int(input())
for i in range(1, n+1): #1부터 n까지
	if i%2==1:
		print(i)
```

## 🍕2) 1부터 N까지의 합 구하기

```python
n = int(input())
sum = 0
for i in range(1, n+1):
	sum = sum+i
print(sum)
```

## 🍕3) N의 약수 출력하기

```python
n = int(input())
for i in range(1, n+1):
	if n%i==0: #n을 나누어 떨어지게 하는 숫자를 약수라고 함!
		print(i, end=' ') #한 칸 띄어서 출력하기
```

# 🍒6. 중첩 반복문(2중 for 문)

```python
for i in range(5):
	for j in range(5):
		print(j, end=' ')
	print()

# 0 1 2 3 4
# 0 1 2 3 4
# 0 1 2 3 4
# 0 1 2 3 4
# 0 1 2 3 4

for i in range(5):
	for j in range(5):
		print("*", end=' ')
	print()
# * * * * *
# * * * * *
# * * * * *
# * * * * *
# * * * * *

for i in range(5):
	for j in range(i+1):
		print("*", end=' ')
	print()
# *
# * *
# * * *
# * * * *
# * * * * *

for i in range(5):
	for j in range(5-i):
		print("*", end=' ')
	print()
# * * * * *
# * * * *
# * * *
# * *
# *
```

# 🍒7. 문자열과 내장 함수

## 🍕upper()함수와 lower()함수
```python
msg = "It is Time"
print(msg.upper()) # 모든 문자를 대문자화 시키는 upper
# IT IS TIME
print(msg)
# It is Time (원본은 그대로)
print(msg.lower()) # 문자를 소문자화 시키는 것
# it is time

tmp = msg.upper()
print(tmp)
#IT IS TIME
```

## 🍕find()함수와 count()함수
```python
msg = "It is Time"
print(tmp.find('T')) # find는 T가 들어있는 배열의 인덱스 번호를 출력해줌
# 1
print(tmp.count('T')) # 대문자 T가 몇개 들어있는지 세주는 함수
# 2
print(msg)
# It is Time
```

## 🍕[n:m]와 len()함수
```python
msg = "It is Time"
print(msg[:2]) # 0번부터 2번 전까지 = 0 번부터 1번까지
# It
print(msg[3:5]) # 3, 4만 출력
# is

print(len(msg)) # 문자열의 길이를 출력해주는 것
# 10
```

## 🍕for문으로 문자 하나씩 접근하기
```python
msg = "It is Time"
for i in range(len(msg)):
	print(msg[i], end=' ') #문자열에 있는 문자 하나하나에 접근
# I t  i s  T i m e 

for x in msg:
	print(x, end=' ') # x가 문자열 하나하나를 접근한다
print()
# I t  i s  T i m e 
```

## 🍕isupper()함수와 islower()함수
```python
msg = "It is Time"
for x in msg:
	if x.isupper(): #x가 대문자이면 참
		print(x, end=' ')
print()
#I T (대문자만 출력해준 것)

for x in msg:
	if x.islower(): #x가 소문자이면 참
		print(x, end=' ')
print()
# t i s i m e
```

## 🍕isalpha()함수와 ord()함수, chr()함수
```python
msg = "It is Time"
for x in msg:
	if x.isalpha(): #x가 알파벳일 때 참, 공백은 참이 아님
		print(x, end=' ')
print()
#ItisTime

tmp='AZ'
for x in tmp:
	print(ord(x))#아스키 넘버를 출력해주는 것 (A: 65, Z:90)

tmp='az'
for x in tmp:
	print(ord(x))#아스키 넘버를 출력해주는 것 (a: 97, z:122)

tmp=66
print(chr(tmp)) # 문자열로 변환
# A
```
