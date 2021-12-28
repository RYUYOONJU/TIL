# 인사이드 자바스크립트 P. 224

## 34. map
map()함수는 주로 배열에 많이 사용되는 함수이다. <br />
배열의 각 요소를 꺼내 사용자 정의 함수를 적용시켜 새로운 값을 얻은 후<br /> **새로운 배열에 넣는다.**

```js
Array.prototype.map = function(callback){
    /* this가 null인지, 배열인지 체크*/
    /* callback이 함수인지 체크*/

    var obj = this;
    var value, mapped_value;
    var A = new Array(obj.length);

    for(var i = 0; i < obj.length; i++){
        value = obj[i];
        mapped_value = callback.call(null, value);
        A[i] = mapped_value;
    }
    return A;
};

var arr = [1,2,3];
var new_arr = arr.map(function(value){
    return value*value
});

console.log(new_arr); // 출력값 [1, 4, 9]
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