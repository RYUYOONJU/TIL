# 인사이드 자바스크립트 P. 137

## 28. 프로토타입 체이닝

### 28.9 객체의 프로퍼티 읽기나 메서드를 실행할 때만 프로토타입 체이닝이 동작한다.
객체의 특정 프로퍼티를 읽으려고 할 때, 프로퍼티가 해당 객체에 없는 경우 프로토타입 체이닝이 발생한다. 반대로 객체에 있는 특정 프로퍼티에 값을 쓰려고 한다면 이때는 일어나지 않는다. 
```js
// 프로토타입 체이닝과 동적 프로퍼티 생성
    //Person 생성자 함수
    function Person(name){
        this.name = name;
    }

    Person.prototype.country = 'Korea'

    var foo = new Person('foo');
    var bar = new Person('bar');
    console.log(foo.country); // 출력값 Korea
    console.log(bar.country); // 출력값 Korea

    foo.country = 'USA';

    console.log(foo.country); // 출력값 USA
    console.log(bar.country); // 출력값 Korea
```

USA가 출력된 이유는 처음 foo 객체를 생성했을땐 foo객체에 country 프로퍼티가 없어서 체이닝으로 Person 프로퍼티로 가서 찾았다. 그리고 foo 객체에 country 프로퍼티를 동적으로 추가해서 마지막엔 usa로 출력되는 것이다. Person.prototype.country는 그대로 Korea이다.