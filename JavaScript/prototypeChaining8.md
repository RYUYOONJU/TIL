# 인사이드 자바스크립트 P. 134 ~ 136

## 28. 프로토타입 체이닝

### 28.8 디폴트 프로토타입은 다른 객체로 변경이 가능하다.
디폴트 프로토타입 객체는 함수가 생성될 때 같이 생성되며 함수의 prototype 프로퍼티에 연결 된다. 이렇게 함수를 생성할 때 해당 함수와 연결되는 디폴트 프로토타입 객체를 다른 일반 객체로 변경하는 것이 가능하다.

```js
//프로토타입 객체 변경
    //Person() 생성자 함수
    function Person(name){
        this.name = name;
    }
    console.log(Person.prototype.constructor);
    // 출력값 Person(name)     생성자 함수 본인이 생성자가 된다.

    //foo 객체 생성
    var foo = new Person('foo');
    console.log('foo.country');
    // 출력값 undefined    Person함수에 country 프로퍼티가 없다.

    //디폴트 프로토타입 객체 변경
    Person.prototype = {
        country : 'korea',
    }
    console.log(Person.prototype.constructor);
    // 출력값 Object()    Person 생성자 함수에서 일반 객체로 프로토타입을 변경

    //bar 객체 생성
    var bar = new Person('bar');

    console.log(foo.country); // 출력값 undefined
    console.log(bar.country); // 출력값 korea
    console.log(foo.constructor); // 출력값 Person(name)
    console.log(bar.constructor); // 출력값 Object
```
생성자 함수의 프로토타입 객체가 변경되면 변경된 시점 이후에 생성되 ㄴ객체들은 변경된 프로토타입 객체로 [[Prototype]] 링크를 연결한다.