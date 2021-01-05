# 01. Variable

<br>

### 1. 변수(Variable)

- 값을 저장하는 공간

- 변수를 선언하는 방법 : `let` or `var` 사용

  ```javascript
  /*
  let, var을 이용하여 변수를 선언한다.
  차이점은 var은 변수 유효범위를 고려하지 않고, let은 고려한다.
  따라서 let을 이용하여 선언된 변수는 유효범위 밖에서 사용 할 수 없다.
  */
  let x;
  var x;
  ```

<br>

- 변수에 값을 할당하는 방법

  1. ```javascript
     var x;
     x = 7;
     ```

  2. ```javascript
     let x;
     x = 7;
```
     
  3.  ```javascript
     let x = 7;
     ```
   
  4. ```javascript
     x = 7;
     ```

<br>

- `const`

  - `const`로 선언된 변수에 값이 한 번 할당되면, 이후 값을 바꿀 수 없다.

  - Read only

  - ```javascript
    const x = 7;
    x = 6; // error
    ```

    <br>

<br>

### 2. 자료형(Data type)

- Primitive

  1. `number` : 정수 or 실수

     ```javascript
     let x = 3;
     let y = 3.14;
     ```

     <br>

  2. `string` : 문자열

     - `let 변수명 = '값'` or `let 변수명 = "값"`

     ```javascript
     let x = 'js';
     let y = "hello";
     ```

     <br>

  3. `boolean` : 불리언, `true` or `false`

     ```javascript
     let x = true;
     let y = false;
     ```

     <br>

<br>

- Reference

  1. `Array` : 여러개 의 값을 하나의 변수에 저장

     `let arr = [1, 'js', 4.4, true];`

     <br>

  2. `Object` : 자바스크립트는 모든 것이 **객체**이다.

     `let x = document.querySelector('h1');`

     <br>

<br>

### 3. 주석

- `// `or `/**/ `사용

  - ```javascript
    let x = 7; // 7을 변수 x에 할당
    ```

  - ```javascript
    /*
    변수 x에
    7을 할당
    */
    let x = 7;
    ```

  

