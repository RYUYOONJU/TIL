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

### 2. 함수의 캡슐화
"I'm XXX. I live in XXX. I'm XX years old"라는 문장을 출력하고 싶을때 XXX는 인자로 입력 받아 출력하는 함수를 만들어보자.
```js
var buffAr = [
    'I am',
    '',
    '. I live in',
    '',
    '. I\'m ',
    '',
    ' years old.',
];

function getCompletedStr(name,city,age){
    buffAr[1] = name;
    buffAr[3] = city;
    buffAr[5] = age;

    return buffAr.join('');
}

var str = getCompletedStr('zzoon','seoul',16);
console.log(str);
```
위 예제의 단점은 buffAr가 전역변수로 노출 되어 있어 다른 함수에서 쉽게 접근하여 배열을 바꿀 수 있다.

```js
var getCompletedStr = (function(){
    var buffAr = [
        'I am',
        '',
        '. I live in',
        '',
        '. I\'m ',
        '',
        ' years old.',
    ]; //자유변수

    return (function(name, city, age){
        buffAr[1] = name;
        buffAr[3] = city;
        buffAr[5] = age;

        return buffAr.join('');
    }); // 클로저
})(); //생명주기가 끝난 함수

var str = getCompletedStr('zzoon','seoul',16);
console.log(str);
```


### 3. setTimeout()에 지정되는 함수의 사용자 정의
```js
function callLater(obj, a, b){
    return(function(){
        obj["sum"] = a + b;
        console.log(obj["sum"]);
    });
}

var sumObj = {
    sum : 0
}

var func = callLater(sumObj, 1, 2);
setTimeout(func,500);
```
