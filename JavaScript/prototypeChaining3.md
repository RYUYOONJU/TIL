# 인사이드 자바스크립트 P. 126 ~ 127

## 28. 프로토타입 체이닝

### 28.3 생성자 함수로 생성된 객체의 프로토타입 체이닝
자바스크립트에서 모든 객체는 자신을 생성한 생성자 함수의 prototype 프로퍼티가 가리키는 객페를 자신의 프로토타입 객체(부모 객체)로 취급한다.
```js
// 생성자 함수 방식의 프로토타입 체이닝
    //Person 생성자 함수
    function Person(name, age, hobby){
        this.name = name;
        this.age = age;
        this.hobby = hobby;
    }

    //foo 객체 생성
    var foo = new Person('foo', 30, 'tennis');

    //프로토타입 체이닝
    console.log(foo.hasOwnProperty('name')); // true

    //Person.prototype 객페 출력
    console.dir(Person.prototype);
```
myObject가 hasOwnProperty를 호출했는데 에러가 발생하지 않은 이유 : 객체 리터럴로 생성한 객체는 Object()라는 내장 생성자 함수로 생성된 것이므로 Object.prototype 객체의 메서드를 사용할 수 있다.
