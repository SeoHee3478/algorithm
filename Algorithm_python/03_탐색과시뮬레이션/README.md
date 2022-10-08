# 1. 회문 문자열 검사

1. 대소문자 구분 없는 문자는 아예 그냥 대문자로 받아올 것 upper함수를 이용해서!
2. 문자열 접근을 -1, -2로도 할 수 있다…
3. for else 구문
4. s[::-1] 문자열을 reverse시켜줌

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

# 2. 숫자만 추출

isdecimal 0~9 숫자

isdigit 알파벳이 아닌 숫자 추출(2^2)도 가능

1) string 문자열 받아오기

2) 문자열 하나씩 for문으로 돌면서 원소가 0~9의 숫자인지 확인하고, 맞다면 계속 10씩 곱해줘서 자연수 만들어주기

3) 약수 구하기 위해서 추출된 값을 1부터 추출된 값까지 for문으로 돌면서 

나누어 떨어지는 수가 있으면 약수의 개수 추가하기

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

op

# 3. 카드 역배치

swap

a,b = b,a

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

# 4. 두 리스트 합치기

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
