# 인사이드 자바스크립트 P. 54 ~ 62

## 7. 배열의 length
모든 배열은 length 프로퍼티가 있고 length는 원소의 개수를 나타낸다. (실제로 배열에 존재하는 개수와 일치하는것은 아님)<br /> 
__&#8251; 배열 내에 가장 큰 인덱스에 1을 더한 값__
```js
var arr = [];
console.log(arr.length); // 출력값 0

arr[0] = 0; // arr.length = 1
arr[1] = 1; // arr.length = 2
arr[2] = 2; // arr.length = 3
arr[100] = 100;
console.log(arr.length); // 출력값 101
```

### 7.1 length 프로퍼티 명시적 변경
```js
var arr = [0, 1, 2];
console.log(arr.length); // 출력값 3

arr.length = 5;
console.log(arr); // 출력값 [0, 1, 2, undefined x2]

arr.length = 2;
console.log(arr); // 출력값 [0, 1]
console.log(arr[2]); // 출력값 undefined
```

### 7.2 배열 표준 메서드와 length 프로퍼티
자바스트립트는 배열에서 사용 가능한 다양한 메서드를 제공한다. 이러한 메서드들은 length프로퍼티를 기반으로 동작한다.

```js
//arr 배열 생성
var arr = ['zero', 'one', 'two'];

//push()메서드 호출
arr.push('three');
console.log(arr); // 출력값 ['zero', 'one', 'two', 'three']

//length 값 변경 후, push() 메서드 호출
arr.length = 5;
arr.push('four');
console.log(arr) // 출력값 ['zero', 'one', 'two', 'three', undefined, 'four']
```
__&#8251; push 메서드는 배열 메서드이며 배열의 제일 마지막에 원소를 추가하는 메서드 이다.__