# 인사이드 자바스크립트 P. 99 ~ 101

## 22. arguments 객체
매개변수, 파라미터라고도 하며 값이 들어갔을땐 인자, arguments라고 한다.
```js
function func(arg1, arg2){
    console.log(arg1, arg2);
}

func(); // 출력값 undefined undefined 
func(1); // 출력값 1, undefined
func(1,2); // 출력값 1, 2
func(1,2,3); // 출력값 1, 2{}
```
arguments 객체는 함수를 호출할 때 넘긴 인자들이 배열 형태로 저장된 객체를 의미한다. (실제 배열이 아닌 유사 배열 객체)<br />
배열 메서드 사용 시 에러 발생.

```js
//add 함수
function add(a,b){
    //arguments 객체 출력
    console.dir(arguments);
    return a + b;
}

console.log(add(1)); // 출력값 NaN (1 + undefined)
console.log(add(1,2)); // 출력값 3
console.log(add(1,2,3)); // 출력값 3
```

arguments 객체는 다음과 같이 세 부분으로 구성되어 있다.(__ proto __ 프로퍼티는 제외)
+ 함수를 호풀할 때 넘겨진 인자(배열형태)
+ length 프로퍼티 : 호출할 때 넘겨진 인자의 개수
+ callee 프로퍼티 : 현재 실행중인 함수의 참조값

