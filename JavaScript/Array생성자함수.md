# 인사이드 자바스크립트 P. 64

## 10. Array() 생성자 함수
Array() 생성자 함수는 호출할 때 인자 개수에 따라 동작이 다르므로 주의 하자!<br />
* 호출할 때 인자가 1개이고, 숫자일 경우 : 호출된 인자를 length로 갖는 빈 배열 생성<br />
* 그외의 경우 : 호출된 인자를 요소로 갖는 배열 생성

```js
var foo = new Array(3)
console.log(foo); // 출력값 [undefined x3]
console.log(foo.length) // 출력값 3

var bar = new Array(1,2,3)
console.log(bar); // 출력값 [1,2,3]
console.log(bar.length) // 출력값 3
```