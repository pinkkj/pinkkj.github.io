---
excerpt: "APPENDIX A. 코딩 테스트를 위한 파이썬 문법"
name: J
writer: J
categories: [책 정리, 이것이 취업을 위한 코딩 테스트다.] # [메인 카테고리, 서브 카테고리]
tags:
  - []

toc: true
toc_sticky: true

date: 2025-04-12
last_modified_at: 2024-04-12

# --- 아래 부터 content
---

# 1. 자료형

### 수 자료형

- 정수형: 양의 정수, 음의 정수, 0
- 실수형: 소수점 아래의 데이터를 포함하는 자료형(소수부가 0이거나, 정수부가 0인 소수는 0 생략 가능)
    - e를 통해 지수 표현 가능 -> e 다음에 오는 수는 10의 지수부 의미
    - 컴퓨터는 2진수를 이용하고, 실수를 처리할 때 부동 소수점 방식을 이용하므로 **실수 정보를 표현하는 정확도에 한계를 가진다**!!<br>
    => round()이용!! <br>
    => rount(실수형 데이터, (반올림하고자 하는 위치 - 1))<br><br>
    ⭐코딩 테스트에서는 실수형 데이터를 비교할 때 소수점 다섯 번째 자리에서 반올림한 결과가 같으면 정답으로 인정!!!

🔖 수 자료형의 연산

- 나누기 연산자(/): 나눠진 결과를 실수형으로 처리
- 나머지 연산자(%)
- 몫 연산자(//)

### 리스트 자료형

🔖 리스트 만들기

```py
# 크기가 N이고, 모든 값이 0인 1차원 리스트 초기화
n = 10
a = [0] * n
print(a)
```

🔖 리스트의 컴프리헨션

- 대괄호안에 조건문과 반복문을 넣는 방식으로 리스트를 초기화할 수 있음.

```py
# 0부터 19까지의 수 중에서 홀수만 포함하는 리스트
array = [i for i in range(20) if i % 2 == 1]

# 1부터 9까지의 수의 제곱 값을 포함하는 리스트
array = [i * i for i in range(1, 10)]

# N X M 크기의 2차원 리스트 초기화
# 무조건 리스트 컴프리헨션 이용!!
n = 3
m = 4
array = [[0] * m for _ in range(n)]
```

>💡언더바?<br>
o 반복을 수행하되 반복을 위한 변수의 값을 무시하고자 할 때

🔖리스트 관련 기타 메서드

![alt text](/assets/img_20250312/image-1.png)

```py
a = [1,2,3,4,5,5,5]
remove_set = {3, 5}

# remove_set에 포함되지 않는 값만을 저장
result = [i for i in a if i not in remove_set]
```

### 문자열 자료형
### 튜플 자료형

🔖리스트와의 차이점
- 튜플은 한 번 선언된 값을 변경할 수 없다.
- 리스트는 대괄호를 이용하지만, 튜플은 소괄호를 이용한다.

🔖튜플을 언제쓰나?

- 그래프 알고리즘 구현 시 이용
- 변경하면 안 되는 값이 변경되고 있지는 않은지 체크
- 각 원소의 성질이 서로 다를 때

### 사전 자료형

- 파이썬의 자료형은 내부적으로 '해시 테이블'이용!
    - 검색과 수정이 O(1)

```py
data = dict()
data['사과'] = 'apple'
data['바나나'] = 'Banana'
```

- 원소 in 사전: (리스트나 튜플에서도 이용 가능) 원소가 있는지 확인

🔖사전 자료형 관련 함수

```py
data = dict()
data['사과'] = "Apple"
data['바나나'] = "Banana"
data['코코넛'] = "Coconut"

# 키 데이터만 담은 리스트
key_list = data.keys()

# 값 데이터만 담은 리스트
value_list = data.values()
print(key_list)
print(value_list)

# 각 키에 따른 값을 하나씩 출력
for key in key_list:
	print(data[key])
```

### 집합 자료형

🔖집합 자료형 소개

- 리스트나 문자열을 이용해 만들 수 있다.
    - 중복X
    - 순서X
- 특정 원소가 존재하는지 검사하는 연산은 O(1)

```py
# 집합 자료형 초기화 방법1
data = set([1,1,2,3,4,4,5])

# 초기화 방법2
data = {1,1,2,3,4,4,5}
```

🔖집합 자료형의 연산

```py
a = set([1, 2, 3, 4, 5])
b = set([3, 4, 5, 6, 7])

# 합집합
print(a | b)

# 교집합
print(a & b)

# 차집합
print(a - b)
```

🔖집합 자료형 관련 함수

- add(): 하나의 집합 데이터에 값을 추가할 때
- update(): 여러 개의 값을 한꺼번에 추가하고자 할 때
- remove(): 특정한 값을 제거할 때<br>
=> 이 때, add(), remove() 모두 시간복잡도 O(1)

```py
data = set([1, 2, 3])
print(data)

# 새로운 원소 추가
data.add(4)
print(data)

# 새로운 원소 여러 개 추가
data.update([5, 6])
print(data)

# 특정한 값을 갖는 원소 삭제
data.remove(3)
print(data)
```

# 2.조건문

### 비교 연산자
### 논리 연산자
### 파이썬의 기타 연산자

![alt text](/assets/img_20250312/image-2.png)

### pass

```py
score = 85

if score >= 80:
	pass # 나중에 작성할 소스코드
else:
	print("성적이 80점 미만입니다.")
    
print("프로그램을 종료합니다.")
```
- 아무것도 처리하고 싶지 않을 때

### 조건문에서 실행될 소스코드가 한줄인 경우

```py
score = 85

if score>=80: result = "Success"
else: result = "Fail"
```

### 조건부 표현식

```py
score = 85
result = "Sucess" if score >= 80 else "Fail"
```

⭐리스트에 있는 원소의 값을 변경해서, 또 다른 리스트를 만들고자 할 때 매우 유용.

```py
# 원래 
a = [1, 2, 3, 4, 5, 5, 5]
remove_set = {3, 5}

result = []
for i in a:
	if i not in remove_set:
    	result.append(i)
        
print(result)

# 수정
a = [1, 2, 3, 4, 5, 5, 5]
remove_set = {3, 5}

result = [i for i in a if i not in remove_set]

print(result)
```

# 3.반복문

### While 문
### for 문

🔖continue

- 만나면 프로그램의 흐름은 반복문의 처음으로 돌아간다.

```py
scores = [90, 85, 77, 65, 97]
cheating_list = {2,4}

for i in range(5):
    if i + 1 in cheating_list:
        continue
    if scores[i] >= 80:
        print('통과')
```

# 4.함수

### global 키워드

- 함수 안에서 함수 밖의 변수 데이터를 변경해야 하는 경우.
- 함수에서 global 키워드로 변수를 지정하면, 해당 함수에서는 지역 변수를 만들지 않고, 함수 바깥에 선언된 변수를 바로 참조.

```py
a = 0

def func():
	global a
    a += 1
    
for i in range(10):
	func()
    
print(a)
```

### 람다 표현식
- 파이썬의 정렬 라이브러리를 사용할 때, 정렬 기준(Key)을 설정할 때에도 자주 사용된다.

```py
def add(a, b):
	return a + b

# 일반적인 add() 메서드 사용
print(add(3, 7))

# 람다 표현식으로 구현한 add() 메서드
print((lambda a, b : a + b)(3, 7))
```

# 5.입출력

### 여러 개의 데이터 입력(공백)

```py
list(map(int, input().split()))
```
1. input()으로 입력받은 문자열을 공백으로 나눈 리스트로 바꾼다.
2. map 함수를 통해 해당 리스트의 모든 원소에 int() 함수 적용!

### 여러 개의 데이터 입력(줄바꿈)

```py
n = int(input())
```

=> 예시

```py
# 데이터의 개수 입력
n = int(input())
# 각 데이터를 공백으로 구분하여 입력
data = list(map(int, input().split()))

data.sort(reverse=True)
print(data)
```
```py
# n, m, k를 공백으로 구분하여 입력
n, m, k = map(int, input().split())

print(n, m, k)
```

### 입력 받을 데이터가 많은 경우???

- sys 라이브러리에 정의되어 있는 sys.stdin.readline() 함수 이용.

```py
import sys
sys.stdin.readline().rstrip()
```

⭐sys 라이브러리를 이용할 때는 한 줄 입력을 받고 나서 rstrip() 함수를 꼭 호출!!<br>
-> readline()으로 입력하면 입력 후 엔터가 줄 바꿈 기호로 입력. 이걸 제거하려면 rstrip() 이용!!!

```py
import sys

# 문자열 입력
data = sys.stdin.readline().rstrip()
print(data)
```

### 출력

- print()를 사용할 때마다 줄이 변경

🔖f-string 문법

```py
answer = 7
print(f"정답은 {answer}입니다.")
```

# 6.주요 라이브러리의 문법과 유의점

[표준 라이브러리 공식 문서](https://docs.python.org/ko/3/library/index.html)
### 알아야 하는것!!

- 내장함수 : print(), input()과 같은 기본 입출력 기능부터 sorted()와 같은 정렬 기능을 포함하고 있는 기본 내장 라이브러리, 파이썬 프로그램을 작성할 때 없어서는 안되는 필수적인 기능을 포함하고 있음
- itertools : 파이썬에서 반복되는 형태의 데이터를 처리하는 기능을 제공하는 라이브러리, 순열과 조합 라이브러리를 제공
- heapq : 힙(Heap) 기능을 제공하는 라이브러리, 우선순위 큐 기능을 구현하기 위해 사용
- bisect : 이진 탐색 기능을 제공하는 라이브러리
- collections : 덱, 카운터 등의 유용한 자료구조를 포함하고 있는 라이브러리
- math : 필수적인 수학적 기능을 제공하는 라이브러리, 팩토리얼, 제곱근, 최대공약수, 삼각함수 관련 함수부터 파이와 같은 상수를 포함

### 내장함수

- 별도의 import 없이 이용 가능!!
- ex) print, input....

- sum()함수 : 리스트와 같은 iterable() 객체가 입력으로 주어졌을 때 모든 원소의 합은 반환
    - 파이썬에서 iterable 객체는 반복 가능한 객체를 말함
→ 리스트, 사전 자료형, 튜플 자료형 등이 이에 해당함
- min()함수 : 파라미터가 2개 이상 들어왔을 때 가장 작은 값을 반환
- max()함수 : 파라미터가 2개 이상 들어왔을 때 가장 큰 값을 반환
- eval()함수 : 수학 수식이 문자열 형식으로 들어오면 해당 수식을 계산한 결과를 반환

```py
result = eval("(3+5) * 7")
print(result)
```

- sorted()함수: iterable 객체가 들어왔을 때 정렬된 결과를 반환, key 속성으로 정렬 기준을 명시할 수 있으며, reverse 속성으로 정렬된 결과 리스트를 뒤집을지의 여부를 설정할 수 있음
```py
# 원소를 튜플의 두번째 원소(수)를 기준으로 내림차순으로 정렬
result = sorted([('홍길동', 35), ('이순신', 75), ('아무개', 50)], key = lambda x: x[1], reverse = True)

print(result)
```

- sort()함수: 리스트와 같은 iterable 객체는 기본적으로 sort()함수를 내장하고 있어서 굳이 sorted()함수를 사용하지 않고도 sort()함수를 사용해서 정렬할 수 있음
→ 리스트 객체의 내부 값이 정렬된 값으로 바로 변경됨

```py
data = [9, 1, 8, 5, 4]
data.sort()
print(data)
```

### itertools

- 파이썬에서 반복되는 데이터를 처리하는 기능을 포함하고 있는 라이브러리

- 제공하는 클래스는 매우 다양하지만, 코딩 테스트에서 가장 유용하게 사용할 수 있는 클래스는 permutations, combinations임

- permutations : 리스트와 같은 iterable 객체에서 r개의 데이터를 뽑아 일렬로 나열하는 모든 경우(순열)를 계산해줌<br>
→ 클래스이므로 객체 초기화 이후에는 리스트 자료형으로 변환하여 사용

```py
#<리스트 ['A', 'B', 'C']에서 3개(r = 3)를 뽑아 나열하는 모든 경우를 출력>

from itertools import permutations

data = ['A', 'B', 'C'] # 데이터 준비
result = list(permutations(data, 3)) # 모든 순열 구하기
print(result)

#<출력>
#[('A', 'B', 'C'), ('A', 'C', 'B'), ('B', 'A', 'C'), ('B', 'C', 'A'), ('C', 'A', 'B'), ('C', 'B', 'A')]
```

- combinations : 리스트와 같은 iterable 객체에서 r개의 데이터를 뽑아 순서를 고려하지 않고 나열하는 모든 경우(조합)를 계산<br>
→ 클래스이므로 객체 초기화 이후에는 리스트 자료형으로 변환하여 사용

```py
#<리스트 ['A', 'B', 'C']에서 2개(r = 2)를 뽑아 순서에 상관없이 나열하는 모든 경우를 출력>

from itertools import combinations

data = ['A', 'B', 'C'] # 데이터 준비
result = list(combinations(data, 2)) # 2개를 뽑는 모든 조합 구하기
print(result)

#<출력>
#[('A', 'B'), ('A', 'C'), ('B', 'C')]
```

- product : permutations와 같이 리스트와 같은 iterable 객체에서 r개의 데이터를 뽑아 일렬로 나열하는 모든 경우(순열)를 계산<br>
→ 다만 원소를 중복하여 뽑음, 객체를 초기화할 때는 뽑고자 하는 데이터의 수를 repeat 속성값으로 넣어줌<br>
→ 클래스이므로 객체 초기화 이후에는 리스트 자료형으로 변환하여 사용

```py
#<리스트 ['A', 'B', 'C']에서 중복을 포함하여 2개(r = 2)를 뽑아 나열하는 모든 경우를 출력>

from itertools import product

data = ['A', 'B', 'C'] # 데이터 준비
result = list(product(data, repeat=2)) # 2개를 뽑는 모든 순열 구하기(중복 허용)
print(result)

#<출력>
#[('A', 'A'), ('A', 'B'), ('A', 'C'), ('B', 'A'), ('B', 'B'), ('B', 'C'), ('C', 'A'), ('C', 'B'), ('C', 'C')]
```

- combinations_with_replacement : combinations와 같이 리스트와 같은 iterable 객체에서 r개의 데이터를 뽑아 순서를 고려하지 않고 나열하는 모든 경우(조합)를 계산<br>
→ 다만 원소를 중복하여 뽑음<br>
→ 클래스이므로 객체 초기화 이후에는 리스트 자료형으로 변환하여 사용

```py
#<리스트 ['A', 'B', 'C']에서 중복을 포함하여 2개(r = 2)를 뽑아 순서에 상관없이 나열하는 모든 경우를 출력>

from itertools import combinations_with_replacement
data = ['A', 'B', 'C'] # 데이터 준비
result = list(combinations_with_replacement(data, 2)) # 2개를 뽑는 모든 조합 구하기(중복 허용)
print(result)

#<출력>
#[('A', 'A'), ('A', 'B'), ('A', 'C'), ('B', 'B'), ('B', 'C'), ('C', 'C')]
```

### heapq

- 파이썬의 힙은 최소 힙(min heap)
- 힙 기능 제공
- 우선 순위 큐 기능을 구현하고자 할 때 이용<br>
=> 보통 PriorityQueue 라이브러리보다 더 빠름.

🔖method
- heapq.heappush(): 삽입
- heapq.heappop(): 꺼내기

🔖힙정렬 구현

```py
#<힙 정렬을 heapq로 구현>
 import heapq
 
 def heapsort(iterable):
 	h = []
    result = []
    # 모든 원소를 차례대로 힙에 삽입
    for value in iterable:
    	heapq.heappush(h, value)
    # 힙에 삽입된 모든 원소를 차례대로 꺼내어 담기
    for_in range(len(h)):
    	result.append(heapq.heappop(h))
    return result
    
result = heapsort([1, 3, 5, 7, 9, 2, 4, 6, 8, 0])
print(result)

#<출력>
#[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

🔖최대 힙 구현(파이썬 힙은 최대 힙 제공X)

```py
# 부호 이용
#<최대 힙을 구현하여 내림차순 힙 정렬 구현>

import heapq

def heapsort(iterable):
 	h = []
    result = []
    # 모든 원소를 차례대로 힙에 삽입
    for value in iterable:
    	heapq.heappush(h, -value)
    # 힙에 삽입된 모든 원소를 차례대로 꺼내어 담기
    for_in range(len(h)):
    	result.append(-heapq.heappop(h))
    return result
  
result = heapsort([1, 3, 5, 7, 9, 2, 4, 6, 8, 0])
print(result)

#<출력>
#[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

### bisect

- 이진탐색 라이브러리
- "정렬된 배열"에서 특정한 원소를 찾아야 할 때 효과적!!

- bisect_left(), bisect_right() 함수가 가장 중요하게 사용되며, 이 두 함수는 시간복잡도 O(logN)에 동작
    - bisect_left(a, x) : 정렬된 순서를 유지하면서 리스트 a에 데이터 x를 삽입할 가장 왼쪽 인덱스를 찾는 메서드
    - bisect_right(a, x) : 정렬된 순서를 유지하도록 리스트 a에 데이터 x를 삽입할 가장 오른쪽 인덱스를 찾는 메서드

![alt text](/assets/img_20250312/image-3.png)

```py
#<정렬된 리스트 [1, 2, 4, 4, 8]이 있을 때 새롭게 데이터 4를 삽입하려 한다는 가정>

from bisect import bisect_left, bisect_right

a = [1, 2, 4, 4, 8]
x = 4

print(bisect_left(a, x))
print(bisect_right(a, x))

#<출력>
#2
#4
```

🔖bisect_left와 right가 정렬된 리스트에서 값이 특정 범위에 속하는 원소의 개수를 구할 때 이용되는 경우

- 원소의 값이 x라고 할 때 left_value ≤ x ≤ right_value인 원소의 개수를 O(logN)으로 빠르게 계산할 수 있음

```py
from bisect import bisect_left, bisect_right

# 값이[left_value, right_value]에 속하는 데이터의 개수를 반환
def count_by_range(a, left_value, right_value):
    right_index = bisect_right(a, right_value)
    left_index = bisect_left(a, left_value)
    return right_index - left_index
```

### collections

- collections 라이브러리의 기능 중 코딩테스트에서 유용하게 사용되는 클래스 : depue, Counter

🔖deque

- 큐 구현시 이용
- 큐는 시작이나 끝에 데이터를 삽입하거나 제거할 때 유용
- deque는 스택이나 큐의 기능을 모두 포함.

![alt text](/assets/img_20250312/image-4.png)

- 첫번째 원소를 제거할 때 popleft() 사용
- 마지막 원소를 제거할 때 pop() 사용
- 첫번째 인덱스에 원소 x를 삽입할 때 appendleft(x) 사용
- 마지막 인덱스에 원소를 삽입할 때 append(x) 사용<br>
∴ deque를 큐 자료구조로 이용할 때 원소를 삽입할 때는 append()를 사용하고, 원소를 삭제할 때는 popleft()를 사용하면 됨<br>
→ 먼저 들어온 원소가 항상 먼저 나가게 됨

```py
#<리스트 [2, 3, 4]의 가장 앞쪽과 뒤쪽에 원소 삽입>

from collections import deque

data = deque([2, 3, 4])
data.appendleft(1)
data.append(5)

print(data)
print(list(data)) # 리스트 자료형으로 변환

#<출력>
#deque([1, 2, 3, 4, 5])
#[1, 2, 3, 4, 5]
```

- Counter: 등장 횟수 세기.

```py
#<원소별 등장 횟수를 세는 기능>

from collections import Counter

counter = Counter(['red', 'blue', 'red', 'green', 'blue', 'blue'])

print(counter['blue']) # 'blue'가 등장한 횟수 출력
print(counter['green']) # 'green'이 등장한 횟수 출력
print(dict(counter)) # 사전 자료형으로 변환

#<출력>
#3
#1
#{'red':2, 'blue':3, 'green':1}
```

### math

- 자주 사용되는 수학적인 기능을 포함하고 있는 라이브러리
팩토리얼, 제곱근, 최대공약수 등을 계산해주는 기능을 포함하고 있으므로 수학 계산을 요구하는 문제를 만났을 때 효과적으로 사용될 수 있음

🔖 factorial(x) 함수 : x! 값을 반환
```py
#<5!를 출력>

import math

print(math.factorial(5)) # 5 팩토리얼을 출력

#<출력>
#120
```

🔖sqrt(x): x의 제곱근 반환

```py
#<7의 제곱근을 출력>

import math

print(math.sqrt(7)) # 7의 제곱근을 출력

#<출력>
#2.6457513110645907
```

🔖gcd(a,b): 최대공약수 구하기

```py
#<21과 14의 최대공약수를 출력>

import math

print(math.gcd(21, 14))

#<출력>
#7
```

🔖파이나 자연상수(e) 제공
```py
import math

print(math.pi) # 파이(pi) 출력
print(math.e) # 자연상수 e 출력

#<출력>
#3.141592653589793
#2.718281828459045
```

# 7. 자신만의 알고리즘 노트 만들기

