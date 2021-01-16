#  2. 알고리즘의 시간 복잡도 분석

- 주어진 시간안에 정상적으로 실행하기 위해, 다양한 요소들을 고려해야한다.

  - 컴퓨터 사양
  - 사용하는 언어
  - 알고리즘

  <br>

- 같은 알고리즘이라도 위의 2가지(컴퓨터 사양, 언어)에 따라, 실행시간의 차이가 있을 수 있다.

- 시간 복잡도 분석을 위해 알고리즘만 고려하고, 파이썬을 사용한다.

  - 파이썬은 1초에 2000만번 연산을 한다고 가정

<br>

### 1. 수행 시간 측정 방법

- 입력 범위 중 **가장 큰 값**을 입력하여, **가장 깊이있게 중첩된 반복문**이 몇 번 수행하는지 확인한다.

  ```python
  # range of input: 0 <= input_value <= 10K
  
  def solve(input_value):
  	total = 0
  	for i in range(input_value):
      	for j in range(i):
          	total += j
              
       return total
      
  input_value = int(input())
  print(solve(input_value))
  ```

  <br>

- 입력 범위 중 가장 큰 값은 10,000

  - 가장 깊이있게 중첩된 반복문의 횟수는 0 + 1 + 2 + ... + 10,000이므로 50,005,000 이다.(약 5천만)
  - 파이썬 기준, 2초가 넘는 연산(문제에 주어진 제한시간과 비교해보자)

<br>

### 2. Big-O

- 가장 깊이 중첩된 반복문만 고려하여 시간 복잡도를 측정하는 방법 (위의 수행시간 측정 방법을 일반화)
- `O(n)`표기
- 차수가 가장 큰 항만 표기하며, 계수는 무시한다.

<br>

### 3. O(n)

- 반복문이 하나이상 존재하며, 중첩된 반복문이 없다.

- `n <= 10M` 일 때, 사용가능 

  ```python
  def solve(input_value):
      total = 0
      for i in range(input_value): total += i
      return total
  
  result = solve(input_value)
  result -= input_value
  print(result)
  ```

  <br>

### 4.O(n^2)

- 이중 반복문이 하나이상 존재

- `n <= 2K` 일 때, 사용가능

  ```python
  # O(n^2)
  def solve(input_value):
      total = 0
      for i in range(input_value):
          for j in range(i):
              total += j
      return total
  
  print(solve(input_value))
  ```

  <br>

  ```python
  # O(n^2 + n) = O(n^2)
  def solve(input_value):
      total = 0
      for i in range(input_value):
          for j in range(i):
              total += j
      
      for i in range(input_value//2):
      	total -= i
      	
      return total
  
  print(solve(input_value))
  ```

  <br>

### 5. O(n^3)

- 3번 중첩된 반복문이 하나이상 존재

- `n <= 500`일 때, 사용 가능

  ```python
  # O(2n^3 + n) = O(n^3)
  def solve(input_value):
      total = 0
      for i in range(input_value):
          for j in range(i):
              for k in range(j):
              	total += k
                  
      for i in range(input_value):
          for j in range(i):
              for k in range(j):
              	total += k
      
      for i in range(input_value//2):
      	total -= i
      	
      return total
  
  print(solve(input_value))
  ```

  <br>

### 6. O(k^n)

- n이 증가함에 따라 실행시간이 지수적으로 증가

- 정답을 찾기위해, 문제의 모든 경우를 탐색 할 때 나타나는 수행시간

  - 완전탐색에서 볼 수 있음

  ```python
  import sys
  
  n = int(sys.stdin.readline().rstrip())
  arr = list(map(int, sys.stdin.readline().rstrip().split()))
  check = [False for i in range(n)]
  score = 0
  ans = 0
  def get_energy(k):
      global check
      l = 0
      r = n-1
  
      for i in range(k-1,-1,-1):
          if not check[i]:
              l = i
              break
      
      for i in range(k+1,n):
          if not check[i]:
              r = i
              break
      
      return arr[l]*arr[r]
  
  def solve(k):
      global score, ans, check
  
      if k == n-2:
          if ans < score: ans = score
          return
      
      for i in range(1,n-1):
          if not check[i]:
              check[i] = True
              e = get_energy(i)
              score += e
              solve(k+1)
              check[i] = False
              score -= e
  
  solve(0)
  print(ans)
  ```

  <br>

### 7. O(logn)

- n이 증가함에 따라 수행시간이 완만하게 증가
- Binary search

<br>

### 8. O(1)

- 반복문이 없음

- 연산의 수에 상관 없이 항상 `O(1)`표기

- 상수 시간

  ```python
  # O(1)
  def solve(input_value):
  input_value += 8
  
  if input_value > 0: input_value *= 2
  elif input_value < 100: input_value -=2
  total = input_value // 3
  
  return total
  
  print(solve(input_value))
  ```

---

##  * 유의사항

- 보수적으로 추정하여 측정된 수행시간이기 때문에, 반복문 안에 있는 연산의 수와 종류에 따라 시간복잡도가 큰 알고리즘이 수행 될 수 있다.
- 언어마다 연산 속도가 다르지만, 이들을 고려하여 채점을 할 것이다. (물론 아닌 경우도 있음)
  - `C++`은 1초에 1억번 연산, `Python`은 1초에 2천만번 연산







