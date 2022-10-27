# 1. 회문 문자열 검사


N개의 문자열 데이터를 입력받아 앞에서 읽을 때나 뒤에서 읽을 때나 같은 경우(회문 문자열) 이면 YES를 출력하고 회문 문자열이 아니면 NO를 출력하는 프로그램을 작성한다.
단 회문을 검사할 때 대소문자를 구분하지 않습니다.


```python
n=int(input())
for i in range(n):
	s=input()
	s=s.upper()
	size=len(s)
	for j in range(size//2):
			if s[j]!=s[-1-j]:
					print("#%d NO" %(i+1))
					break
	else:
			print("#%d YES" %(i+1))
```
1. 대소문자 구분 없는 문자는 아예 그냥 대문자로 받아올 것 upper함수를 이용해서!
2. 문자열 접근을 -1, -2로도 할 수 있다…
3. for else 구문
4. s[::-1] 문자열을 reverse시켜줌

# 2. 숫자만 추출

문자와 숫자가 섞여있는 문자열이 주어지면 그 중 숫자만 추출하여 그 순서대로 자연수를 만 듭니다. 만들어진 자연수와 그 자연수의 약수 개수를 출력합니다.
만약 “t0e0a1c2h0er”에서 숫자만 추출하면 0, 0, 1, 2, 0이고 이것을 자연수를 만들면 120이 됩니다.즉첫자리0은자연수화할때무시합니다. 출력은120를출력하고,다음줄에120 의 약수의 개수를 출력하면 됩니다.
추출하여 만들어지는 자연수는 100,000,000을 넘지 않습니다.

```python
s = input()

res=0
for x in s:
    if x.isdecimal():
        res=res*10+int(x)
cnt=0
for i in range(0, res+1):
    if res%i==0:
        cnt+=1
print(cmt)
```

isdecimal 0~9 숫자

isdigit 알파벳이 아닌 숫자 추출(2^2)도 가능

1) string 문자열 받아오기

2) 문자열 하나씩 for문으로 돌면서 원소가 0~9의 숫자인지 확인하고, 맞다면 계속 10씩 곱해줘서 자연수 만들어주기

3) 약수 구하기 위해서 추출된 값을 1부터 추출된 값까지 for문으로 돌면서 

나누어 떨어지는 수가 있으면 약수의 개수 추가하기


op

# 3. 카드 역배치
1부터 20까지 숫자가 하나씩 쓰인 20장의 카드가 아래 그림과 같이 오름차순으로 한 줄로 놓 여있다. 각 카드의 위치는 카드 위에 적힌 숫자와 같이 1부터 20까지로 나타낸다.

이제 여러분은 다음과 같은 규칙으로 카드의 위치를 바꾼다: 구간 [a, b] (단, 1 ≤ a ≤ b ≤ 20)가 주어지면 위치 a부터 위치 b까지의 카드를 현재의 역순으로 놓는다.
예를 들어, 현재 카드가 놓인 순서가 위의 그림과 같고 구간이 [5, 10]으로 주어진다면, 위치 5부터 위치 10까지의 카드 5, 6, 7, 8, 9, 10을 역순으로 하여 10, 9, 8, 7, 6, 5로 놓는다. 이제 전체 카드가 놓인 순서는 아래 그림과 같다.

이 상태에서 구간 [9, 13]이 다시 주어진다면, 위치 9부터 위치 13까지의 카드 6, 5, 11, 12, 13을 역순으로 하여 13, 12, 11, 5, 6으로 놓는다. 이제 전체 카드가 놓인 순서는 아래 그림 과 같다.

오름차순으로 한 줄로 놓여있는 20장의 카드에 대해 10개의 구간이 주어지면, 주어진 구간의 순서대로 위의 규칙에 따라 순서를 뒤집는 작업을 연속해서 처리한 뒤 마지막 카드들의 배치 를 구하는 프로그램을 작성하시오.


```python
a = list(range(21)) #1부터 21까지 값이 채워진 배열이 새로 생성됨

for _ in range(10): #- 사용시 변수 값 없이 반복할 수 있음
    n1,n2=map(int, input().split())
    center=n2-n1
    for j in range((n2-n1+1)//2): #범위 주의하기
        a[n1+j],a[n2-j]=a[n2-j],a[n1+j]
    
a.pop(0) #0번 인덱스 pop하기    
for x in a:
    print(x, end=' ')
```

swap

a,b = b,a

# 4. 두 리스트 합치기

오름차순으로 정렬이 된 두 리스트가 주어지면 두 리스트를 오름차순으로 합쳐 출력하는 프로 그램을 작성하세요.

```python
n=input()
nList=list(map(int, input().split()))
m=input()
mList=list(map(int,input().split()))

new=[]
new=nList+mList
new.sort()
print(new)
```

sort를 쓰게 되면 8개의 자료구조 이므로 8log8

정렬이 이미 되어있는 것을 활용하면 n번만에 확인할 수 있으므로 이걸로 할 것

1. 두 지점을 가르키는 포인트 변수가 필요함
2. p1 → a[0], p2→b[0]
3. a[p1]과 a[p2] 중에 작은 값을 c 배열에 추가
4. 그리고 a배열을 다쓰고 b배열만 남으면 남은 b배열을 슬라이스해서 배열 뒤에 붙이기

```python
n=int(input())
a=list(map(int, input().split()))
m=int(input())
b=list(map(int,input().split()))

print(a,b)

# 두 지점을 가르키는 포인트 변수, p1 → a[0], p2→b[0]
p1=0
p2=0
c=[]

# a[p1]과 a[p2] 중에 작은 값을 c 배열에 추가
while p1<n and p2<m: #둘중에 하나 원소 순회가 다 끝나면
    if a[p1]<=b[p2]:
        c.append(a[p1])
        p1+=1
    else: 
        c.append(b[p2])
        p2+=1
# a배열을 다쓰고 b배열만 남으면 남은 b배열을 슬라이스해서 배열 뒤에 붙이기
if p1<n:
    c=c+a[p1:]
if p2<m:
    c=c+b[p2:]

for x in c:
    print(x, end=' ')
```

# 5. 수들의 합

N개의 수로 된 수열 A[1], A[2], ..., A[N] 이 있다. 이 수열의 i번째 수부터 j번째 수까지의 합 A[i]+A[i+1]+...+A[j-1]+A[j]가 M이 되는 경우의 수를 구하는 프로그램을 작성하시오.


```python
n,m=map(int, input().split())
a=list(map(int,input().split()))
lt=0
rt=0
tot=a[0]
cnt=0
while True:
    if tot<m:
        if rt<n:
            tot+=a[rt]
            rt+=1
        else:
            break
    elif tot==m:
        cnt+=1
        tot-=a[lt]
        lt+=1
    else:
        tot-=a[lt]
        lt+=1
print(cnt)
```

# 6. 격자판 최대합

N*N의 격자판이 주어지면 각 행의 합, 각 열의 합, 두 대각선의 합 중 가 장 큰 합을 출력합 니다.

```python
n=int(input())
a=[list(map(int, input().split())) for _ in range(n)] #2차원 배열을 한번에 읽어들이는 법

largest=-2147000000 #가장 작은 값으로 초기화

for i in range(n): #0행부터 n-1행까지, 각 행의 합, 각 열의 합 구하기
    rowSum=colSum=0
    for j in range(n):
        rowSum+=a[i][j]
        colSum+=a[j][i]
    if rowSum>largest:
        largest=rowSum
    if colSum>largest:
        largest=colSum

#대각선의 합
rowSum=colSum=0
for i in range(n):
    rowSum+=a[i][i]
    colSum+=a[i][n-i-1]
if rowSum>largest:
    largest=rowSum
if colSum>largest:
    largest=colSum

print(largest)
```

1. 각 행의 합, 열의 합 구하기
2. 대각선의 합 구하기

주의할점!

최솟값, 최댓값을 비교할 때 한 배열에 넣고 이후에 비교하려고 하지말고

수를 구하는 과정에서 바로 최솟값 최댓값을 구하기!

2차원 배열 한번에 입력하는 방법도 외워두기!

# 7. 사과나무(다이아몬드)

현수의 농장은 N*N 격자판으로 이루어져 있으며, 각 격자안에는 한 그루의 사과나무가 심어저 있다. N의 크기는 항상 홀수이다. 가을이 되어 사과를 수확해야 하는데 현수는 격자판안의 사 과를 수확할 때 다이아몬드 모양의 격자판만 수확하고 나머지 격자안의 사과는 새들을 위해서 남겨놓는다.
만약 N이 5이면 아래 그림과 같이 진한 부분의 사과를 수확한다. 현수과 수확하는 사과의 총 개수를 출력하세요.

```python
n = int(input())
a=[list(map(int, input().split())) for _ in range(n)]

s=e= n//2

res=0
for i in range(n):
    for j in range(s,e+1):
        res+=a[i][j]
    if i<n//2:
        s-=1
        e+=1
    else:
        s+=1
        e-=1
print(res)
```

1. s와 e 포인터를 두어서 다이아몬드 끝 값을 설정해줌
- 절반보다 위에있는 상황 일 때는 s의 값은 줄여주고 e의 값은 증가시켜줌
- 절반보다 아래에 있을 때는 s의 값은 감소시켜주고 e의 값은 감소시켜줌

# 8. 곶감문제

```python
n = int(input())
a = [list(map(int, input().split()))for _ in range(n)]
m=int(input())
# 회전시켜서 새로운 배열 다시 만들기
for i in range(m):
    h, t, k=map(int, input().split())
    if t==0: #왼쪽으로 도는 거라면!
        for _ in range(k):
            a[h-1].append(a[h-1].pop(0))#제일 앞에 있는 값 pop해주고 그것을 뒤에 추가해주기
    else: #오른쪽으로 도는 거라면!
        for _ in range(k):
            a[h-1].insert(0, a[h-1].pop())#제일 뒤에있는 값 pop해주고 그것을 맨 앞에 추가해주기

#모래시계 모양의 합들 더해주기, s&e 변수를 새로 생성해서 만들기!
res=0
s=0
e=n-1
for i in range(n):
    for j in range(s,e+1):
        res+=a[i][j]
    if i<n//2:
        s+=1
        e-=1
    else:
        s-=1
        e+=1
        
print(res)
```

1. append함수는 제일 뒤에 원소를 추가해주고 insert는 두개의 파라미터를 받아 원하는 위치에 원소를 추가할 수 있다.
2. 모래시계, 다이아몬드 모양의 2차원 배열 합을 더할 때는 새로운 변수 s, e를 생성해서 1씩 증가시켜주거나 감소시켜주는 방식으로 계산하자

# 9. 봉우리

```python
dx=[-1,0,1,0]
dy=[0,1,0,-1]
n = int(input())
a=[list(map(int, input().split()))for _ in range(n)]
a.insert(0, [0]*n)#윗 줄에 0 추가
a.append([0]*n)#아랫 줄에 0 추가

for x in a:#x는 하나의 행을 가르키고 모든 행을 순회함
    x.insert(0, 0) #왼쪽에 0 추가
    x.append(0) #오른쪽에 0 추가

cnt=0
for i in range(1,n+1):
    for j in range(1,n+1):
        if all(a[i][j]>a[i+dx[k]][j+dy[k]] for k in range(4)): 
        #i와 j에서 변화하는 값을 배열에 넣어주어서 for문으로 처리...
        # if a[i][j]>a[i-1][j] and a[i][j]>a[i+1][j] and a[i][j]>a[i][j-1] and a[i][j]>a[i][j+1]:
            cnt+=1
print(cnt)
```

insert는 배열 넣는 위치를 지정할 수 있음

append는 끝에 넣을 수 있음

python의 all 문법 모든 조건이 참이여만 실행함

배열 뒤에 for문 사용할 수 있다…

# 10. 스도쿠검사

```python
def check(a):
    for i in range(9):
        ch1=[0]*9 #행 비교 배열
        ch2=[0]*9 #열 비교 배열
        for j in range(9):
            ch1[a[i][j]]=1
            ch2[a[j][i]]=1
        if sum(ch1)!=9 or sum(ch2)!=9:
            return False
    for i in range(3): #9칸 검사 4중 for문
        for j in range(3):
            ch3=[0]*10
            for k in range(3):
                for s in range(3):
                    ch3[a[i*3+k][j*3+s]]=1
            if sum(ch3)!=9:
                return False
    return True

a=[list(map(int, input().split())) for _ in range(9)]
if check(a):
    print("YES")
else:
    print("NO")
```
