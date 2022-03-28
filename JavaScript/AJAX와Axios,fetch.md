# AJAX와 Axios

## AJAX
AJAX는 Asynchronous JavaScript And XML의 약자로<br />
Javascript를 사용한 비동기 통신, 클라이언트와 서버간에 데이터를 주고 받는 기술<br />
Javascript에서 비동기 HTTP 통신을 하게 해주며 페이지 새로 고침이 일어나지 않는다.<br />

### &#8251; 비동기 HTTP 통신이란?<br />
request와 response를 비동기 식으로 주고 받을 수 있다/<br />
예. 페이스북 좋아요 누를 때 마다 페이지 새로고침이 된다면? <비동기가 아닐 경우>

### 순수 AJAX CODE
```js
// use Ajax without Jquery

function reqListener (e) {
    console.log(e.currentTarget.response);
}

var oReq = new XMLHttpRequest();
var serverAddress = "https://jsonplaceholder.typicode.com/posts";

oReq.addEventListener("load", reqListener);
oReq.open("GET", serverAddress);
oReq.send();

```

### jQuery AJAX CODE
```js
// use Ajax with Jquery

var serverAddress = 'https://jsonplaceholder.typicode.com/posts';

// jQuery의 .get 메소드 사용
$.ajax({
    url: ,
    type: 'GET',
    success: function onData (data) {
        console.log(data);
    },
    error: function onError (error) {
        console.error(error);
    }
});
```

## Axios
Axios는 Promise based HTTP client for the browser and node.js
즉, node.js와 브라우저를 위한 HTTP통신 라이브러리<br />
비동기로 HTTP 통신을 가능하게 해주며 return을 promise 객체로 해주기 때문에 response 데이터를 다루기도 쉽다.<br />

### Axios POSE Method CODE
```js
axios({
  method: 'post',
  url: '/user/12345',
  data: {
    firstName: 'Yongseong',
    lastName: 'Kim'
  }
});
```

## fetch
fetch는 ES6부터 Javascript 내장 함수로 들어왔다.<br />
Promise 기반으로 만들어졌기에 Axios와 마찬가지로 데이터를 다루기 어렵지 않으며, <br />
내장라이브러리로 편리하다.

### fetch POST Method CODE
```js
//fetch
const url ='http://localhost3000/test`
const option ={
   method:'POST',
   header:{
     'Accept':'application/json',
     'Content-Type':'application/json';charset=UTP-8'
  },
  body:JSON.stringify({
  	name:'sewon',
    	age:20
  })

  fetch(url,options)
  	.then(response => console.log(response))
```





