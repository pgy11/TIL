# 05. Object

### 1.  객체(object)

- object type으로 new연산자와 생성자를 통해 변수에 할당된다.

  - 인스턴스(instance)

  <br>

- 객체(object)와 인스턴스(instance) ([참고](https://webclub.tistory.com/37))

  - 서로 비슷하지만, 객체는 좀 더 *일반적인 의미*
  -  인스턴스는 *현재 생성된 바로 그 객체*

  <br>

- JavaScript는 모든 것을 객체 취급

- 객체의 속성과 메소드는 복잡한 현실세계를 반영한 것이다.

- 이 챕터에서는 사용자 정의 객체를 생성하는 방법을 설명한다.

<br>

### 2. class를 이용한 객체 생성

- ECMA6부터 class 예약어를 사용 할 수 있다.

- 선언 및 생성 방법

  ```js
  /*
  class 클래스명{
  	변수;
  	메소드;
  }
  */
  
  class Person{
      name = '';
  	age = 0;
  
  	constructor(name, age){
          this.name = name;
          this.age = age;
      }
  
  	print(){
          console.log(`이름: ${this.name}, 나이: ${this.age}`);
      }
  }
  
  let p = new Person('Gil-dong', 26);
  p.print(); // 이름 : Gil-dong, 나이 : 26
  ```

  <br>

- 접근제한자는 ECMA7부터 지원하지만, 브라우저에서 지원을 안 할 수도 있다.

  - set, get을 이용해 캡슐화를 시도하는 방법이 있다.(e.g. 멤버변수 조작) 

  ```javascript
  class Person{
      name = '';
  	age = 0;
  
  	constructor(name, age){
          this.name = name;
          this.age = age;
      }
  
  	print(){
          console.log(`이름: ${this.name}, 나이: ${this.age}`);
      }
  
  	get birthYear(){
          return 2021 - this.age + 1;
      }
  
  	set birthYear(){
          this.age = 2021 - year + 1;
      }
  }
  
  let p = new Person('Gil-dong', 26);
  p.birthYear = 1997;
  //p.birthYear(1997) // error, not a function - Type error
  
  // Gil-dong는 1997 출생
  console.log(`${p.name}는 ${p.birthYear} 출생`);
  ```

  <br>

<br>

### 3. function을 이용한  객체 생성

- 

  

  ```javascript
  function Student(name, age, major){
  	this.name = name;
  	this.age = age;
  	this.major = major;
  	
  	this.print = function(){
  		console.log(`이름 : ${this.name}, 나이 : ${this.age}, 전공 : ${this.major}`);
  	}
  }
  
  let s = new Student('Min-ji', 22, 'CS');
  s.print(); // 이름 : Min-ji, 나이 : 22, 전공 : CS
  ```

  <br>

<br>

### 4. JSON(JavaScript Object Notation)

- 키, 값쌍으로 이루어져 있으며, 데이터를 교환 할 때 사용한다.

  ```javascript
  let e = {
      name : 'Gil-dong',
      age : 28,
      department : 'Lab'
  };
  console.log(e); // { name: 'Gil-dong', age: 28, department: 'Lab' }
  ```

  <br>

- JSON의 value는 다양한 자료형(object, array, number, string, boolean)이 올 수 있다.

  ```javascript
  let w = {
      person : {name : 'Gil-dong', age : 22},
      department : 'Lab',
      items : [1,2,3,4],
      male : true
  };
  ```

  









