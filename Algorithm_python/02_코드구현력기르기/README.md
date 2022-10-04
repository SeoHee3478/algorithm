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
