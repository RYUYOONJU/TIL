# 인사이드 자바스크립트 P. 118 ~ 120

## 26. 함수 리턴
__자바스크립트 함수는 항상 리턴값을 반환한다.__ <br />
return 문을 사용하지 않았더라도 다음의 규칙으로 항상 리턴값을 반환한다.
1. 일반 함수나 메서드는 리턴값을 지정하지 않을 경우 undefined 값이 리턴된다.
2. 생성자 함수에서 리턴값을 지정하지 않을 경우 생성된 객체가 리턴된다.

<br />

### 1. 일반 함수나 메서드는 리턴값을 지정하지 않을 경우 undefined값이 리턴된다.

```js
// noReturnFunc() 함수
var noReturnFunc = function(){
    console.log('This function has no return statement.');
};

var result = noReturnFunc();
console.log(result); 
// 출력값 This function hs no return , undefined
```

### 2. 생성자 함수에서 리턴값을 지정하지 않을 경우 생성된 객체가 리턴된다.

<br />

생성자 함수에서 별도의 리턴값을 지정하지 않을 경우 this로 바인딩된 새로 생성된 객체가 리턴된다. 때문에 리턴값을 따로 지정하지 않는다.
```js
// Person() 생성자 함수
function Person(name, age, gender){
    this.name = name;
    this.age = age;
    this.gender = gender;

    // 명시적으로 다른 객체 반환
    return {name : 'bar', age : 20, gender : 'woman'};
};

var foo = new Person('foo', 30, 'man');
console.log(foo);
```

<br />

```js
function Person(name, age, gender){
    this.name = name;
    this.age = age;
    this.gender = gender;

    return 100;
};

var foo = new Person('foo', 30, 'man');
console.log(foo);
// 출력값 Person {name : 'foo', age : '30', gender : 'man'}
```
생성자 함수의 리턴값으로 넘긴 값이 객체가 아닌 불린, 숫자, 문자열의 경우는 리턴값을 무시하고 this로 바인딩된 객체가 리턴된다. 