# 인사이드 자바스크립트 P. 224

## 35. reduce
reduce()는 배열의 각 요소를 하나씩 꺼내서 사용자의 함수를 적용시킨 뒤 그 값을 계속 누적시키는 함수이다.

```js
Array.prototype.reduce = function(callback,memo){
    /* this가 null인지, 배열인지 체크*/
    /* callback이 함수인지 체크*/

    var obj = this;
    var value, accumulated_value = 0;
    var A = new Array(obj.length);
    console.log(this)
    for(var i = 0; i < obj.length; i++){
        value = obj[i];
        accumulated_value = callback.call(null, accumulated_vaalue, value);
    }
    return accumulated_value;
};

var arr = [1,2,3];
var accumulated_val = arr.reduce(function(a,b){
    return a+b*b
});

console.log(accumulated_val); // 출력값 14
```

```js
Object.prototype.map = function (callback, thisArg) {
  var callback = callback.bind(thisArg);
  let result = [];
  for (let i = 0; i < this.length; i++) {
    mapped = callback(this[i], i, this);
    result.push(mapped);
  }
  return result;
}

function reduceTest() {
  // pass a function to map
  const map1 = arguments.map(x => x * 2);

  console.log(map1);
  // expected output: Array [2, 8, 18, 32]
}

reduceTest(1, 4, 9, 16)
console.log([1, 4, 9, 16].map((x, i, arr) => x * 2));
```
```js
Object.prototype.reduce = function (callback, initialValue) {
    let accumulator = initialValue ?? this[0];
     // initialValue != null ? initialValue : this[0];
    let i = initialValue ? 0 : 1;
    while (i < this.length) {
        accumulator = callback(accumulator, this[i], i, this);
        i += 1;
    }
    return accumulator;
};

const reducer = (previousValue, currentValue) => previousValue + currentValue;

function reduceTest() {
    // 1 + 2 + 3 + 4
    console.log(arguments.reduce(reducer));
    // expected output: 10

    // 5 + 1 + 2 + 3 + 4
    console.log(arguments.reduce(reducer, 5));
    // expected output: 15
}

reduceTest(1, 2, 3, 4);
```