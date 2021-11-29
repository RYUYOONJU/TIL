# 인사이드 자바스크립트 P.63

## 10. splice() 배열 메서드

```
splice(start, deleteCount,item...)
• start : 배열에서 시작위치
• deleteCount : start에서 지정한 시작 위치부터 삭제할 요소의 수
• item : 삭제할 위치에 추가할 요소
```
```js
var arr = ['zero', 'one', 'two', 'three'];
arr.splice(2,1) //2번째 인덱스에서부터 1개를 삭제한다.
console.log(arr); // 출력값 ['zero', 'one', 'three']
console.log(arr.length) // 출력값 3
```