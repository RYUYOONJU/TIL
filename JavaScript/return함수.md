# 인사이드 자바스크립트 P. 98

## 21. 함수를 리턴하는 함수
함수를 호출함과 동시에 다른 함수로 바꾸거나 자기 자신을 재정의 할때 쓰임.

```js
//self() 함수
var self = function(){
    console.log('a');
    return function(){
        console.log('b');
    }
}
self = self(); // 출력값 a
self(); // 출력값 b
```
 1. 처음 self() 함수가 출력될때는 a가 출력된다. 그리고 self에 리턴값이 저장이 된다.
 2. 다시 self()를 호출할땐 b가 호출된다. 