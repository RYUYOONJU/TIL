# 인사이드 자바스크립트 P. 124 ~ 125

## 28. 프로토타입 체이닝

### 28.2 객체 리터럴 방식으로 생성된 프로토타입 체이닝
자바스크립트 객체는 자기 자신의 프로퍼티뿐만 아니라 부모 역할을 하는 프로토타입 객체의 프로퍼티에도 접근이 가능하다. 이것이 __프로토타입 체이닝__ 이다. <br /> 원리 : 해당 객체에 접근하려는 프로퍼티나 메서드가 없으면 부모 객체의 프로퍼티를 검색한다.
```js
// 객체 리터럴 방식의 프로토타입 체이닝
    var myObject = {
        name : 'foo',
        sayName : function(){
            console.log('My name is' + this.name)
        }
    };

    myObject.sayName(); // 출력값 My name is foo
    console.log(myObject.hasOwnProperty('name')); // true
    console.log(myObject.hasOwnProperty('NickName')); // false
    myObject.sayNickName(); //Object #<Object> has no method'sayNickName'


* hasOwnProperty()메서드 : 호출한 객체가 인자로 넘긴 문자열 이름의 프로퍼티나 메서드가 있는지 체크하는 자바스크립트 표준 API
```
myObject가 hasOwnProperty를 호출했는데 에러가 발생하지 않은 이유 : 객체 리터럴로 생성한 객체는 Object()라는 내장 생성자 함수로 생성된 것이므로 Object.prototype 객체의 메서드를 사용할 수 있다.
