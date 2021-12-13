# 인사이드 자바스크립트 P. 101 ~ 102

## 23. 호출 패턴과 this 바인딩
### 23-1. 객체의 메서드 호출할 때 this 바인딩
메서드 :  객체의 프로퍼티가 함수일 경우.
메서드를 호출할 때 메서드 내부 코드에서 사용된 this는 __해당 메서드를 호출한 객체로 바인딩 된다.__
```js
// myObject 객체 생성
var myObject = {
    name : 'foo',
    sayName : function(){
        console.log(this.name);
    }
};

// otherObject 객체 생성
var otherObject = {
    name : 'bar'
}

// otherObject.sayName()메서드
otherObject.sayName = myObject.sayName;

// sayName()메서드 호출
myObject.sayName(); // foo
otherObject.sayName(); // bar
```
this는 자신을 호출한 객체에 바인딩 되므로 각각의 name이 출력이 된다.