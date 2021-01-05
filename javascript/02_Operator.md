# 02. 연산자(Operator)

### 1. 산술연산자

 1. `+` : 두 수를 합치거나 두개의 문자열을 이어붙이기 할 때 사용하는 연산자

    ```javascript
    let x = 7;
    let y = 8;
    let z = x + y; // 15가 z에 할당된다.
    ```

    <br>

    ```javascript
    let x = 'hello';
    let y = 'js';
    let z = x + y; // hellojs가 z에 할당된다.
    ```

    

 2. `-` :  두 수를 뺄 때 사용하는 연산자

    `let x = 3 - 4;`

    <br>

 3. `*` : 두 수를 곱할 때 사용하는 연산자

    `let x = 7 * 2;`

    <br>

 4. `/` :  두 수를 나눌 때 사용하는 연산자

    `let x = 7 / 2;`

    <br>

 5. `%` : 나머지를 구할 떄 사용하는 연산자

    `let x = 7 % 2;`

    <br>

<br>

### 2.  대입 연산자

- `=` : 값을 할당 할 떄 사용하는 연산자

  `let x = 7;`

  <br>

<br>

### 3. 비교 연산자

1. `===` : 두 변수의 값이 같으면 `true`, 아니면 `false`를 반환하는 연산자

   ```javascript
   let x = 3;
   let y = 7;
   x === y; // false
   ```

   <br>

   ```javascript
   let x = 3;
   let y = 3;
   x === y; // true
   ```

   <br>

   ```javascript
   let x = 3;
   let y = '3';
   x === y; // false
   ```

   <br>

2. `==` : 역할은 1번과 동일하지만 좀 더 느슨하다.

   ```javascript
   /*
   ===은 ==에 비해 엄격하다. ===은 데이터의 자료형도 고려한다.
   */
   2 == '2'; // true
   2 === '2'; // false
   
   0 == false; // true
   0 === false; // false
   ```

   <br>

3. `!==` : 두 변수의 값이 서로 다르면 `true`아니면 `false`을 반환하는 연산자

   ```javascript
   let x = 7;
   let y = 8;
   x !== y; // true
   
   let p = 3;
   let q = 3;
   p !== q; // true
   ```

   <br>

4.  `!=` : 3번과 역할이 동일하나 좀 더 느슨하다.

   ```javascript
   /*
   !==은 자료형도 고려한다.
   */
   2 != '2'; // false
   2 !== '2'; // true
   
   0 != false; // false
   0 !== false; // true
   ```

   <br>

5. `>` : 좌 변수의 값이 우 변수보다 크면 `true`아니면 `false`을 반환하는 연산자

   ```javascript
   7 > 5; // true
   5 > 7; // false
   ```

   <br>

6. `>=` : 좌 변수의 값이 우 변수보다 크거나 같으면 `true`아니면 `false`을 반환하는 연산자

   `6 >= 6; // true`

   <br>

7. `<` : 좌 변수의 값이 우 변수보다 작으면 `true`아니면 `false`을 반환하는 연산자

   ```javascript
   7 < 5; // false
   5 < 7; // true
   ```

   <br>

8. `<=` 좌 변수의 값이 우 변수보다 작거나 같으면 `true`아니면 `false`을 반환하는 연산자

   `8 <= 8; // true`

   <br>

<br>

### 4. 논리 연산자

1. `조건식1 && 조건식2` : 두 조건식이 모두 `true`면 `true`아니면 `false`을 반환하는 연산자

   ```javascript
   7 == 7 && 6 > 5; // true
   7 > 10 && 6 == 6; // false
   7 != 7 && 6 == 6; // false
   7 == 7 && 6 < 5; // false
   ```

   <br>

2. `조건식1 || 조건식2` : 두 조건식 중 하나라도 `true`면 `true`, 모두 `false`이면 `false`를 반환하는 연산자

   ```javascript
   7 == 7 || 6 > 5; // true
   7 == 7 || 6 != 6; // true
   7 > 10 || 6 == 6; // true
   7 > 10 || 6 != 6; // false
   ```

   <br>

3. `!조건식` : `true`이면 `false`, `false`이면 `true`를 반환하는 연산자

   ```javascript
   !(3 == 3); // false
   !(3 > 10); // true
   ```

   <br>

<br>

### 5. 비트 연산자

- 01.09이전에 올릴 예정

<br>

### 6. 삼항 연산자

- `조건식?  실행문1 : 실행문2` : 조건식이 `true`이면 `실행문1`을 실행, `false`이면 `실행문2`를 실행

  ```javascript
  let x = 7;
  let y = 5;
  
  x > y? y = 3 : y = 10; // 조건식이 true이므로 y = 3
  
  x < y? y = 3: y = 10; // 조건식이 false이므로 y = 10
  ```

  <br>

<br>

###  7. 자료형 알기

- `typeof 변수명` 

  ```javascript
  let x = 7;
  typeof x; // number
  
  x = 'js';
  typeof x; // string
  
  x = true
  typeof x; // boolean
  ```

  
