# 인사이드 자바스크립트 P. 132

## 28. 프로토타입 체이닝

### 28.6 프로토타입도 자바스크립트 객체다.
함수가 생성될 때, 자신의 prototype 프로퍼티에 연결되는 프로토타입 객체는 디폴트로 constructor 프로퍼티만을 가진 객체다. 당연히 프로토타입 객체 역시 자바스크립트 객체이므로 일반 객체처럼 동적으로 프로퍼티를 추가/삭제가 가능하다.
```js
// 프로토타입 객체의 동적 메서드 생성 예제 코드
    //Person 생성자 함수
    function Person(name){
        this.name = name;
    }

    //foo 객체 생성
    var foo = new Person('foo');

    //foo.sayHello();     주석 제거 시 에러 발생

    //프로토타입 객체에 sayHello() 메서드 정의
    Person.prototype.sayHello = function(){
        consolelog('Hello');
    }

    foo.sayHello(); // 출력값 Hello
```