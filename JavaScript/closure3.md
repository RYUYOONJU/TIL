# 인사이드 자바스크립트 P. 155 ~ 159

## 33. 클로저의 활용할 때 주의사항 

### 1. 클로저의 프로퍼티값이 쓰기 가능하므로 그 값이 여러번 호출로 항상 변할 수 있음에 유의해야 한다.

```js
function outerFunc(argNum){
    var num = argNum;
    return function(x){
        num += x;
        console.log('num: '+ num);
    }
}

var exam = outerFunc(40)
exam(5); // 45
exam(-10); // 35
```
exam 값을 호출할 때마다 자유변수 num값은 계속해서 변한다.


<br />


### 2. 하나의 클로저가 여러 함수 객체의 스코프 체인에 들어가 있는 경우도 있다.

```js
function func(){
    var x = 1;
    return{
        func1 : function(){console.log(++x);},
        func2 : function(){console.log(-x);}
    }
}

var exam = func();
exam.func1();
exam.func2();

```
func1, func2 두 함수 모두 자유변수 x를 참조한다. 각각의 함수가 호출될 때마다 x값이 변한다.


<br />


### 3. 루프 안에서 클로저를 활용할 때는 주의하자
```js
function countSeconds(howMany){
    for(var i = 1; i <= howMany; i++){
        setTimeout(function(){
            console.log(i);
        }i*1000); 
        // setTiimeout 함수 인자로 들어가는 함수는 자유변수 i를 참조한다.
        // countSeconds(), 즉 외부함수가 종료되고 i 값은 이미 4가 된 이후에 setTimeout이 실행되어 4가 출력된다.
    }
}
countSeconds(3)
```

```js
function countSeconds(howMany){
    for(var i = 1; i <= howMany; i++){
        (function(currentI){
            setTimeout(function(){
                console.log(currentI)
            }currentI*1000)
        }(i));
    }
}

countSeconds(3);
```
즉시 실행 함수를 실행시켜 루프 i 값을 currentI에 복사해서 setTimeout에 들어갈 함수에서 사용하면 원하는 값을 얻을 수 있다.
