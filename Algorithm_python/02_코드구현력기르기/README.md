# 🍒 1. K번째 약수

### 🍕 내가 작성한 코드

```python
n, k = input().split()
n = int(n)
k = int(k)
a = []

for i in range(1, n+1):
    if n%i==0:
        a.append(i)

if len(a)<k:
    print("-1")
else:
    print(a[k-1])
```

### 🍕 정답 코드

```python
n, k=map(int, input().split())
cnt = 0
for i in range(1, n+1): #1부터 n까지 반복문 돌리기
    if n%1==0:
        cnt+=1 #카운트 개수 세기
    if cnt==k:
        print(i)
        break
else:
    print(-1)#앞에 문이 정상적으로 끝나면 이 문을 실행함(약수를 발견하지 못함)
```

### 📝 배운점

1. 입력받은 2개의 정수를 map 함수를 이용해서 한번에 int형으로 변환해주기
2. 약수를 찾으면서 동시에 약수의 개수를 count하여 불필요한 계산을 하지 않고 바로 답을 출려하도록 코드 작성(cnt 변수를 사용하여 k번째 약수가 나오면 바로 출력)
    - **for else 구문**을 활용하여 앞에 코드가 정상적으로 끝나면 else문이 실행되도록 함
    - for else 구문 예시
    
    ```python
    for i in range(1,11)
    	print(i)
    	if i==5:
    		break
    else:
    	print(11)
    #for else 구문: 정상적으로 동작하면 else까지 출력함, 중간에 멈추게 되면 else를 출력하지 않음
    ```
    

# 🍒 2. K번째 수

### 🍕 정답 코드

```python
T = int(input()) # input은 무조건 string으로 읽어오고, 이것을 Int로 변경해줌

for t in range(T): #케이스 개수만큼 반복 수행
    n, s, e, k = map(int, input().split())
    a=list(map(int,input().split()))
    a=a[s-1:e] #a[1:5]는 1번 인덱스부터 4번인덱스까지 출력
    a.sort()
    print("#%d %d" %(t+1,a[k-1])) #출력방법 %d는 숫자를 출력!
```

### 📝 배운점

1. 리스트 형식의 입력 값 받아오는 방법

`N = N.append(int(input().split()))`

이렇게 했는데 계속 `int() argument must be a string, a bytes-like object or a number, not 'list'` 이렇게 오류가 났다. 받아온 배열 전체를 int로 한번에 변환해주려고 해서 오류가 났다. 하나하나 int형으로 변경해줘야하니 map 함수를 사용하는 점 주의!

```python
a=list(map(int,input().split()))
```

2. a[n:m] 배열 slice하기

배열 n번째부터 m번째 까지가 아닌 n번째부터 m-1번째 까지라는 사실에 유의!

3. %를 사용한 출력방법

```python
print(”#%d %d” %(1,2))
# 1 2
```

%d는 정수 표기, %s는 문자열 표기, %f는 실수 표기


# 🍒 3. K번째 큰 수

### 🍕 정답코드
```python
n, k=map(int, input().split())
a = list(map(int, input().split()))
b = []
#중복을 제거하는 자료구조 set
res=set() #5를 여러번 넣어도 딱 한번만 들어간다
for i in range(n):
    for j in range(i+1, n):
        for m in range(j+1, n):
            res.add(a[i]+a[j]+a[m]) #set자료는 add, 중복을 제거하면서 입력이 됨

#set은 sort개념이 없음, list로 다시 변경해야함
res=list(res)
res.sort(reverse=True) #내림차순
print(res[k-1])
```

### 📝 배운점

1. index 값만 추출하면 되는데 원소의 값까지 한번에 추출하려고 해서 답을 작성하기가 어려웠음… 단계를 나눠서 생각하기! Index 번호부터
2. set의 개념
    - 집합의 의미를 가짐, 순서가 없고 중복을 허용하지 않는다.
    - 반복 가능하고, 가변적이며, 중복요소가 없고, 정렬되지 않은 데이터 타입
    - set() 함수를 통해 set으로 변경해줌
    - 원소를 추가할 때 add, 삭제할 때는 remove, 추가할 때 update()
    - 집합 연산이 가능해서 교집합 & , 합집합 | , 차집합- 연산이 가능
    - sort 개념이 없음, sort 개념을 넣고싶다면 list로 변경할 것

3. sort 내림차순으로 정렬할 때는

```python
a.sort(reverse=True)
```

# 4-0. 🍒 [선수지식] 최솟값 구하기

### 🍕 내가 짠 코드

```python
# 최솟값 구하기(me)
arr=[5,3,7,9,2,5,2,6]
arrMin = min(arr)
print(arrMin)
```

### 🍕 정답 코드1

```python
# 최솟값 구하기
arr=[5,3,7,9,2,5,2,6]
arrMin = float('inf') # 가장 큰 값을 무한대로 설정
for i in range(len(arr)):
    if arr[i]<arrMin:
        arrMin = arr[i]
        
print(arrMin)
```

### 🍕 정답 코드2

```python
# 최솟값 구하기
arr=[5,3,7,9,2,5,2,6]
arrMin = arr[0] # 처음값을 설정해도 괜찮음
for i in range(1, len(arr)):
    if arr[i]<arrMin:
        arrMin = arr[i]
        
print(arrMin)
```

### 🍕 정답 코드3

```python
# 최솟값 구하기
arr=[5,3,7,9,2,5,2,6]
arrMin = float('inf') # 가장 큰 값을 무한대로 설정
for x in arr:
    if x<arrMin:
        arrMin = x
        
print(arrMin)
```

# 🍒 4. 대표값

### 🍕 내가 짠 코드

```python
# 대표값 구하기
n = int(input())
scores = list(map(int, input().split()))
Avg=sum(scores)/len(scores) 
minDiff=float('inf')
a=[]

for index, value in enumerate(scores):
    print(index, value, value-scoresAvg)
```

enumerate까지 가져왔는데, 평균값과 학생의 점수 차이를 어디에다가 저장해야할지 몰라서 문제 해결 못함…

### 🍕 정답 코드

```python
# 대표값 구하기
n = int(input())
a = list(map(int, input().split()))
ave=int(sum(a)/n+0.5) #반올림
min=2147000000 #정수형의 가장 큰 값

for idx, x in enumerate(a):
    tmp=abs(x-avg)
    if tmp<min:
        min=tmp
        score=x #점수가 같은 경우가 있기ㄷ 때문에 점수도 저장해놔야함
        res=idx+1 #index는 0번부터 시작하기 때문
    elif tmp==min: ##점수차이가 같은 값이 하나 더 나타난다면
        if x>score: #이전에 발견한 학생의 점수보다 더 높은 점수라면(같은 점수가 또 있다면 여기서 걸러짐 >=하면 안됨!!뒤에점수로 됨)
            score=x #지금 발견한 학생의 점수를 score에 대입
            res=idx+1 #지금 발견한 학생의 index번호를 저장
            
print(ave,res)
```

### 📝 배운점

1. 평균값 구할 때
    - round값 이용해서 반올림x
        - 소수 첫째자리, 둘째자리 반올림 하는 법
            
            `round(1.5)` `round(1.45,2)` 인자 넣어주기
            
        - round는 round_half_even방식을 택하기 떄문에 우리가 알고 있는 기존의 반올림과 다름, 반올림 할 때 정확하게 반절의 값이면 짝수값과 가까운 값으로 반환함
        - 무조건 0.5를 더해서 int형으로 변환하는 방식으로 반올림
            
            ```python
            int(a+0.5)
            ```
            
    - 학생 전체 수 구할 때 len(a) 가 아닌 기존에 받아온 n을 이용해서 사용

2. index와 value가 둘다 필요할 때는 enumerate를 사용하자
    - 평균과 점수 차이가 필요할 때는 함수 내부에서 선언해주자

3. 최솟값 구하기
    - 우선 기본 설정 값을 아주 큰수(inf, 2147000000)로 해놓고, 그 큰 수보다 작은 수가 있다면 그 수를 작은 값으로 변경
        - 2147000000이 가장 큰 정수인 이유는?
            - 2147483647(2^31-1)
            - int형은 크기가 4byte의 크기를 가지고 있는 정수형 자료
            - 4byte = 32bit이기에 2^32개의 숫자를 표현할 수 있으며, 음수까지는 표현할 수 있기에 2^31개, 0도 양수처리 되므로 최종적으로 int형은 -2^31~2^31-1의 범위를 가진다

# 🍒 5. 정다면체

두 개의 정 N면체와 정 M면체의 두 개의 주사위를 던져서 나올 수 있는 눈의 합 중 가장 확률이 높은 숫자를 출력하는 프로그램을 작성하세요.
정답이 여러 개일 경우 오름차순으로 출력합니다.

▣ 입력설명
첫 번째 줄에는 자연수 N과 M이 주어집니다. N과 M은 4, 6, 8, 12, 20 중의 하나입니다.

▣ 출력설명
첫 번째 줄에 답을 출력합니다.

▣ 입력예제 1
46

▣ 출력예제 1
567

### 🍕 내가 짠 코드

```python
a,b = map(int, input().split())
cnt = list(range(1, a+b+1))
cnt = [0 for i in range(a+b+1)]
for i in range(1, a+1):
    for j in range(1, b+1):
        cnt[i+j]+=1

print(cnt)
print(max(cnt))

max = 0
res = []

for index, value in enumerate(cnt):
    print(index, value)
    if value>max:
        max = value
    elif max==value:
        
print(res)
```

### 🍕 정답 코드

```python
#1. input값 불러오기
n,m = map(int, input().split())

#2. cnt 배열 0으로 차있는거 만들기
cnt = [0]*(n+m+3) #그냥 넉넉하게 3더함

#3. n+m의 모든 경우의 수 구해서 cnt배열에 넣기_이중for문
for i in range(1, n+1):
    for j in range(1, m+1):
        cnt[i+j]+=1

#4. 빈도 횟수(cnt)의 최대값 구하기_for문
max=0
for i in range(n+m+1):
    if cnt[i]>max:
        max = cnt[i]

#5. 여러개의 최대값 구하기
for i in range(n+m+1):
    if cnt[i]==max:
        print(i, end=' ')
```

### 3. 배운점 📝
cnt배열에 한번에 넣을 생각을 못했따…

for 문 여러개 써서 구할 생각도 못했다..

단순하게 생각하자..

# 🍒 6. 자릿수의 합

N개의 자연수가 입력되면 각 자연수의 자릿수의 합을 구하고, 그 합이 최대인 자연수를 출력
하는 프로그램을 작성하세요. 각 자연수의 자릿수의 합을 구하는 함수를 def digit_sum(x)를
꼭 작성해서 프로그래밍 하세요.

▣ 입력설명
첫 줄에 자연수의 개수 N(3<=N<=100)이 주어지고, 그 다음 줄에 N개의 자연수가 주어진다.
각 자연수의 크기는 10,000,000를 넘지 않는다.

▣ 출력설명
자릿수의 합이 최대인 자연수를 출력한다. 자릿수의 합이 같을 경우 입력순으로 먼저인 숫자
를 출력합니다.

▣ 입력예제 1
3
125 15232 97

▣ 출력예제 1
97

### 🍕 내가 짠 코드

```python
N = int(input())
a = list(map(int, input().split()))

b=[]
for i in a:
    b.append(str(i))
print(b)

sum=[]
for i in b:
    for j in range(len(i)):
        sum[i]+=i[j]
print(sum)
```

`TypeError: list indices must be integers or slices, not str`

### 🍕 답안코드1

```python
#input값으로 입력값 받아오기(input, list)
n= int(input())
a = list(map(int, input().split()))

#각자리 수 합하는 함수만들기
def digit_sum(x):
    #while문으로 10으로 계속 나눠서 나머지값들 합해서 값 return하기
    sum=0
    while x>0:
        sum = sum+x%10
        x=x//10
        return sum

#list배열에 for문으로 하나하나 함수로 접근해서 가장 큰 최댓값 구하기
max=0
for x in a:
    tot=digit_sum(x)
    if tot>max:
        max=tot
        res=x
print(res)
```

### 🍕 답안코드2

```python
#input값으로 입력값 받아오기
n = int(input())

#list으로 배열값 받아오기
a=list(map(int, input().split()))

#각자리수 함하는 함수 만들기
def digit_sum(x):
    #while문으로 str함수 쪼개서 각자리 수 더한값 리턴하기
    sum=0
    for i in str(x):
        sum=sum+int(i) #왜 여기가 int임? 아 i값 자체가 str 의 i번쨰 문자열임...
        return sum
#for문으로 배열 하나하나 접근해서 최댓값 구하기
max=0
for x in a:
    tot=digit_sum(x)
    if max<tot:
        max=tot
        res=x
print(res)
```
