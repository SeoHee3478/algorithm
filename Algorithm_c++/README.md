# 1. C++ 문법 정리

## 1. 입출력
```c++
#include <iostream> //입출력을 위한 헤더파일

using namespace std;

int main(){
  int a;
  cin >> a; //입력 코드
  cout << a; //출력 코드
  return 0;
}
```

```c++
#include <iostream>

int main(void){
  int num1;
  std::cout << "첫 번째 숫자 :
  std::cin >> num1;
  
  int num2;
  std::cout << "두 번째 숫자 : ";
  std::cin >> num2;
  
  int result = num1 + num2;
  std::cout << "합:" <<num1+num2<<std::endl;
  
  return 0;
}
```
<<는 하나의 연산자, 출력 대상을 연이어 출력할 수 있게 도와줌
cout으로 출력함수를 입력하고 그 다음에 <<를 사용하여 출력할 것을 입력!

cin은 입력코드, >>가 아니라 <<로 입력값을 받을 수 있음

endl은 개행을 하는 코드, \n과 같은 기능을 함

## 2. 알고리즘 할 때 자주 쓰는 라이브러리 코드
```c++
#include <stdio.h>
#include <vector> //크기가 가변적인 배열, 동적으로 할당되어 크기를 자유 자재로 변경할 수 있음, 두가지 자료형을 하나의 쌍으로 묶을 수 있는 Pair 사용 가능
#include <set> //key라고 불리는 원소들의 집합 중복이 허용되지 않음!
#include <iostream> //입출력!
#include <cmath>
#include <stdlib.h>
#include <string> ///문자열 string
#include <queue> //FIFO 자료구조, queue 사용 가능하고 BFS에 유용
#include <stack> //LIFO 자료구조, stack 사용 가능
#include <map> //map은 <key,value> 쌍으로 저장 가능
using namespace std;

int main(int argc, char* argv[]){
}
```

## 3. 기본적인 문법
```c++
#include <isotream>

using namespace std;

int main(){
  //조건문
  if (condition){
    ...
  }
  else if(condition){
    ...
  }
  else{
    ...
  }
  
  //조건문 switch
  switch(color){
    case "blue":
      cout << "파란색입니다.";
      break;
    case "red":
      cout << "빨간색입니다.";
      break;
    default:
      cout << "색상이 없습니다.";
      break;
  }
  
  //반복문 for
  for(int i=0;i<len;i++){
    //i가 len보다 작을 때 까지 반복
  }
  
  //반복문 while
  while (condition){
    //조건이 참인 경우 반복
  }
  
  //반복문 do while
  do{
    //일단 실행하고 조건을 검사함.
    //선실행 후판단
  }while(조건)
  
  //삼항연산자
  condition?'true':'false';
  }
}
```

## 4. 코딩테스트에 유용한 자료구조와 함수
### 문자열 string
`#include <string>`으로 라이브러리를 임포트해준다.

```c++
#include <string>

int main(){
  string std;
  std = "Hello World";
  return 0;
}
```

### 내장 함수
  #### 1. push_back, pop_back
  ```c++
  //문자열 맨 뒤에 element를 추가시킨다
  str.push_back(__element);
  //문자열 맨 뒤의 element를 삭제한다
  str.pop_back();
  ```
  
  #### 2. size, length
  ```c++
  //string의 사이즈를 반환한다.
  str.size();
  //string의 길이를 반환한다. size랑 항상 같은 값
  str.length();
  ```
  
  #### 3. empty
  ```c++
  //빈 문자열인지 체크
  //return bool type
  str.empty()
  ```
  
  #### 4. find
  ```c++
  //찾고자 하는 문자가 어디 인덱스에 있는지
  //return index;
  //두번째 인자는 몇번 인덱스부터 찾아줘, default는 0.
  //없으면 -1을 반환함
  str.find(__element,startIndex);
  ```
  
  #### 5. substr
  ```c++
  // 부분 문자열로 잘라줘
  // return string type
  // 몇번 인덱스부터 몇개 잘라줘.
  str.substr(__startIndex, __number);
  ```
  
  #### 6. clear
  ```c++
  // 싹 비워줘
  str.clear();
  ```
  
  #### 7. front,back
  ```c++
  // 맨 뒷값이랑 맨 앞값 줘
  // return string type
  str.front();
  str.back();
  ```
  
  #### 8. begin, end
  ```C++
  // 맨 앞 값과 뒷 값을 가르키는 반복자(iterator) 포인터를 반환한다.
  str.begin();
  str.end();
  ```
  => sort나 다른 함수에 넣을 때 쓰게 됨
  
  #### 9. erase
  ```C++
  // n번부터 m개 지워줘
  1. 인자가 1개이고, 숫자일때 => 이 뒤로 싹 지워줘
  str.erase(startIndex);

  2. 인자가 1개이고, 반복자일 때 => 이거 하나만 지워줘
  str.erase(iterator);

  3. 인자가 2개이고, 숫자일 때 => 여기서부터 몇개 지워줘
  str.erase(startIndex, size_type len);

  4. 인자가 2개이고, 반복자일 때 => 여기서부터 여기까지 지워줘
  str.erase(iterator start, iterator end);
  ```
  
### vertor
파이썬의 리스트처럼 동적 할당 자료구조
`#include <vector>`으로 라이브러리를 임포트해준다.

```c++
#include <vector>

int main(){
    // 선언
	  vertor<type> name;
    // 2차원으로도 선언 가능.
   vector<vector<type>> name;
    
    // m으로 초기화된 n개의 원소를 가지는 벡터를 생성.
    vector<int> vect(n,m)
    
	return 0;
}
```

### 내장 함수
  #### 1. push_back, pop_back
  `string과 활용방법 동일`
  
   #### 2. at
   ```c++
   //둘 다 인덱스에 접근하는 것이지만 at은 범위를 점검하고 들어가기 때문에 []보다 느리지만
   //at을 사용하면 런타임 에러가 아닌 out of range예외를 발생시킴
   vect.at(index);
   vect[index];
   ```
   #### 3. front,back
   
   #### 4. cleart
   
   #### 5. begin, end
   
   #### 6. size
   
   #### 7. empty
   
   #### 8. erase
   
## 5. 그 외 코딩테스트에 쓰는 유용한 라이브러리
  ### 1.algorithm
  ```c++
  #include <algorithm>
  #include <functional> // greater, less 포함하고있음.

  int main() {

      1. 정렬
      sort(arr, arr+n);
      sort(vect.begin(), vect.end()) // 처음부터 끝까지 오름차순 정렬
      sort(vect.begin(), vect.begin() + n) // 처음부터 n번째까지 정렬
      sort(vect.begin(), vect.end(), less<type>) // 처음부터 끝까지 오름차순(default) 정렬
      sort(vect.begin(), vect.end(), greater<type>) // 처음부터 끝까지 내림차순 정렬

      2. 최대, 최소
      max(a, b) 
      min(a, b) 
      *max_element(vect.begin(), vect.end()); // 원소중 가장 큰 값
      *min_element(vect.begin(), vect.end()); // 원소중 가장 큰 값
      // 활용 방법
      // 1. 가장 큰값의 인덱스가 알고싶을 때
      *max_element(vect.begin(), vect.end())-vect.begin();

      3. 탐색
      find(vect.begin(), vect.end(), element); // 이 범위에서 element를 찾아줘
      // element를 찾으면 해당 인덱스의 iterator을 반환하고,
      // 못찾았을 때는 마지막 인덱스의 iterator인 vect.end()를 반환한다.

    return 0;

      4. 순열 관련
      next_permutation();
      prev_permutation();
  }
  ```
  
  ### 2. stack, queue
  파이썬이랑 거의 동일
```C++
  #include <stack>
  #include <queue>

  int main() {
    1. stack
      stack<type> st = { };
      st.top();
      st.push(element);
      st.pop();
      st.empty();
      st.size();
      swap(st1, st2);

      2. queue
      queue<type> q = { };
      q.front();
      q.back();
      q.push();
      q.pop();
      q.empty();
      q.size();
      swap(q1, q2);
  }
  ```
  





