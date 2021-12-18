# 인사이드 자바스크립트 P. 128

## 28. 프로토타입 체이닝

### 28.4 프로토타입 체이닝의 종점
자바스크립트에서 Object.prototype 객체는 __프로토타입 체이닝의 종점이다.__ <br /> 객체 리터럴 방식이나 생성자 함수를 이용한 방식이나 결국엔 Object.prototype에서 프로토타입 체이닝이 끝난다. <br />
결국 방식에 상관없이 모든 자바스크립트 객체는 Object.prototype 객체가 가진 프로퍼티와 메서드에 접근하고 공유가 가능하다.
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
