#  네트워크 TIL 🚀



## 1. HTTP 헤더

HTTP 프로토콜의 리퀘스트와 리스폰스에는 반드시 메시지 헤더가 포함되어 있는데 메시지 헤더에는 클라이언트나 서버가 리퀘스트나 리스폰스를 처리하기 위한 정보가 들어있다.

리퀘스트 메시지의 헤더 ex)

```http
GET HTTP/1.1
Accept:text/html,application/xhtml+xml,application/xml;q=0.9
Accept-Encoding: gzip, deflate
Connection: keep-alive
Host: localhost:8000
User-Agent: HTTPie/2.1.0
```



리스폰스 메시지의 헤더 ex)

```http
HTTP/1.1 304 Not Modified
Connection : close
Date:Tue, 01 Feb 2021 02:01:07 GMT
ETag:"45bae1-25e-50ebde89"
Server:Apache
```



## 2. HTTP 헤더 필드

HTTP를 구성하는 요소들 중에서 가장 다양한 정보를 가지고 있는 것이 HTTP 헤더필드이다.

### 2.1 헤더 필드의 구조

```text
헤더 필드 명 : 필드 값
Context-Type: text/html
```



**헤더 필드가 중복된 경우?**

- 브라우저에 따라 최초의 헤더 필드를 우선적으로 처리하고 어떤 브라우저는 마지막 헤더필드를 우선적으로 처리함.



### 2.2 헤더 필드의 종류

1. 일반적 헤더 필드(General Header Fields)
2. 리퀘스트 헤더 필드(Request Header Fields)
   - 클라이언트의 정보, 리스폰스의 콘텐츠에 관한 우선 순위 등
3. 리스폰스 헤더 필드(Response Header Fields)
   - 서버의 정보, 클라이언트의 추가 정보 요구 등
4. 엔티티 헤더 필드(Entity Header Fields)
   - 콘텐츠 갱신 시간 등



### 2.3 End-to-end vs Hop-by-hop



#### 2.3.1 end-to-end

- 최종 수신자에게 전달되어야 하는 헤더.
- 중간 프록시는 종단간 헤더를 수정되지 않은 상태로 재전송해야하며, 캐시는 반드시 이를 저장해야한다.



#### 2.3.2 hop-by-hop

- 단일 전송-레벨 연결에서만 의미가 있고 프록시에 의해서 재전송되거나 캐시되어선 안된다.
- Connection 헤더 필드에 열거해야 한다.



## 3. 일반 헤더 필드



### 3.2 Connection

connection 헤더 필드의 역할

- 프록시에 더 이상 전송하지 않는 헤더 필드를 지정

```http
GET / HTTP/1.1
Upgrade: HTTP/1.1
Connection: Upgrade
```

- 지속적인 접속 관리

```markdown
Connection: keep-alive (HTTP/1.1의 기본 값)
Connection: Close (HTTP/1.0 요청의 기본 값)
```



### 3.3 Date

Date 헤더 필드는 HTTP 메시지를 생성한 날짜를 나타내는데 다음과 같은 포맷으로 지정되어 있다.

```markdown
# Date : Tue, 03 Jul 2012 04:40:59 GMT
```

하지만 오래된 HTTP에서는 다음과 같은 포맷을 사용한다.

```markdown
# Date : Tue, 03-Jul-12 04:40:59 GMT
```



### 3.4 Pragma

Pragma 헤더 필드는 후방 호환성만을 위해 정의되어 있는 헤더 필드이다. 지정할 수 있는 값은 한 개뿐.

```markdown
Pragma : no-cache
```

호환성을 모두 고려하여 다음과 같이 보내는 경우도 존재한다.

```http
Cache-Control : no-cache
Pragma : no-cache
```



### 3.5 Trailer

HTTP 프로토콜 헤더에 Trailer 헤더가 존재하면 마지막 chunk 뒤에 HTTP 헤더를 추가할 수 있다. 즉, 마지막 chunk 뒤에 존재하는 HTTP 헤더의 이름을 정의할 수 있다.

```http
HTTP/1.1 200 OK
Content-Type: text/html
Trailer: Expires

Expires: Tue, 28 Sep 2004 23:59:59 GMT
```



### 3.6 Transfer-Encoding

`Transfer-Encoding`헤더 필드는 메시지 바디의 전송 코딩 형식을 지정할 때 사용한다.



### 3.7 Upgrade

Upgrade 헤더 필드는 HTTP 및 다른 프로토콜의 새로운 버전이 통신에 이용되는 경우에 사용된다.

**Upgrade 헤더 필드에 의해서 업그레이드 되는 대상은 클라이언트와 인접한 서버 사이뿐이기 때문에 Upgrade 헤더 필드를 사용하는 경우는 Connection:Upgrade도 지정해야한다.**

### 3.8 Via



### 3.9 Warning

warning 헤더는 기본적으로 캐시에 관한 문제의 경고를 유저에 전달한다.

```markdown
Warning: 113 gw.hackr.jp:8080 "Heuristic expiration"Tue, 03 Jul => 2012 05:09:44 GMT

`Warning: [경고 코드][경고한 호스트:포트 번호]"[경고문]"([날짜])`
```



## 4. 리퀘스트 헤더 필드

리퀘스트 헤더 필드는 클라이언트 측에서 서버 측으로 송신된 리퀘스트 메시지에 사용되는 헤더로 리퀘스트의 부가 정보와 클라이언트의 정보, 리스폰스의 콘텐츠에 관한 우선 순위 등을 추가한다.



### 4.1 Accept



### 4.2 Accept-Charset



### 4.3 Accept-Encoding



### 4.4 Accept-Language



### 4.5 Authorization



### 4.6 Expect



### 4.7 From

From 헤더 필드는 유저 에이전트를 사용하고 있는 유저의 메일 주소를 전달한다. **기본적으로 검색 엔진 등의 에이전트 책임자에게 연락처 메일 주소를 나타내는 목적으로 사용된다.** (User-Agent 헤더 필드에 메일 주소를 포함하고 있는 것도 있다.)



### 4.8 Host

```http
Host: www.naver.com
```

host 헤더 필드는 리퀘스트한 리소스의 인터넷 호스트와 포트 번호를 전달한다. Host 헤더 필드는 HTTP/1.1에서 유일한 필수 헤더이다.

리퀘스트가 서버에 오면 호스트 명을 IP 주소로 해결해 리퀘스트가 처리되는데 이 때 같은 IP 주소로 복수의 도메인이 적용되어 있다고 한다면 어느 도메인에 대한 리퀘스트인지 알 수 없다.



### 4.9 If-Match

"If-xxx"라는 서식의 리퀘스트 헤더 필드는 조건부 리퀘스트라고 부릅니다. 조건부 리퀘스트를 받은 서버는 조건에 맞는 경우에만 리퀘스트를 받는다.

```http
If-Match: "123456"
```

조건부 리퀘스트의 하나로 서버 상의 리소스를 특정하기 위해서 엔티티 태그 값(ETag)을 전달한다. 



### 4.10 If-Modified-Since

```http
GET /index.html
If-Modified-Since: Thu, 15 Apr 2004 00:00:00 GMT
```

If-Modified-Since 헤더 필드는 조건부 리퀘스트의 하나로 리소스가 갱신 날짜가 필드 값보다 새롭지 않다면 리퀘스트를 받아들이겠다는 뜻을 전달합니다.

지정한 리소스가 갱신되어 있지 않은 경우에는 304 Not Modified 리스폰스를 반환한다.



### 4.11 If-None-Match

If-None-Match 헤더 필드는 조건부 리퀘스트의 하나로 If-Match 헤더 필드와는 반대로 동작한다. If-None-Match의 필드 값에 지정된 엔티티 태그 값이 지정된 리소스의 ETag 값과 일치하지 않으면 리퀘스트를 받아들이겠다는 뜻을 전달한다.



### 4.12 If-Range

If-Range 헤더 필드는 조건부 리퀘스트의 하나로 If-Range로 지정한 필드 값(ETag 값)과 지정한 리소스의 ETag 값 혹은 날짜가 일치하면 Range 리퀘스트로서 처리하고 싶다는 것을 전달한다.



### 4.13 If-Unmodified-Since

```http
If-Unmodified-Since : Thu, 03 Jul 2012 00:00:00 GMT
```

지정된 리소스가 필드 값에 지정된 날짜 이후에 갱신되어 있지 않는 경우에만 리퀘스트를 받아들이도록 전달한다.



### 4.14 Max-Forwards

Max-Forwards 헤더 필드는 TRACE 혹은 OPTIONS 메소드에 의한 리퀘스트를 할 때 전송해도 좋은 서버 수의 최대치를 10진수 정수로 지정한다.

**서버는 다음 서버에 리퀘스트를 전송할 때는 Max-Forwards 값에서 1을 빼서 다시 set한다.**



### 4.15 Proxy-Authorization

```http
Proxy-Authorization : Basic dGlwoJkpNlAGfFTY5
```

Proxy-Authorization 헤더 필드는 프록시 서버에서의 인증 요구를 받아들인 때 인증에 필요한 클라이언트의 정보를 전달한다. 클라이언트와 서버의 HTTP 액세스 인증과 비슷하지만 다른 점은 클라이언트와 프록시 사이에 인증이 이루어진다는 점이다.



### 4.16 Range

```http
Range: bytes=5001-10000
```

Range 헤더 필드는 리소스의 일부분만 취득하는 Range 리퀘스트를 할 때 지정 범위를 전달한다. 5001 바이트부터 10000바이트까지 리소스를 요구하고 있다. Range 헤더 필드가 달린 리퀘스트를 받아들인 서버가 리퀘스트를 처리할 수 있는 경우에는 상태코드 206 Partial Content 리스폰스를 반환한다.



### 4.17 Referer

Referer 헤더 필드는 리퀘스트가 발생한 본래의 리소스의 URI를 전달한다. 기본적으로 Referer 헤더 필드는 보내져야 하지만 브라우저의 주소창에 직접 URI를 입력한 경우와 보안상 바람직하지 않다고 판단된 경우에는 보내지 않아도된다.



### 4.18 TE

```http
TE: gzip, deflate=0.5
```

TE 헤더 필드는 리스폰스로 받을 수 있는 전송 코딩의 형식과 상대적인 우선순위를 전달한다.



### 4.19 User-Agent

```http
User-Agent:Mozilla/5.0 (Windows NT 6.1) AppleWebKit/535.19(KHTML, like Gecko) Chrome/18.0.1025.162 Safari/535.195
```

User-Agent 헤더 필드는 리퀘스트를 생성한 브라우저와 유저 에이전트의 이름 등을 전달하기 위한 필드입니다.



## 5. 리스폰스 헤더 필드



### 5.1 Accept-Ranges

```http
Accept-Ranges: bytes
```

Accept-Ranges 헤더 필드는 서버가 리소스의 일부분만 지정해서 취득할 수 있는 Range 리퀘스트를 접수할 수 있는지 여부를 전달합니다. 지정 가능한 필드 값은 2개이며 수신 가능한 경우에는 'bytes', 수신 불가능한 경우에는 'none'이라고 기록한다.



### 5.2 Age

```http
Age : 600
```

Age 헤더 필드는 얼마나 오래 전에 오리진 서버에서 리스폰스가 생성되었는지를 전달한다. 필드 값의 단위는 초입니다. 프록시가 리스폰스를 생성했다면 Age 헤더 필드는 필수이다.



### 5.3 ETag

```http
ETag : '82e222930907ce725faf677779359712'
```

ETag 헤더 필드는 엔티티 태그라고 불리며 일의적으로 리소스를 특정하기 위한 문자열을 전달합니다.



#### 5.3.1 강력한 ETag 값과 약한 ETag 값

강한 ETag 값은 엔티티가 아주 조금 다르더라도 반드시 값은 변화합니다.

```http
ETag: 'Usagi-1234'
```



#### 5.3.2 약한 ETag 값

약한 ETag 값은 리소스가 같다는 것만을 나타낸다. 의미가 다른 리소스로 그 차이가 있는 경우에만 ETag 값이 변화한다.

```http
ETag: W/"usagi-1234"
```



### 5.4 Location

```http
Location : http://www.naver.com/sample.html
```

Location 헤더 필드는 리스폰스의 수신자에 대해서 Request-URI 이외의 리소스 액세스를 유도하는 경우에 사용된다.



#### 5.5 Proxy-Authenticate

```http
Proxy-Authenticate: Basic realm="Usagidesign Auth"
```

Proxy-Authenticate 헤더 필드는 프록시 서버에서의 인증 요구를 클라이언트에 전달한다. 클라이언트와 서버와의 HTTP 액세스 인증과 비슷한데 다른 점은 클라이언트와 프록시 사이에서 인증이 이루어진다는 점이다.



#### 5.6 Retry-After ("다시 접속을 시도해 주세요")

`Retry-After` 응답 HTTP 헤더는 다음에 올 요청이 이루어지기 전에 브라우저가 대기해야 하는 시간을 가르킵니다. 이 헤더가 사용되는 두 가지 경우가 있다.

- 503(Service Unavailable) 응답이 전송된 경우, 서비스가 얼마나 오랫동안 이용 불가능한지 예측되는 시간을 가리킨다.
- 301(Moved Permanently)와 같은, 리다이렉트 응답이 전송된 경우, 리다이렉트 요청을 하기 이전에 사용자 에이전트가 대기해주길 원하는 최소한의 시간을 가리킨다.

값으로는 두 가지 형식이 가능한데, 다음과 같다.

```http
Retry-After : Wed, 21 Oct 2015 07:28:00 GMT
Retry- After : 120
```

ex) 도메인이 변경되었을 때 location 헤더를 이용해서 주소를 리다이렉트 할 수 있었다. 하지만 아무런 메세지 없이 Redirect가 발생한다면 왜 리다이렉트되는지 이상하게 생각할 수도 있다. "도메인이 변경되 어 다른 페이지로 이동합니다"라는 메시지를 준다면 이런 문제를 해결할 수 있다.



#### 5.7 Server

Server 헤더 필드는 서버에 설치되어 있는 HTTP 서버의 소프트웨어를 전달합니다. 단순히 서버의 소프트웨어 명칭만이 아닌 버전이나 옵션에 대해서도 기재하기도 한다.



#### 5.8 Vary

Vary 헤더 필드는 캐시를 컨트롤하기 위해서 사용한다. 오리진 서버가 프록시 서버에 로컬 캐시를 사용하는 방법에 대한 지시를 한다. 오리진 서버로부터 Vary에 지정되었던 리스폰스를 받아들인 프록시 서버는 이후 캐시된 때의 리퀘스트와 같은 Vary에 지정되어 있는 헤더 필드를 가진 리퀘스트에 대해서만 캐시를 반환한다.



#### 5.9 WWW-Authenticate

웹 서버의 서비스 목적에 따라 허가된 클라이언트에게만 서비스를 제공해야 하는 경우가 있다. 예컨데, 특정 부서를 위한 홈페이지등이 그렇다. 접속은 가능하지만 로그인 과정을 통해 허가된 사용자에게만 컨텐츠를 제공해야 할 때 이 헤더가 사용된다.

```http
WWW-Authenticate : Basic realm="Usagidesign Auth"
```

WWW-Authenticate와 Proxy-Authenticate 응답 헤더는 리소스에 대한 액세스를 얻기 위해 사용되어야 할 인증 방법을 정의한다. 이들은 클라이언트가 인증 정보를 제공할 방법을 알기 위해, 어떤 인증 스킴이 사용될 것인지를 구체적으로 명시해줘야한다.

```http
WWW-Authenticate : <type> realm=<realm>
Proxy-Authenticate : <type> realm=<realm>
```

여기서 `<type>`은 인증 스킴이다.("Basic"은 가장 일반적인 스킴이고) realm은 보호되는 영역을 설명하거나 보호의 범위를 알리는데 사용됩니다. 



## 6. 엔티티 헤더 필드

엔티티 헤더 필드는 리퀘스트 메시지와 리스폰스 메시지에 포함된 엔티티에 사용되는 헤더로 콘텐츠의 갱신 시간을 같은 엔티티에 관한 정보를 포함합니다.



#### 6.1 Allow

```http
Allow: GET, HEAD
```

Allow 헤더 필드는 Request-URI에 지정된 리소스가 제공하는 메소드의 일람을 전달한다. 서버가 받을 수 없는 메소드를 수신한 경우에는 상태코드 405 리스폰스와 함께 수신 가능한 메소드의 일람을 기술한 Allow 헤더 필드를 반환한다.



#### 6.2 Content-Encoding

```http
Content-Encoding: gzip
```

Content-Encoding 헤더 필드는 서버가 엔티티 바디에 대해서 실시한 콘텐츠 코딩 형식을 전달한다. 콘텐츠 코딩은 엔티티의 정보가 누락되지 않도록 압축할 것을 지시한다. 주로 4가지가 자주 사용된다.

- Gzip
- Compress
- Deflate
- Identity



#### 6.3 Content-Language

엔티티 바디에 사용된 자연어를 전달한다.



#### 6.4 Content-Length

```http
Content-Length : 15000
```

이 헤더 필드는 엔티티 바디의 크기를 전달한다. 엔티티 바디에 전송 코딩이 실시된 경우에는 Content-Length 헤더 필드를 사용하면 안된다.



#### 6.5 Content-Location

```http
Content-Location : http://www.naver.com/index-ja.html
```

Content-Location 헤더는 메시지 바디와 관련된 URI 정보를 제공하는 헤더이다. 클라이언트의 Accept-Language 헤더 정보를 이용해서 사용자의 언어환경을 파악한 후 적절한 언어의 서비스 URI를 전달하려 할 때 활용할 수 있다.

Accept-Language: en-US 인경우, 응답헤더의 Content-Location: /main_us.html

Accept-Language: ko-KR 인경우, 응답헤더의 Content-Location: /main_ko.html



#### 6.6 Content-MD5

```http
Content-MD5 : OGFKZDUwNGVhNgY3N2MxDlWzmQ4NTBmY2ly==
```

Content-MD5 헤더 필드는 메시지 바디가 변경되지 않고 도착했는지 확인하기 위해 MD5 알고리즘에 의해서 생성된 값을 전달한다. 메시지 바디에 MD5 알고리즘을 적용해서 얻은 128비트의 바이너리 값에 Base64 인코딩을 한결과를 필드 값에 기록한다.

유효성을 확인하기 위해서는 수신한 클라이언트 측에서 메시지 바디에 같은 MD5 알고리즘을 실행하여 바디가 올바른지 여부를 알아낸다.



#### 6.7 Content-Range

클라이언트가 대용량의 파일을 웹서버에서 다운로드 하다가 중간에 끊기는 일이 발생했다. 클라이언트가 Range 헤더를 이용해서 끊긴 부분부터 다시 다운받기를 시도하는 경우 웹서버는 Accept-Range 헤더와 함께 이어서 파일을 전송해 줄 수 있다.

Range 헤더를 이용해서 파일을 이어받으려고 할 때 웹 서버는 Accept-Range 헤더와 함께 클라이언트가 요청한 부분부터 데이터를 전송한다는 정보를 전달하는데 이 때 Content-Range 헤더가 사용된다.

**웹 서버가 다시 전송을 시작하는 시점을 Content-Range에 표시한다.**



#### 6.8 Content-Type

Content-Type 헤더는 클라이언트가 요청한 컨텐츠의 형태를 표시하는 헤더이다. Content-Type의 형태는 다음과 같다.

```http
Content-Type : 주타입/ 서브타입
```



#### 6.9 Expires

Expires 헤더는 단어 뜻 그대로 컨텐츠의 유효기간이라고 이해할 수 있다. 캐시 서버가 캐싱하고 있는 컨텐츠가 Expires 헤더에 명시되어 있는 기간이 지나게 되면, 더 이상 유효한지 아닌지를 실제 웹서버에서 확인해야 한다.

Expires와 Cache-Control 헤더의 max-age가 같이 사용된 경우에는 Cache-Control 헤더가 먼저 적용되기 떄문에 Expires헤더가 무시될 수 있다.



#### 6.10 Last-Modified

Last-Modified 헤더 필드는 리소스가 마지막으로 갱신되었던 날짜 정보를 전달한다.



## 7. 쿠키를 위한 헤더 필드

서버와 클라이언트 간의 상태를 관리하는 쿠키는 HTTP/1.1의 사양인 RFC2616에 포함된 것은 아니지만 웹 사이트에서 널리 사용된다. 쿠키가 호출되었을 때는 쿠키의 유효 기한과 송신지의 도메인, 경로, 프로토콜 등을 체크하는 것이 가능하기 떄문에 적절하게 발행된 쿠키는 다른 웹 사이트와 공격자의 공격에 의해 데이터가 도난당하는 일은 없다.



#### 7.1 Set-Cookie

클라이언트의 처음 요청에 웹서버가 Set-cookie를 이용해서 쿠키를 발행한다.



#### 7.1.1 Expires

쿠키의 Expires 속성은 브라우저가 쿠키를 송출할 수 있는 유효기간을 지정할 수 있다. 속성을 생략하면 브라우저 세션이 유지되고 있는 동안만 유효하게 된다. 한번 송출한 쿠키는 서버에서 명시적으로 삭제하는 방법은 없고 쿠키를 덮어쓰는 방식으로 삭제하는 것이 가능하다.



#### 7.1.2 Path

쿠키의 path 속성은 쿠키를 송출하는 범위를 특정 디렉토리에 한정할 수 있다.



#### 7.1.3 Domain

쿠키의 domain 속성에 의해서 지정된 도메인 명은 후방 일치가 되서 'sample.com'로 지정하면 'www.sample.com', 'www2.sample.com' 등에도 쿠키가 송출된다.



#### 7.1.4 Secure

secure 속성은 웹 페이지가 HTTPS에서 열렸을 때에만 쿠키 송출을 제한하기 위해서 사용된다. 생략하는 경우 HTTP와 HTTPS에도 쿠키를 반송한다.



#### 7.1.5 HttpOnly

쿠키의 HttpOnly 속성은 자바스크립트를 경유해서 쿠키를 취득하지 못하도록 하는 쿠키의 확장이다. XSS 도청으로 부터 도청을 막을 수 있다.

https://4rgos.tistory.com/1



#### 7.2 Cookie

Cookie 헤더 필드는 클라이언트가 HTTP의 상태 관리 지원을 원할 때 서버로부터 수신한 쿠키를 이후의 리퀘스트에 포함해서 전달한다.



#### 7.3 이외 헤더 필드

- X-Frame-Option
- X-XSS-Protection
- DNT
- P3P



#### 7.3.1 X-frame-Option

```http
X-Frame-Option : DENY
```

X-Frame-Option 헤더 필드는 다른 웹 사이트의 프레임에서 표시를 제어하는 리스폰스 헤더로, 클릭 재킹이라는 공격을 막을 목적으로 한다.

- DENY: 거부
- SAMEORIGIN

모든 웹 서버에서 설정해두는 것이 바람직하다.



#### 7.3.2 X-XSS-Protection

X-XSS-Protection : 1

이 헤더 필드는 크로스 사이트 스크립팅 대책으로서 브라우저의 XSS 보호 기능을 제어하는 HTTP 리스폰스 헤더이다.

- 0: XSS 필터를 무효로 한다.
- 1: XSS 필터를 유효로 한다.



#### 7.3.3 DNT

DNT는 Do Not Track이라는 뜻이고 개인 정보 수집을 거부하는 의사를 나타내는 HTTP 리퀘스트 헤더이다.

- 0 : 트래킹 동의
- 1 : 트래킹 거부



#### 7.3.4 P3P

P3P 헤더 필드는 사용자들이 허용하는 정보만 웹 사이트들이 수집할 수 있게 통제하는 도구이다. P3p는 웹 사이트의 프라이버시 보호정책을 전달하는 기준을 제공한다.