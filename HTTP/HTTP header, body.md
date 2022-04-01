# HTTP의 header와 body
## HTTP의 구조
HTTP 헤더와 본문으로 구성되어 있다. HTTP 본문에는 실제로 통신과정에서 주고 받을 컨텐츠가 담겨져 있다. 

HTTP헤더는 HTTP메시지(request/response)와 본문에 대한 정보를 말해주고 있다. <br />
해당 메시지가 제공하는 기능에 대한 최소한의 정보가 정리된 요약본이다. 

## 1. 공통헤더
 - 요청과 응답에 모두 사용되는 헤더

### 1.1 Date
HTTP 메시지가 만들어진 시각

### 1.2 Connection
일반적으로 HTTP/1.1을 사용하며 Connection은 기본적으로 keep-alive로 되어있다.

### 1.3 Content-Length
요청과 응답 메시지의 본문 크기를 바이트 단위로 표시. 메시지 크기에 따라 자동으로 만들어진다.

### 1.4 Cache-Control
웹 뷰에서, 일반 모바일 브라우저에서 304라는 응답 코드를 주면 이녀석을 의심 해보자.

### 1.5 Content-Type
컨텐츠의 타입(MIME)과 문자열 인코딩(utf-8 등등)을 명시할 수 있다.

### 1.6 Content-Language
사용자의 언어. ex) ko, ja, en

### 1.7 Content-Encoding
응답 컨텐츠를 br, gzip, deflate 등의 알고리즘으로 압축해서 보내면, 브라우저가 알아서 해제해서 사용한다.


## 2. 요청헤더

### 2.1 Host
서버의 도메인 네임.
Host 헤더는 반드시 하나가 존재해야 한다.

### 2.2 User-Agent
가장 흔하게 보고 사용하는 헤더이다. 
현재 사용자가 어떤 클라이언트(운영체제, 앱, 브라우저 등)를 통해 요청을 보냈는지 알 수 있다.

### 2.3 Accept
클라이언트가 허용할 수 있는 파일 형식(MIME TYPE)

ex1) Accept: text/html (HTML 형식인 응답을 처리하겠다)

ex2) Accept: image/png, image/gif

ex3) Accept: text/*
콤마로 여러 타입을 동시에 적어줄 수도 있고, *(와일드카드)로 텍스트면 ok라고 요청할 수 있다.

ex4)
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate
Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7

### 2.4 Cookie
웹서버가 클라이언트에 쿠키를 저장해 놓았다면 해당 쿠키의 정보를 이름-값 쌍으로 웹서버에 전송한다.

### 2.5 Origin
POST같은 요청을 보낼 때, 요청이 어느 주소에서 시작되었는지를 나타내는데 이때 보낸 주소와 받는 주소가 다르면 CORS 문제가 발생하기도 한다.

&#8251; CORS란?

### 2.6 If-Modified-Since
페이지가 수정되었으면 최신 버전 페이지 요청을 위한 필드

### 2.7 Authorization
Authorization 헤더는 인증 토큰을 서버로 보낼 때 사용하는 헤더.
API 요청같은 것을 할 때 토큰이 없으면 거절당하기 때문에 이 때, Authorization을 사용한다.
JWT(Json Web Token) 을 사용한 인증에서 주로 사용 한다.
ex) Authorization: Bearer xxx.xxx.xxx


## 3. 응답헤더

### 3.1 Server
웹서버 정보를 나타낸다.

### 3.2 Access-Control-Allow-Origin
요청 Host와 응답 Host가 다르면 CORS 에러가 발생하는데 서버에서 응답 메시지 Access-Control-Allow-Origin 헤더에 프론트 주소를 적어주면 에러가 발생하지 않는다.
ex) Access-Control-Allow-Origin: goddaehee.tistory.com

#### 관련 헤더
 - Access-Control-Request-Method : 실제로 보내려는 메서드
 - Access-Control-Request-Headers : 실제로 보내려는 헤더
 - Access-Control-Allow-Methods : 서버가 허용하는 메서드
 - Access-Control-Allow-Headers : 서버가 허용하는 헤더

### 3.3 Allow
Allow 헤더는 CORS 요청 외에도 적용된다.
ex) Allow: GET
위와 같은 경우는 GET 요청만 받는다. POST 와 같은 경우는 405 Method Not Allowed 에러 Return 한다.

### 3.4 Content-Disposition
응답 본문을 브라우저가 어떻게 표시해야 할지 알려주는 헤더.
 - inline : 웹페이지 화면에 표시
 - attachment : 다운로드

### 3.5 Location
300번대 응답이나 201 Created 응답일 때 어느 페이지로 이동할지를 알려주는 헤더

ex ) HTTP/1.1 302 Found
     Location: /login
위와 같은 응답시 브라우저는 /login 주소로 리다이렉트합니다.

### 3.6 Content-Security-Policy
다른 외부 파일들을 불러오는 경우, 차단할 소스와 불러올 소스를 여기에 명시할 수 있다.
하나의 웹 페이지는 다양한 외부 소스들을 불러온다. (이미지, JS, CSS, 폰트, 아이프레임 등) 

ex) Content-Security-Policy: default-src 'self' (자신의 도메인의 파일들만 가져올 수 있다)
    Content-Security-Policy: default-src https: (https를 통해서만 파일을 가져올 수 있다)
    Content-Security-Policy: default-src 'none' (못가져 오게 만듬)
https:로 지정하면 https를 통해서만 파일을 가져올 수 있게 됩니다. 'none'으로 지정하면 가져올 수 없습니다.


