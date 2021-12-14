# 인사이드 자바스크립트 P. 115 ~ 118

## 23. 호출 패턴과 this 바인딩
### 23-4. call과 apply 메서드를 이용한 명시적 this 바인딩
지금까지는 함수 호출이 발생할 때 상황에 따라 this가 정해진 객체에 자동으로 바인딩이 되는 예제 였다면 call과 apply 메서드를 활용해 명시적 바인딩이 가능하다.

&#8251; call과 apply의 차이점은 call() 은 함수에 전달될 인수 리스트를 받는데 비해, apply() 는 인수들의 단일 배열을 받는다는 점이다.

```js
// 생성자 함수
function Person(name, age, gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
}

// foo 빈 객체 생성
var foo = {};

//apply() 메서드 호출
Person.apply(foo,['foo', 30, 'man']);
console.dir(foo);
```


```js

// Object.prototype.slice = Array.prototype.slice // 모든 객체에 바인딩

Object.assign(Object.prototype, {
    slice: Array.prototype.slice,
    log: console.log.bind(this)
});

//apply 메서드를 활용한 arguments 객체의 배열 표준 메서드 silce 활용코드
function yes() {
    // Object.assign(arguments['[[Prototype]]'].__proto__, Array.prototype);
    console.dir(arguments);
    //arguments.shift();

    //arguments 객체를 배열로 변환
    // arguments.slice = Array.prototype.slice.apply(arguments); // 일시적으로 바인딩
    var args = arguments.slice();
    console.dir(args);
}

yes(1, 2, 3);

console.log([1, 2, 3].slice());
```
