# 06. Array

### 1. 배열(Array)

- 다양한 자료형의 데이터들을 하나의 변수에 저장하는 내장 객체

- 배열 생성 방법

  - `new`연산자를 이용한 배열 생성

    ```javascript
    let subject = new Array(10, true, 'hello', [1,2,3]);
    console.log(subject); // [ 10, true, 'hello', [ 1, 2, 3 ] ]
    ```

    <br>

  - `[]`을 이용한 배열 생성

    ```javascript
    let subject = [10, true, 'hello', [1,2,3]];
    console.log(subject); // [ 10, true, 'hello', [ 1, 2, 3 ] ]
    
    // 인덱스 3, 4에 저장된 값이 없어도, 인덱스 6에 값을 저장 할 수 있다.
    let arr = [];
    arr[0] = 10;
    arr[1] = true;
    arr[2] = 'hello';
    arr[3] = [1,2,3];
    arr[6] = 'JS';
    console.log(arr); // [ 10, true, 'hello', [ 1, 2, 3 ], <2 empty items>, 'JS' ]
    ```

    <br>

- 프로퍼티 `length`를 통해 배열의 길이를 알 수 있다.

  ```javascript
  let subject = [10, true, 'hello', [1,2,3]];
  console.log(subject.length); // 4, [1,2,3]은 하나의 요소로 취급한다.
  ```

  <br>

- `length`의 값을 변경하면 배열의 길이가 변경된 `length`의 값으로 변한다.

  - 0, 1, 2, ..., `length-1` 인덱스에 해당하는 요소가 남고, 나머지는 모두 삭제된다.

  ```javascript
  let subject = [10, true, 'hello', [1,2,3]];
  subject.length = 2;
  console.log(subject); // [ 10, true ]
  ```

  <br>

<br>

### 2. Array 객체에서 제공하는 메소드

- 알아두면 유용한 메소드들 위주로 작성

1. `slice([start[, end]])`

   - 인덱스 `start`번부터 인덱스 `end-1`에 해당하는 요소들을 배열 형태로 반환한다.

   - `start`가 주어지지 않을 경우, 인덱스 0부터 시작한다.

   - `end`가 주어지지 않을 경우, `slice()`는 인덱스 `start`부터 `length-1`까지 슬라이싱한다.

   - 원본 배열을 변경하지 않기 때문에, `slice()` 통해 반환된 배열을 별도의 변수에 저장해야한다.

     ```javascript
     let subject = [10, true, 'hello', [1,2,3]];
     let result = subject.slice(1,3);
     console.log(result); // [ true, 'hello' ]
     
     subject = [10, true, 'hello', [1,2,3]];
     result = subject.slice(1);
     console.log(result); // [ true, 'hello', [ 1, 2, 3 ] ]
     ```

     <br>

   - `start`와 `end`에 음의 값을 줄 수 있다. (e.g. -1은 마지막 요소를 가리키고 -2는 마지막에서 2번째 요소를 가리킨다.)

     ```javascript
     let subject = [10, true, 'hello', [1,2,3]];
     let result = subject.slice(-4,-2);
     console.log(result); // [ 10, true ]
     
     subject = [10, true, 'hello', [1,2,3]];
     result = subject.slice(-1);
     console.log(result); // [ [ 1, 2, 3 ] ]
     ```

     <br>

2. `join([separator])`

   - 요소와 요소사이에 `separator`(객체)를 붙인다. 그리고 문자열 형태로 반환한다. 만약 `separator`가 없으면 `,`가 사용된다.

   - 원본 배열을 변경하지 않기 때문에, `join()`을 통해 반환된 배열을 별도의 변수에 저장해야한다.

     ```javascript
     let subject = [10, true, 'hello', [1,2,3]];
     let result = subject.join('-');
     console.log(result); // 10-true-hello-1,2,3
     
     let alpha = ['a', 'b', 'c', 'd'];
     result = alpha.join(true);
     console.log(result); // atruebtruectrued
     
     result = alpha.join(99);
     console.log(result); // a99b99c99d
     
     result = alpha.join();
     console.log(result);
     ```

     <br>

3. `concat([value1[, value2[, ...[, valueN]]]])`

   - 주어진 `value`들을 배열에 이어붙인다.

   - 원본 배열을 변경하지 않기 때문에, `concat()`을 통해 반환된 배열을 별도의 변수에 저장해야한다.

     ```javascript
     let machines = ['computer', 'car', 'mobile phone'];
     let family = ['father', 'mother'];
     
     let result = family.concat(machines);
     console.log(result); // [ 'father', 'mother', 'computer', 'car', 'mobile phone' ]
     
     result = family.concat(1, 2, 5);
     console.log(result); //[ 'father', 'mother', 1, 2, 5 ]
     ```

     <br>

4. `toString()`

   - 배열을 문자로 변환한다.

     ```javascript
     let machines = ['computer', 'car', 'mobile phone'];
     let result = machines.toString();
     console.log(result); // computer,car,mobile phone
     
     let subject = [10, true, 'hello', [1,2,3]];
     result = subject.toString();
     console.log(result); // 10,true,hello,1,2,3
     ```

     <br>

5. `shift()`

   - 첫번째 요소를 삭제한다.

   - 원본 배열을 변경한다.

     ```javascript
     let machines = ['computer', 'car', 'mobile phone'];
     let removed = machines.shift();
     console.log(removed); // computer
     console.log(machines); // [ 'car', 'mobile phone' ]
     ```

     <br>

6. `unshift(element1[, ...[, elementN]])`

   - 요소 또는 요소들을 배열의 첫번째 요소 왼쪽에 추가한다.(i.e. `unshift()`후 배열의 첫번째 요소는 추가된 요소 또는 요소들이다.)

   - 원본 배열을 변경한다.

     ```javascript
     let machines = ['computer', 'car', 'mobile phone'];
     machines.unshift('network device');
     console.log(machines); // [ 'network device', 'computer', 'car', 'mobile phone' ]
     
     let family = ['father', 'mother'];
     family.unshift('me', 'brother', 'sister');
     console.log(family); // [ 'me', 'brother', 'sister', 'father', 'mother' ]
     ```

     <br>

7. `pop()`

   - 배열의 마지막 요소를 삭제한다.

   - 원본 배열을 변경한다.

     ```javascript
     let machines = ['computer', 'car', 'mobile phone'];
     let removed = machines.pop();
     console.log(removed); // mobile phone
     console.log(machines); // [ 'computer', 'car' ]
     ```

     <br>

8. `push(element1[, ...[, elementN]])`

   - 배열의 마지막요소의 우측에 새로운 요소 또는 요소들을 추가한다.

   - 원본 배열을 변경한다.

     ```javascript
     let machines = ['computer', 'car', 'mobile phone'];
     machines.push('network device');
     console.log(machines); // [ 'computer', 'car', 'mobile phone', 'network device' ]
     
     let family = ['father', 'mother'];
     family.push('me', 'brother', 'sister');
     console.log(family); // [ 'father', 'mother', 'me', 'brother', 'sister' ]
     ```

     <br>

9. `splice(start[, deleteCount[, item1[, item2[, ...]]]])`

   - 인덱스 `start`부터 시작하여 `deleteCount`개의 요소들을 지우고 `item`들을 추가한다.

   - 원본 배열을 변경한다.

     ```javascript
     let machines = ['computer', 'car', 'mobile phone', 'motor', 'oven', 'bike', 'mike'];
     machines.splice(1, 0, 'speaker'); // 삭제되는 요소 없고 인덱스 1에 speaker가 추가 -> car은 인덱스 2로 밀려나게 된다.
     console.log(machines); // [ 'computer',  'speaker',  'car',  'mobile phone',  'motor',  'oven',  'bike',  'mike']
     ```

     <br>

     ```javascript
     let machines = ['computer', 'car', 'mobile phone', 'motor', 'oven', 'bike', 'mike'];
     machines.splice(1, 3, 'speaker'); // 인덱스 1부터 시작하여, 3개의 요소 삭제, 인덱스 1에 speaker 추가
     console.log(machines); // [ 'computer', 'speaker', 'oven', 'bike', 'mike' ]
     ```

     <br>

     ```javascript
     let machines = ['computer', 'car', 'mobile phone', 'motor', 'oven', 'bike', 'mike'];
     machines.splice(1, 3); // 인덱스 1부터 시작하여, 3개의 요소 삭제
     console.log(machines); // [ 'computer', 'oven', 'bike', 'mike' ]
     ```

     <br>

     ```javascript
     let machines = ['computer', 'car', 'mobile phone', 'motor', 'oven', 'bike', 'mike'];
     machines.splice(1, 5, 'bettery', 'light', 'air-conditioner'); // 인덱스 1부터 시작하여, 5개의 요소 삭제, 3개 요소 추가
     console.log(machines); // [ 'computer', 'bettery', 'light', 'air-conditioner', 'mike' ]
     ```

     <br>

     ```javascript
     let machines = ['computer', 'car', 'mobile phone', 'motor', 'oven', 'bike', 'mike'];
     // start에 음의 값을 줄 수 있다.
     machines.splice(-2, 1); // 마지막에서 2번째 요소(bike) 삭제
     
     console.log(machines); // [ 'computer', 'car', 'mobile phone', 'motor', 'oven', 'mike' ]
     ```

     <br>

     ```javascript
     let machines = ['computer', 'car', 'mobile phone', 'motor', 'oven', 'bike', 'mike'];
     // deleteCount를 생략 할 수 있다.
     machines.splice(2); // 인덱스 2부터 시작하여 인덱스 length-1에 해당하는 요소 모두 삭제
     
     console.log(machines); // [ 'computer', 'car' ]
     ```

     <br>

10. `reverse()`

    - 배열의 순서를 뒤집는다.

    - 원본 배열을 변경한다.

      ```javascript
      let nums = [1, 2, 3, 4, 5];
      nums.reverse();
      console.log(nums); // [ 5, 4, 3, 2, 1 ]
      ```

      <br>

11. `sort([compareFunction])`

    - 배열을 오름차순으로 정렬한다.

    - 배열 안의 요소들을 문자열로 변환하여 비교한다.

      - 따라서 숫자를 비교하려면, `[compareFunction]`을 이용한다.
      - `[compareFunction]`은 비교를 위해 두 개의 `paramter`가 필요하다.

      ```javascript
      let nums = [1, 20, 305, 4, 51, 7];
      nums.sort();
      console.log(nums); // [ 1, 20, 305, 4, 51, 7 ]
      ```

      ```javascript
      /*
      compareFunction 형식(오름차순 정렬)
      
      function comp(a, b){
      	if(a < b) return -1;
      	if(a > b) return 1;
      	return 0;
      }
      */
      
      let nums = [1, 20, 305, 4, 51, 7];
      nums.sort((a,b)=>{
          if(a < b) return -1;
          if(a > b) return 1;
          return 0;
      });
      console.log(nums); // [ 1, 4, 7, 20, 51, 305 ]
      ```

      ```javascript
      // 숫자의 경우, 오름차순 정렬 할 때, return a - b를 이용하여 간단하게 구현 할 수 있다.
      let nums = [1, 20, 305, 4, 51, 7];
      nums.sort((a,b)=>{
      	return a - b;
      });
      console.log(nums); // [ 1, 4, 7, 20, 51, 305 ]
      ```

      

