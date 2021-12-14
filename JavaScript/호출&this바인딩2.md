# 인사이드 자바스크립트 P. 103 ~ 108

## 23. 호출 패턴과 this 바인딩
### 23-2. 함수를 호출할 때 this 바인딩

함수에서 호출하면 함수 내부 코드에서 사용된 this는 **전역 객체(window)로 바인딩 된다.**

```js
var foo = "I'm foo"; // 전역 변수 선언
console.log(foo); // 출력값 I'm foo
console.log(window.foo); // 출력값 I'm foo
```

```js
var test = "This is test";
console.log(window.test); // This is test

//sayFoo()함수
var sayFoo = function () {
  console.log(this.test); // sayFoo() 함수 호출 시 this는 전역 객체에 바인딩 된다.
};

sayFoo(); // This is test
```

<br />

#### ★ 내부함수의 this 바인딩 예시1

```js
//전역 변수 value 정의
var value = 100;

//myObject 객체 생성
var myObject = {
    value : 1,
    func1 : function(){
        this.value += 1
        console.log('func1() called. this.value : ' + this.value);

        //func2() 내부 함수
        func2 = function(){
            this.value += 1
            console.log('func2() called. this.value : ' + this.value);

            //func3() 내부 함수
            func3 = function(){
                this.value += 1
                console.log('func3() called. this.value : ' + this.value))
            }
            func3(); // 3번 내부 함수 호출
        }
        func2(); // 2번 내부 함수 호출
    }
};
myobject.func1(); // 1번 메서드 호출

// 결과값 2, 101, 102
```

1번 함수는 myObject의 메서드라 자신을 호출한 myObject에 this가 바인딩이 되었고 나머지 2,3번은 내부 함수라 (내부 함수도 함수이기 때문.) 전역 객체에 바인딩이 되었다. 

#### ★ 내부함수의 this 바인딩 예시2

```js
//전역 변수 value 정의
var value = 100;

//myObject 객체 생성
var myObject = {
    value : 1,
    func1 : function(){
        var that = this

        this.value += 1
        console.log('func1() called. this.value : ' + this.value);

        //func2() 내부 함수
        func2 = function(){
            that.value += 1
            console.log('func2() called. this.value : ' + that.value);

            //func3() 내부 함수
            func3 = function(){
                that.value += 1
                console.log('func3() called. this.value : ' + that.value))
            }
            func3(); // 3번 내부 함수 호출
        }
        func2(); // 2번 내부 함수 호출
    }
};
myobject.func1(); // 1번 메서드 호출

// 결과값 2, 3, 4
```