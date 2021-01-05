# 03. Command

### 1. 조건문

1. `if`, `else if`, `else`

   ```javascript
   /*
   if(조건식1){
   	실행문1;
   }
   else if(조건식2){
   	실행문2;
   }
   else{
   	실행문3;
   }
   */
   
   let x = 7;
   let y = 5;
   
   // x -= y가 실행, 그 외는 모두 실행되지 않음
   if(x > y){
   	x -= y;
   }
   else if(x == y){
   	x = 0;
   }
   else{
   	y -= x;
   }
   ```

   <br>

2. `switch`

   ```javascript
   /*
   switch(표현식){
   	case 1:
   		실행문1;
   		break;
   		
   	case 2:
   		실행문2;
   		break
   	
   	case 3:
   		실행문3;
   		break
   	
   	default:
   		실행문4;
   		break;
   }
   */
   
   let x = 'rice';
   let y = 7;
   
   // switch문에 의해 y === 9
   switch(x){
   	case 'tomato':
   		y += 1;
   		break;
   		
   	case 'rice':
   		y += 2;
   		break;
   	
   	case 'grape':
   		y += 3;
   		break;
   	
   	default:
       	y = 0;
       	break;
   }
   ```

   <br>

<br>

### 2. 반복문

1. `while`

   ```javascript
   /*
   초기값;
   while(조건식){
   	실행문;
   	증감식;
   }
   */
   
   let i = 0;
   let sum = 0;
   
   // sum === 55
   while(i < 11){
   	sum += i;
   	i++;
   }
   ```

    <br>

2. `do while`

   - while문은 조건을 만족해야만 실행문을 실행하지만, do while문은 실행을 먼저하고 그 다음에 조건을 고려한다.

   ```javascript
   /*
   초기값;
   do{
   	실행문;
   	증감식;
   }while(조건식);
   */
   
   let i = 0;
   let sum = 0;
   
   // sum === 55 
   do{
   	sum += i;
   	i++;
   }while(i < 11);
   ```

   <br>

3. `for`

   ```javascript
   /*
   for(초기값; 조건식; 증감식){
   	실핼문;
   }
   */
   
   let sum = 0;
   
   // sum === 55
   for(i=0; i<11; i++){
   	sum += i;
   }
   ```

   <br>

4. `continue, break`

   - `continue` : 반복문안에 있는 실행문의 일부만 실행하고 싶을 때. 조건식을 이용해서 사용한다.

     ```javascript
     let sum = 0;
     let i;
     
     // sum === 25(1 + 3 + 5 + 7 + 9)
     for(i = 0; i < 11; i++){
     	if(i % 2 == 0) continue;
     	sum += i;
     }
     ```

     <br>

   - `break` : 반복문 전부 돌지 않고 중간에 빠져나오고 싶을 때, 조건식을 이용해서 사용한다.

     ```javascript
     let sum = 0;
     let i;
     
     // sum === 10(0 + 1 + 2 + 3 + 4)
     for(i = 0; i < 11; i++){
     	if(i == 5) break;
     	sum += i;
     }
     ```

     

