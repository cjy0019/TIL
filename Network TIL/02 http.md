# 네트워크 TIL 😎



## 1. HTTP

HTML(HyperText Markup Language) 문서를 교환하기 위해 만들어진 프로토콜이다. HTTP를 사용하여 통신을 하는 경우 반드시 한 쪽은 클라이언트 한 쪽은 서버가 된다. 일반적으로 클라이언트는 프론트엔드, 서버는 백엔드라고 칭한다.

한줄로 정리해보자면, **HTTP는 클라이언트와 서버의 역할을 명확하게 구분해주고 브라우저와 서버가 데이터를 어떻게 주고 받을지에 대한 통신 규약이라고 할 수 있겠다.**



## 2. HTTP Request & HTTP Response

HTTP 프로토콜을 사용하여 데이터를 주고 받기 위해서는 반드시 **요청과 응답이 존재해야한다.** 즉, 클라이언트 사이드에서 리퀘스트 없이 리스폰스를 받는 경우와 서버 사이드에서 리퀘스트의 수신없이 리스폰스가 발생하는 경우는 절대 없다.

<img src="https://mdn.mozillademos.org/files/8659/web-server.svg" width="70%"/>

[이미지 출처-MDN](https://developer.mozilla.org/ko/docs/Learn/Common_questions/What_is_a_web_server)



### 2.1 HTTP 메시지의 구성

리퀘스트 메시지는 **메소드, URI, 프로토콜 버전, 옵션 리퀘스트 헤더 필드, 엔티티로 구성되어 있다.**

**Request Message**

Request Header + 빈 줄 + Request Body

- Header 
  - 첫 번째 줄
    - 요청 메서드 + 요청 URI + HTTP 프로토콜 버전
  - 두 번째 줄
    - Header 정보('Header Name : Header Value' 형태)
- 빈 줄
  - 요청에 대한 모든 메타 정보가 전송되었음을 알림.
- Body
  - POST, PUT의 경우에만 존재
  - 요청과 관련된 내용 (ex. HTML 폼 태그)

```http
POST /form/entry HTTP/1.1
HOST: hackr.jp
Connection : keep-alive
Content-Type : application/x-www-form-urlencoded
Content-Length : 16

name=ueno&age=37
```



**Response Message**

Response Header + 빈 줄 + Response Body

- Header
  - 첫 번째 줄
    - HTTP 프로토콜 + 응답 코드 + 응답 메시지
  - 두 번째 줄
    - Header 정보('Header Name : Header Value')
      - 날짜, 웹 서버 이름, 웹 서버 버전, 콘텐츠 타입, 콘텐츠 길이, 캐시 제어 방식 등
- 빈 줄(empty-line)
  - 요청에 대한 모든 메타 정보가 전송되었음을 알림.
- Body
  - 실제 응답 리소스 데이터
  - 201, 204와 같은 상태 코드를 가진 응답에는 보통 body가 존재하지 않는다.

```http
HTTP /1.1 200 Ok
Date : Tue, 10 Jul 2012 06:50:15 GMT
Content-Length: 362
Content-Type: text/html

<html>
...
```

프로토콜 버전, 상태 코드, 상태 코드 설명, 리스폰스 헤더필드, 바디로 구성되어 있다.



## 3. HTTP 프로토콜 특징

### HTTP 프로토콜은 stateless 프로토콜이다

HTTP프로토콜은 stateless 프로토콜이라고 불리는데 이는 각각의 데이터 요청이 서로 독립적인 관계가 된다는 의미를 내포한다. 이전 데이터 요청을 다음 데이터 요청이 기억하지 못한다는 뜻이다.

시대가 변하면서 stateless의 특성으로는 처리하기 어려운 일들이 생겨났고 이런 요소를 해결하기 위해 등장한 것이 쿠키이다.



## 4. HTTP 메서드

- GET : 리소스 획득, 존재하는 특정 리소스의 표시를 요청하는데, 오직 데이터를 받는 기능만 한다.
- POST : POST 메서드는 특정 리소스에 엔티티를 제출할 때 사용됨.
- PUT : 목적 리소스 모든 현재 표시를 요청 payload로 바꾼다.
- HEAD : HEAD 메서드는 GET 메서드의 요청과 동일한 기능이지만 응답 본문은 포함하지 않는다.(헤더를 돌려줌)
- DELETE : 파일을 삭제하기 위해서 사용됨.
- OPTIONS : 목적 리소스의 통신을 설정하는데 사용됨.
- TRACE : TRACE 메서드는 목적 리소스의 경로에 따라 메시지 loop-back 테스트를 한다. 크로스 사이트 트레이싱 같은 공격 때문에 잘 사용되지 않는다.
- CONNECT : 주로 SSL이랑 TLS등의 프로토콜로 암호화된 것을 터널링 시키기 위해 사용됨.



참고자료 

1. 그림으로 배우는 HTTP & Network
2. MDN