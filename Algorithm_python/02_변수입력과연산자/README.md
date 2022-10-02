# 2. 변수 입력과 연산자

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
