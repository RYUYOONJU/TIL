# # 인사이드 자바스크립트 P. 118 

## 25. slice
어떤 배열의 begin부터 end까지(end 미포함)에 대한 얕은 복사본을 새로운 배열 객체로 반환합니다. 원본 배열은 바뀌지 않습니다.

```js
var arrA = [1,2,3];
var arrB = arrA.slice(0); // 출력값 1,2,3
var arrC = arrA.slice(); // 출력값 1,2,3
var arrD = arrA.slice(1); // 출력값 2,3
var arrE = arrA.slice(1,2); // 출력값 2
```