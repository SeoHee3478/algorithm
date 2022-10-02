# 1. 변수와 출력함수

## 변수명 정하기

1) 영문과 숫자, _로 이루어진다

2) 대소문자로 구분한다.

3) 문자나, _로 시작한다.

4) 특수문자를 사용하면 안된다.(&, % 등)

5) 키워드를 사용하면 안된다.(if, for 등)

### 한꺼번에 변수를 선언하고 값을 할당하는 방법

```python
a, b, c = 3,2,1
```

### 값 교환

```python
a, b = 10, 20
print(a, b) // 10 20
a, b = b, a 
print(a, b) // 20 10
```

### 변수 타입

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

### 출력방식
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
