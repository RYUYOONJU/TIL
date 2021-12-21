# 인사이드 자바스크립트 P. 155 ~ 159

## 32. 클로저의 활용
1. 특정함수에 사용자가 정의한 객체의 메서드 연결하기
2. 함수의 캡슐화
3. setTimeout()에 지정되는 함수의 사용자 정의

### 1. 특정함수에 사용자가 정의한 객체의 메서드 연결하기
```js
function HelloFunc(){
    this.greeting = 'Hello';
}

HelloFunc.prototype.call = function(func){
    func ? func(this.greeting) : this.func(this.greeting)
}

var userFunc = function(greeting){
    console.log(greeting);
}

var objHello = new HelloFunc()
objHello.func = userFunc;
objHello.call();
```

```js
function saySomething(obj, methodName, name){
    return (function(greeting){
        return obj[methodName](greeting, name);
    });
}

function newObj(obj, name){
    obj.func = saySomething(this,"who",name)
}

newObj.prototype.who = function(greeting,name){
    console.log(greeting + " " + (name|| "everyone"));
}

var obj1 = new newObj(objHello, "zzoon");
obj.func = saySomething(this, "who", name);

```