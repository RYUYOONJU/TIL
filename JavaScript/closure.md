# 인사이드 자바스크립트 P. 155 ~ 159

## 31. 클로저의 개념
생명주기가 끝난 외부 함수의 변수(자유변수)를 참조하는 함수를 클로저라고 한다.
```js
function outerFunc(){
    var x = 10; // 자유변수
    var innerFunc = function(){
        console.log(x);
    } // => 클로저 함수
    return innerFunc;
}

var inner = outerFunc();
inner(); // 출력값 10
```

```js
function outerFunc(arg1, arg2){
    var local = 8;
    function innerFunc (innerArg){
        console.log((arg1 + arg2)/(innerArg + local));
    }
    return innerFunc;
}
var exam1 = outerFunc(2,4);
exam1(2);
```