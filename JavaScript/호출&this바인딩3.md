# 인사이드 자바스크립트 P. 109 ~ 113

## 23. 호출 패턴과 this 바인딩
### 23-3. 생성자 함수를 호출할 때 this 바인딩
생성자 함수 : 기존 함수에 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작한다. (함수 이름의 첫 문자를 대문자로 쓰기)

<br />

+ __생성자 함수가 동작하는 방식__<br />
new 연산자로 함수를 생성자로 호출하면 다음과 같은 동작으로 동작한다.
    1. 빈 객체 생성 및 this 바인딩<br />
    생성자 함수가 실행되기 전 빈 객체가 생성된다. 하지만 빈 객체는 아니다. 자신의 부모인 프로토타입 객체와 연결되어 있으며 부모 객체의 포로퍼티나 메서드를 자신의 것처럼 사용할 수 있다.
    생성자 함수가 생성한 객체는 자신을 생성한 생성자 함수의 프로토타입 프로퍼티가 가르키는 객체를 자신의 프로토타입 객체로 설정한다.
    2. this를 통한 프로퍼티 생성<br />
    함수 코드 내부에서 this를 사용해서 앞에서 생성된 빈 객체에 동적으로 프로퍼티나 메서드를 생성할 수 있다.
    3. 생성된 객체 리턴<br />
    리턴문이 동작하는 방식은 경우에 따라 다르므로 주의해야 한다. 리턴문이 없을 경우, this로 바인딩된 새로 생성한 객체가 리턴된다.

```js
//Person() 생성자 함수
var Person = function (name){
    //함수 실행 전
    this.name = name;
    //함수 리턴
};

//foo 객체 생성
var foo = new Person('foo');
console.log(foo.name); // 출력값 foo
```

<br />

+ __객체 리터럴 방식과 생성자 함수를 통한 객체 생성 방식의 차이__<br />
객체 리터럴 방식으로 생성된 객체는 같은 형태의 객체를 재생성할 수 없고 생성자 함수를 사용해서 객체를 생성하면 호출할 때 다른 인자를 넘김으로써 같은 형태의 서로 다른 객체를 생성할 수 있다.

```js
// 객체 리터럴 방식으로 foo 객체 생성
var foo = {
    name : 'foo',
    age : 35,
    gender : 'man'
};
console.dir(foo);

// 생성자 함수
function Person(name, age, gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
}

// Person todtjdwk gkatnfmf dldydgo bar, baz 객체 생성
var bar = new Person('bar', 33, 'woman');
console.dir(bar);

var baz = new Person('baz', 25, 'woman');
console.dir(baz);

/* 
출력값

object
age : 35
gender : 'man'
name : 'foo'
__proto__ : Object

Person
age : 33
gender : 'woman'
name : 'bar'
__proto__ : Person

Person
age : 25
gender : 'woman'
name : 'baz'
__proto__ : Person
*/ 
```

<br />

+ __생성자 함수를 new를 붙이지 않고 호출할 경우__
```js
var qux = Person('qux', 20, 'man') //new 연산자 없이 호출
console.log(qux); // 출력값 undefined
console.log(window.name); // 출력값 qux
console.log(window.age); // 출력값 20
console.log(window.gender); // 출력값 man
```
new없이 생성자 함수를 호출 시 this는 전역객체에 바인딩 된다. 그러므로 window 객체에 동적으로 name, age, gender 프로퍼티가 생성된다.

