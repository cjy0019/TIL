# 네트워크 TIL 🤔



## 1. HTTP 상태코드

클라이언트가 서버로 리퀘스트를 보낼 때  서버에서 그 결과가 어떻게 되는었는지 알려주는 것이 상태 코드의 역할이다. 상태 코드는 일반적으로 3자리 숫자로 표현되는데 **첫 번째 자리는 리스폰스의 클래스를 의미한다.** 나머지 2자리는 분류가 없다.

| **Response Class Code** | **Response Class 의미**        | **설명**                                   |
| ----------------------- | ------------------------------ | ------------------------------------------ |
| 1                       | Informational (정보)           | 리퀘스트를 받고, 처리 중에 있음.           |
| 2                       | Success (성공)                 | 리퀘스트를 정상적으로 처리함.              |
| 3                       | Redirection (리디렉션)         | 리퀘스트 완료를 위해 추가 동작이 필요함.   |
| 4                       | Client Error (클라이언트 오류) | 클라이언트 요청을 처리할 수 없어 오류 발생 |
| 5                       | Server Error (서버 오류)       | 서버에서 리퀘스트 처리 실패                |



## 2. 100번대 (조건부 응답)

- 100(계속): 요청자는 요청을 계속해야 한다. 서버는 이 코드를 제공하여 요청의 첫 번째 부분을 받았으며 나머지를 기다리고 있음을 나타낸다.
- 101(프로토콜 전환): 요청자가 서버에 프로토콜 전환을 요청했으며 서버는 이를 승인하는 중이다.
- 102(처리)



## 3. 200번대 성공(Success)

**200번대는 클라이언트가 요청한 작업을 서버가 성공적으로 수행했다는 상태를 알려주는 코드이다.**



- 200 OK는 리퀘스트가 정상으로 처리되었음을 알려준다.
- 201 Created는 요청이 정상적으로 처리되었고, 그로 인해 리소스가 새롭게 생성되었다는 것을 의미한다. 회원가입과 같은 서비스가 이에 해당하는 좋은 예라고 할 수 있다.
- 204 No Content는 리퀘스트가 정상적으로 처리되었지만, 어떠한 엔티티 바디를 되돌려 보내서도 안된다. 클라이언트에서 서버에 정보를 보내는 것 외에 서버에서 보낼 정보가 없을 경우에 사용된다.(ex - 게시글 삭제)



## 4. 300번대 리다이렉트(Redirection)

**300번대 코드들은 리다이렉션에 관련된 상태를 의미한다.** 클라이언트가 요청한 리소스가 옮겨지거나 리소스가 삭제되었거나 정상적인 방법으로 더 이상 해당 리소스에 접근할 수 없고 다른 URL을 통해 그 리소스에 접근해야할 때 300번대 코드를 사용한다.



- 301 Moved Permanently는 가장 많이 사용되는 코드이다. 브라우저는 자신의 요청에 대한 응답으로 301을 받으면 **HTTP 헤더의 Location**을 찾아보고 존재한다면 Location에 담긴 URL로 자동 리다이렉션한다.



## 5. 400번대 클라이언트 에러(Client Error)

**400번대의 코드들은 클라이언트가 서버에 보낸 요청이 잘못된 경우를 나타낸다.**



- 400 Bad Request는 필자도 가장 많이 마주친 400번대 코드이다. 간단히 말해 클라이언트에서 리퀘스트형식에 맞게 보내지 않았을 때, 예외처리가 안되었을 때 주로 발생한다.
- 401 Unauthorized는 인증되지 않은 사용자가 인증이 필요한 리소스를 요청하는 경우에 발생한다. 서버가 401을 응답으로 보낼 경우 클라이언트에서는 로그인이 필요한 경우라고 판단하고 **로그인 페이지로 리다이렉션 하기도 한다.**
- 403 Forbidden은 클라이언트가 접근이 금지된 리소스를 요청했을 때 발생한다.
- 404 Not Found는 리퀘스트한 리스폰스가 서버에 없음을 의미한다.

![404 not found 에러의 의미와 해결 방법 : 네이버 블로그](data:image/png;base64,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)

#### 	5.1 401 vs 403

​	401은 로그인되지 않았을 때 주로 발생하지만, 403은 리소스를 요청한 사용자가 누구인지 신경쓰지 않고 클라이언트측에서 리소스에 접근하는 것 자체가 	금지라는 뜻을 내포하고 있다.



## 6. 500번대 서버 에러(Server Error)

**500번대 리스폰스는 서버 원인으로 에러가 발생하고 있음을 나타낸다.**



- 500 Internal Server Error는 서버에서 리퀘스트를 처리하는 도중에 알 수 없는 에러가 발생했다는 의미이다. 에러의 원인을 클라이언트에게 알려주지 않는다.
- 502 Bad Gateway는 백엔드 어플리케이션이 죽은 상황에 발생한다.
- 503 Service Unavailable는 503은 서버가 요청을 처리할 준비가 되지 않았음을 의미한다. 즉, 서버가 과부하 상태이거나 점검중일 떄 발생함을 나타낸다.



참고자료

- https://evan-moon.github.io/2020/03/15/about-http-status-code/

- 그림으로 배우는 HTTP & 네트워크