# 인사이드 자바스크립트 p. 114

```js
function A(arg) {
    if (!(this instanceof A)) // this == global
        return new A(arg);
    this.value = arg ?? 0;
    // return undefined
}

var a = new A(100);
var b = A(10);

console.log(a.value);
console.log(b?.value);
console.log(global.value);
```
