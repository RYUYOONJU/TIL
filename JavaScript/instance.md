# # 인사이드 자바스크립트 P. 114 

## 24. 강제로 인스턴스 생성하기
일반 함수와 생성자 함수의 구분이 별도로 없다. new 연산자를 사용하지 않고 생성자 함수를 호출 하는 경우 에러가 발생한다.

```js
function A(arg) {
    if (!(this instanceof A)) // this == global
        return new A(arg);
    this.value = arg ?? 0;
    // return undefined
}

var a = new A(100);
var b = A(10);

console.log(a.value); // 출력값 100
console.log(b?.value); // 출력값 10
console.log(global.value); // 출력값 undefined

```