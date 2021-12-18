# 인사이드 자바스크립트 P. 132 ~ 133

## 28. 프로토타입 체이닝

### 28.7 프로토타입 메서드와 this 바인딩
프로토타입 메서드 내부에서 this를 사용한다면 this는 메서드 호출할 때와 같이 바인딩이 된다.

```js
// 프로토타입 메서드와 this 바인딩
    //Person 생성자 함수
    function Person(name){
        this.name = name;
    }

    //getName() 프로토타입 메서드
    Person.prototype.getName = function(){
        return this.name;
    }

    //foo 객체 생성
    var foo = new Person('foo');
    console.log(foo.getName()); // 출력값 foo

    //Person.prototype 객체에 name 프로퍼티 동적 추가
    Person.prototype.name = 'person';

    console.log(Person.prototype.getName()); // 출력값 person
```