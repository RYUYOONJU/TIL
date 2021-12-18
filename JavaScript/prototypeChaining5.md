# 인사이드 자바스크립트 P. 129 ~ 131

## 28. 프로토타입 체이닝

### 28.5 기본 데이터 타입 확장
자바스크립트의 숫자, 문자열, 배열 등에서 사용되는 표준 메서드들의 경우, 이들의 프로토타입인 Number.prototype, String.prototype, Array.prototype 등에 정의 되어 있다. 이러한 기본 내장 프로토타입 객체 또한 Object.prototype을 자신의 프로토타입으로 가지고 있어서 프로토타입 체이닝으로 연결된다.
```js
// String 기본 타입에 메서드 추가
String.prototype.testMethod = function(){
    console.log('This is the String.prototype.testMethod()');
};

var str = 'this is test'
str.testMethod();
console.dir(String.prototype);
```
String.prototype 또한 자신의 프로토타입이 있으며 그것이 바로 Object.prototype라는 것이다.