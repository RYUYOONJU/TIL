# 인사이드 자바스크립트 P. 141 ~ 146

## 30. 스코프 체인
함수 스코프에서 먼저 찾고 함수스코프에 값이 없으면 외부 스코프에서 찾는다,

### 30.1 전역 실행 컨텍스트의 스코프 체인
```js
var var1 = 1;
var var2 = 2;
console.log(var1); // 출력값 1
console.log(var2); // 출력값 2
```

### 30.2 함수를 호출한 경우 생성되는 실행 컨텍스트의 스코프 체인
```js
var var1 = 1;
var var2 = 2;
function func(){
    var var1 = 10;
    var var2 = 20;
    console.log(var1); // 출력값 10  
    console.log(var2); // 출력값 20
}

fucn();
console.log(var1); // 출력값 1
console.log(var2); // 출력값 2
```
```js
var value = "value1";
function printFunc(){
    var value = "value2";

    function printValue(){
        return value;
    }
    console.log(printValue());
}

printFunc(); // 출력값 value2
```
```js
var value = "value1";

function printValue(){
    return value;
}
function printFunc(func){
    var value = "value2";
    console.log(func());
}
printFunc(printValue);

// printFunc는 printValue를 시작하는 함수이며 그 다음 printValue가 실행된다.
```