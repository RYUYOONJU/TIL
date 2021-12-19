# 인사이드 자바스크립트 P. 139 ~140

## 29. 실행 컨텍스트
콜스택 : 함수를 호출할 때 해당 함수의 호출 정보가 차곡차곡 쌓여 있는 스택 <br />
컨텍스트 : 실행 가능한 자바스크립트 코드 블록이 실행되는 환경 <br />
실행 컨텍스트의 생성 : 현재 실행되는 컨텍스트에서 이 컨텍스트와 관련 없는 실행 코드가 실행되면, 새로운 컨텍스트가 생성되어 스택에 들어가고 제어권이 그 컨텍스트로 이동한다.
```js
console.log('This is global context');

function ExContext1(){
    console.log('This is ExContext1');
};

function ExContext2(){
    ExContext();
    console.log('This is ExContext2');
};

ExContext2();

```