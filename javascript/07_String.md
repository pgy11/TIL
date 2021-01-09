# 07. String

### 1. 문자열(String)

- `String` 객체는 일련의 문자들을 표현하거나 조작 할 때, 사용된다.

  - text 형식의 데이터를 저장 할 때 유용

  <br>

- `string` 객체 생성 방법

  ```javascript
  let str1 = new String('Hello JS');
  console.log(str1); // [String: 'Hello JS']
  console.log(str1.toString()); // Hello JS
  
  let str2 = 'Hello JS';
  console.log(str2); // Hello JS
  ```

  <br>

- 프로퍼티 `length`를 이용하여 문자열의 길이를 알 수 있다.

  - `length`를 조작해도 `string` 객체의 내용이나 길이가 변하지 않는다.

  ```javascript
  let str = 'Hello JS';
  console.log(str.length); // 8
  
  str.length = 4; // length의 변화가 생겼지만, string 객체에서 아무일도 일어나지 않는다.
  console.log(str.length); // 8
  console.log(str); // Hello JS
  ```

  <br>

<br>

### 2. String 객체에서 제공하는 메소드

- 알아두면 유용한 메소드들 위주로 작성

1. `charAt([index])` 

   - 인덱스 `index`에 해당하는 문자(요소)를 반환한다.
   - `index`가 주어지지 않으면, 인덱스 0에 해당하는 문자를 반환한다.
   - `index` 값이 문자열 범위 밖의 값인 경우, `charAt()`은 빈 문자열을 반환한다.

   ```javascript
   let str = 'Hello JS';
   console.log(str.charAt(2)); // l
   console.log(str.charAt()); // H
   console.log(str.charAt(99)); // 빈 문자열('') 
   console.log(str.charAt(-1)); // 빈 문자열('')
   ```

   <br>

2. `indexOf(searchValue [, fromIndex])`

   - `searchValue`는 찾고 싶은 문자, 또는 문자열. 문자열 안에 `searchValue`가 있으면 이에 해당하는 인덱스 반환한다.

     - 문자열 안에 `searchValue`가 여러개 있으면, 첫번째로 발견한 문자에 해당하는  인덱스 반환한다.
     - 찾고 싶은 문자가 문자열 안에 없으면, -1 반환한다.
     - `searchValue`가 문자열로 주어진 경우, `searchValue`의 첫번째 문자에 해당하는 문자열의 인덱스를 반환한다.

     <br>

   - `fromIndex`는 문자열 안에서 찾기 시작하는 위치(인덱스)

     - `fromIndex`가 3이면, 문자열의 인덱스 3부터 시작하여, 찾고 싶은 문자를 탐색한다.
     - `searchValue`가 빈 문자열이고, `fromIndex`가 문자열의 길이와 같거나 크면, `indexOf()`는 문자열의 길이를 반환한다.
     - `searchValue`가 빈 문자열이고, `fromIndex`가 문자열의 길이보다 작거나 같으면 `indexOf()`는 `fromIndex`를 반환한다.
     - `fromIndex`가 음의 값이면, 인덱스 0부터 탐색 시작한다.

     <br>

   ```javascript
   let str = 'Hello JS';
   console.log(str.indexOf('l')); // 2
   console.log(str.indexOf('l', 3)); // 3
   console.log(str.indexOf('W')); // -1
   console.log(str.indexOf('JS')); // 6
   
   console.log(str.indexOf('', 8)); // 8
   console.log(str.indexOf('', 50)); // 8
   
   console.log(str.indexOf('', 3)); // 3
   console.log(str.indexOf('', 6)); // 6
   
   console.log(str.indexOf('l', -2)); // 2
   ```

   <br>

3. `lastIndexOf(searchValue[, fromIndex])`

   - 하는 일은 `indexOf()`와 같지만, `searchValue`를 찾기 위해, 마지막 인덱스부터 탐색한다. 

   - `searchValue`가 빈 문자열일 경우, `fromIndex`를 반환한다.

     - `fromIndex`가 음의 값이면 0을 반환
     - `fromIndex`가 문자열의 길이보다 크면, 문자열의 길이를 반환

     <br>

   - `fromIndex`의 기본 값은 `+infinity`이다.

     - 마지막 인덱스부터 첫번째 인덱스까지 탐색한다.
     - `fromIndex`가 음의 값이면 첫번째 인덱스만 확인한다.

   ```javascript
   let str = 'Hello JS';
   console.log(str.lastIndexOf('l')); // 3
   console.log(str.lastIndexOf('l', 2)); // 2
   console.log(str.lastIndexOf('JS')); // 6
   console.log(str.lastIndexOf('w')); // -1
   
   console.log(str.lastIndexOf('', 3)); // 3
   console.log(str.lastIndexOf('', 17)); // 8
   console.log(str.lastIndexOf('', -1)); // 0
   
   console.log(str.lastIndexOf('J', 23)); // 6
   console.log(str.lastIndexOf('H', -1)); // 0
   console.log(str.lastIndexOf('H', 0)); // 0
   ```

   <br>

4. `includes(searchString[, position])`

   - ECMAScript 2015에서 추가된 메소드
   - `includes()`는 문자열이 다른 문자열에 존재하는지 확인해주고 존재하면 `true` 없으면 `false` 반환한다.
   - `searchString`은 찾고자하는 문자열이다.
   - `position`은 찾고자 하는 위치(인덱스)다. 기본 값은 0이다.

   ```javascript
   let str = 'I study JavaScript hard';
   let w1 = 'JavaScript';
   let w2 = 'javascript';
   
   // str은 w1을 포함한다.(str은 w1의 문자열을 갖고 있다.)
   console.log(str.includes(w1)); // true
   
   // str은 w2를 포함하지 않는다.(str은 w2의 문자열을 갖고 있지 않다.)
   console.log(str.includes(w2)); // false
   
   // w1은 str를 포함하지 않는다.(w1은 str의 문자열을 갖고 있지 않다.)
   console.log(w1.includes(str)); // false
   ```

   <br>

5. `toLowerCase()`

   - 문자열의 모든 문자들을 소문자로 변경하고 반환한다.

   ```javascript
   let str = 'Hello JS';
   let changed = str.toLowerCase();
   console.log(str); // Hello JS
   console.log(changed); // hello js
   ```

   <br>

6. `toUpperCase()`

   - 문자열의 모든 문자들을 대문자로 변경하고 반환한다.

   ```javascript
   let str = 'Hello JS';
   let changed = str.toUpperCase();
   console.log(str); // Hello JS
   console.log(changed); // HELLO JS
   ```

   <br>

7. `concat(str2 [, ...strN])`

   - 문자열 또는 문자열들을 이어붙이고 결과를 반환한다.
   - 주어진 `parameter`가 `string` 타입이 아니면 `string` 타입으로 변환한 후 이어붙인다. 

   ```javascript
   let str1 = 'I study'
   let str2 = ' javascript'
   let str3 = ' hard';
   
   let result = str1.concat(str2);
   console.log(result); // I study javascript
   
   result = str1.concat(str2, str3);
   console.log(result); // I study javascript hard
   ```

   ```javascript
   let src = 'hello '
   let data = [1, true, 'js', [7,8]];
   
   let result = src.concat(data);
   console.log(result); // hello 1,true,js,7,8
   ```

   <br>

8. `replace(regexp|substr, newSubstr|function)`

   - 문자열의 `substr`들을 `newSubstr`로 대채하고 그 결과를 반환한다.
     - 문자열 안에 여러개의 `substr`이 있으면, 그 중 첫번째만 변경한다.
   - 정규식, 함수를 `paramter`로 줄 수 있다.(여기서는 다루지 않는다.)

   ```javascript
   let str = 'abc789abc';
   let result = str.replace('a', 'w');
   console.log(result); // wbc789abc
   
   result = str.replace('abc', 'hello');
   console.log(result); // hello789abc
   
   result = str.replace('quiz', 'apple'); // nothing changed.
   console.log(result); // abc789abc
   ```

    <br>
   
9. `substring(indexStart[, indexEnd])`

   - 인덱스 `indexStart`부터 인덱스 `indexEnd-1`에 해당하는 문자들을 문자열로 반환한다.
   - `indexEnd`의 값이 주어지지 않으면 인덱스 `indexStart`부터 인덱스 `length - 1`에 해당하는 문자들을 문자열로 반환한다.
   - `indexStart === indexEnd`일 경우, 빈 문자열을 반환한다.
   - `indexStart > indexEnd`일 경우, 이들의 값이 서로 바뀌고 이후 `substring()`을 수행한다.
   - 음의 값이 `paramter`에 주어지면, 0으로 대체되고, `substring()`을 수행한다.
   - 문자열의 길이보다 큰 값이 `parameter`에 주어지면, 문자열의 길이로 대체대고, `substring()`을 수행된다.
   - `paramter`의 값이 `NaN`이면, 0으로 대체되고, `substring()`을 수행한다.

   ```javascript
   let str = 'abcd';
   console.log(0,2); // ab
   console.log(2); // cd
   
   console.log(1,1); // 빈 문자열('')
   console.log(4,0); // abcd
   console.log(-1,3); // abc
   
   console.log(2,7); // cd
   console.log('pq', 4); // abcd
   
   //true == 1, true !== 1 -> true가 1로 변환
   console.log(true, 4); // bcd
   ```

   <br>

10. `substr(start[, length])`

    - 인덱스 `start`시작하여 `length`개 문자들을 문자열로 반환한다.
    - `substr()`은 ECMAScript에서 legacy feature이기 때문에, 향후 버전에서는 지원을 하지 않을 수도 있다. 따라서 사용하지 않는 것을 권장한다.
    - 혹시 내가 사용 할 까봐 여기에 기록을 남겨둔다.

    <br>

11. `split([separator[, limit]])`

    - `separator`를 기준으로 문자열들을 쪼개고 이들을 배열에 넣고, 배열을 반환한다.

      - `separator`에 정규식이 올 수 있다.
      - 문자열을 `separator`에 넣고 `split()`을 수행 할 수 있다.
      - `sparator`에 값을 생략하거나, 문자열에 `sparator`를 찾을 수 없으면, 전체 문자열을 배열에 넣고, 배열을 반환한다
      - `sprator === ''`이면, 문자열들을 문자들로 쪼개고 배열에 넣어서 배열을 반환한다.
        - 문자열의 각 문자들은 `UTF-16`에 속하는 문자들이여야 한다.

      <br>

    - 음이 아닌 값을 `limit`에 주면, `split()`으로 인해 쪼개진 문자들의 수를 제한한다.

    - `limit === 0`이면 `[]`을 반환한다.

    ```javascript
    let str = 'abcd';
    console.log(str.split('b')); // [ 'a', 'cd' ]
    console.log(str.split('a')); // [ '', 'bcd' ]
    console.log(str.split('bc')); // [ 'a', 'd' ]
    
    console.log(str.split()); // [ 'abcd' ]
    console.log(str.split('k')); // [ 'abcd' ]
    
    console.log(str.split('')); // [ 'a', 'b', 'c', 'd' ]
    
    console.log(str.split('', 2)); // [ 'a', 'b' ]
    console.log(str.split('c', 0)); // []
    ```

    <br>

12. `trim()`

    - 문자열의 앞 뒤 공백을 제거한다.

    ```javascript
    let str = ' Hello JS ';
    console.log(str.trim() + '!!'); // Hello JS!!
    
    str = '  Hello JS  ';
    console.log(str.trim() + '!!'); // Hello JS!!
    ```

    

