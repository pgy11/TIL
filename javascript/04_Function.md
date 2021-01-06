# 04. Function

### 1. 함수  기초

- JavaScript는 모든 것이 객체로 되어있는데, 함수 역시 객체로 취급된다.

- 정의

  ```javascript
  /*
   function 함수명(parameter1, parameter2, ...){
   	실행문;
   	return data;
   }
  */
  
  function add(x, y){
      return x + y;
  }
  
  let res = add(4,3);
  console.log(res); // res === 7
  ```

  <br>

- 0개 이상의 `parameter`를 가질 수 있다.

- `return`문이 사용되지 않거나, 값이 없는 데이터를 반환하고, 이를 변수에 할당하면 `undefined`로 설정된다.

  ```javascript
  function hello(){
  	let x = 8;
  }
  
  function getParameter(k){
      return k;
  }
  
  console.log(hello()); // undefined
  
  let variable;
  console.log((variable)); // undefined
  ```

  

- 호출 할 때, 함수에서 필요한 개수만큼의 `parameter`를 주지 않으면, 해당 `parameter`는 `undefined`로 설정된다.

  ```javascript
  /*
  2개의 parameter가 필요한데, 아무것도 안주면 parameter은 undefined으로 설정된다. 따라서 연산이 불가능하다.
  NaN
  */
  function add(x, y){
      return x + y;
  }
  
  let res = add(); // NaN
  ```

  <br>

- 호출 할 때, 요구되는 `parameter`의 수보다 더많은 `parameter`을 주게되면, 왼쪽부터 필요한 수만큼의 `parameter`가 사용된다.

  ```javascript
  /*
  요구되는 paramter의 수는 2이지만, 3개를 줘서 호출 할 때, 2개만 사용된다.
  7,8이 사용된다.
  */
  
  function add(x, y){
      return x + y;
  }
  
  let res = add(7,8,9);
  console.log(res); // x === 15
  ```

  <br>

- `parameter`에서 기본 값을 정할 수 있다.

  ```javascript
  function add(x, y=7){
  	return x + y;
  }
  
  console.log(add(4)); // 11
  ```

  <br>

- 앞의 `parameter`의 값이 뒤의 `parameter`의 기본 값에 사용 될 수 있다.

  ```javascript
  function displayInfo(name, food, eat = name + ' eats ' + food){
  	console.log(eat);
  }
  
  displayInfo('Gil-dong', 'apple'); // Gil-dong eats apple
  ```

  <br>

- `parameter`에 함수를 줄 수 있다.

  ```javascript
  function subtract(x, y){
  	return x - y;
  }
  
  function callSubFunc(f){
  	return f;
  }
  
  res = callSubFunc(subtract(8, 5));
  console.log(res); // res === 3
  ```

  <br>

<br>

### 2. 익명 함수(Anonymous function)

- 함수명을 표시하지 않고 사용한다.

- `JavaScript`는 모든 것을 **객체**취급 하기 때문에 익명 함수를 변수에 할당 할 수 있다.

  ```javascript
  multiply = function(x, y){
      return x * y;
  };
  
  console.log(multiply(4,2)); // 8
  ```

  <br>

- 일회용으로 사용하기 좋다.

- 정의와 동시에 바로 사용하고 싶으면, `}` 옆에 `()`을 붙이되, 안에 필요한 수 만큼의 `paramter`들을 적는다.

  - 반환 값을 변수에 저장 할 때, 반환 값이 없거나 또는 저장을 하지 않을 때, 사용하는 방법이 약간 다르다.
  - 반환값이 없거나, 변수에 저장하지 않을 때, `function(){}`을 `()`으로 묶는다.

  ```javascript
  /*
  function(parameter1, paramter2, ...){
  	실행문;
  	return data;
  }(paramter1, paramter2, ...);
  */
  
  /*
  반환값이 변수에 저장 될 때
  */
  console.log(
  	function(){
  		return 'hello js';
  	}()
  ); // hello js
  
  let res = function(x, y){
      return x + y;
  }(7, 8);
  
  console.log(res); // res === 15
  
  /*
  반환값이 없거나, 저장하지 않을 때
  */
  
  (function(){
      console.log('hello js');
  })();
  
  (function(x, y){
      console.log(x + y); // 6
      return x + y;
  })(4,2);
  ```

  <br>

<br>

### 3. 람다식(Lambda expression)

- 화살표 함수(Arrow function), `=>`를 이용하여 표현한다.

  ```javascript
  /*
  (paramter1, paramter2, ...) => {
  	실행문
  	return data;
  }
  */
  
  let display = () => {
  	console.log('Hello js');
  };
  
  display(); // Hello js
  ```

  

- 익명 함수를 생성과 동시에 사용하는 것보다, 람다식을 이용해서 생성과 동시에 실행하는 것이 더 편리하다.

- 정의와 동시에 바로 사용하고 싶으면, `}` 옆에 `()`을 붙이되, 안에 필요한 수 만큼의 `paramter`들을 적는다. `() => {}`를 `()`으로 감싼다.

  ```javascript
  let k = ((x) => {
      return x + 1;
  })(5);
  
  console.log(k); // k === 6
  
  (() => {
      console.log('Hello js');    
  })();
  ```

  <br>

<br>

### 4. 클로저(Closure)

- 함수의 반환 값으로 다른 함수를 반환한다.

- 반환되는 함수의 실행문은 외부 함수에 있는 지역변수에 접근 할 수 있다.

  ```javascript
  function makeAddr(x){
      let y = 1;
      return function(z){
          y = 100; // 외부 함수의 지역변수에 접근하여 100 할당
          return x + y + z; // 외부 함수의 parameter에 접근하여 연산
      }
  }
  
  let add5 = makeAddr(5);
  let add10 = makeAddr(10);
  
  console.log(add5(2)); // 107
  console.log(add10(2)); // 112
  
  function multi(n){
      return function(){
          return n *= n;
      }
  }
  
  let multi5 = multi(5);
  let multi10 = multi(10);
  
  console.log(multi5()); // 25
  console.log(multi10()); // 100
  ```

  <br>

- 클로저 함수에서 변수를 만들 때, 외부 함수의 변수명을 고려해야한다. (유효범위에 주의)

<br>

<br>

### 5. 재귀 함수

- 자기 자신을 호출하는 함수

- 종료점이 필요하다.

  ```javascript
  function fact(n){
      if(n == 1){
          return 1;
      }
      return n * fact(n-1);
  }
  
  let k = fact(4);
  console.log(k); // 4 * 3 * 2 * 1 === 24
  ```

  