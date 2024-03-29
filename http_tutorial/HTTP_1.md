- HTTP 는 웹서버로부터 이미지, HTML 페이지, 텍스트 파일 등을 빠르고 정확하게 웹 브라우저로 옮겨준다. 신뢰성 있는 데이터 프로토콜을 사용하여 전송 중 손상 되거나 꼬이지 않음을 보장

- 웹 서버는 웹 리소스를 관리하고 제공한다. 이미지, 동영상, 워드 파일 등을 어떠한 콘텐츠 소식도 리소스가 가능

- Media Type (MIME TYPE) : HTTP 는 웹에서 전송 되는 객체 각각에 mime 타입이라는 데이터 포맷 라벨을 붙임

    - HTML => text/html
    - plain ASCII 텍스트 => text/plain
    - JPEG => image/jepg
    - GIF => image/gif

### URI (WebServer Resource)
- 웹 서버 리소스는 각자 이름을 갖고 있기 때문에, 클라이언트는 관심 있는 리소스를 지목할 수 있다. 서버 리소스 이름은 URI 또는 통합 자원 식별자 라고 불린다.
- URI 는 URL 과 URN 두 가지가 있음

- URL => 통합 자원 지시자는 리소스 식별자의 가장 흔한 형태, 특정 서버의 리소스에 대한 구체적인 위치를 나타냄

- URL 의 첫번쨰 부분은 스키마 (사용 되는 프로토콜을 서술) 라고 불림, 두번째 부분은 인터넷 주소를 제공, 마지막 부분은 웹 서버의 리소스를 가르킴

### Transaction 
- HTTP 트랜잭션은 요청 명령과 응답으로 구성 되어 있음, 이 상호작용은 HTTP 메세지 라고 불리는 정형화 된 데이터 덩어리를 통해 이루어진다.

##### **Method**
- HTTP 메서드는 여러 가지의 요청 명령을 지워한다, 모든 HTTP 요청 메세지는 한 개의 메서드를 갖는다. 

- 메서드
    - GET : 클라이언트에서 지정한 리소스를 받는다.
    - PUT : 클라이언트에서 서버로 보낸 데이터를 지정한 이름의 리소스로 저장
    - DELETE : 리소스를 서버에서 삭제
    - POST : 클라이언트 데이터를 서버 게이트웨이 어플리케이션으로 보냄
    - HEAD : 지정한 리소스에 대한 응답에서 HTTP 헤더 부분만 받음

##### **상태코드**
- HTTP 응답 메세지는 상태 코드와 함께 반환
    - 200 : 정상적으로 반환
    - 302 : 다른 곳에서 리소스를 가져가라
    - 404 : 리소스를 찾을 수 없음


### **메세지**
- HTTP 메세지는 단순한 줄 단위에 문자열이다. 클라이언트에서 서버로 보낸 메세지를 요청 메세지라고 부른다. 서버에서 클라이언트로 가는 메세지를 응답 메세지라고 부른다.

    - 시작줄 : 요청이라면 무엇을 해야 하는지, 응답이라면 무슨 일이 일어났는 지 나타낸다.
    - 헤더 : 이름과 하나의 값으로 구성된다.
    - 본문 : 요청의 본문은 서버로 데이터를 실어 보내며 응답의 본문은 클라이언트로 데이터를 반환한다.

### **TCP 커넥션**
- TCP 커넥션을 이용하여 메세지가 옮겨진다.

#### TCP / IP
- HTTP 는 네트워크 통신의 핵심적인 세부사항에 대하여 신경쓰지 않고 있다가 TCP/IP 프로토콜 에게 맡긴다.

- TCP 가 제공하는 것
    - 오류 없는 데이터 전송
    - 순서에 맞는 전달
    - 조각나지 않는 데이터 스트림

#### 접속 IP 주소, 포트 번혼
- HTTP 클라이언트가 서버에 메세지를 전송 할 수 있게 되기 전에, 인터넷 프로토콜 주소와 포트 번호를 이용하여 클라이언트와 서버 사이에 TCP/IP 커넥션을 맺어야 한다.

### **웹의 구성 요소**

- **Proxy** : 클라이언트와 서버 사이에 위치 하여  HTTP 중개자

- **Cache** : 많이 찾는 웹페이지를 클라이언트 가까이에 보관하는 HTTP 창고

- **Gateway** : 다른 어플리케이션과 연결 된 특별한 웹서버
- **Tunnel** : 단순 HTTP 통신을 전달 하기만 하는 특별한 Proxy
- **Agent** : 자동회된 HTTP 요청을 만드는 준 지능적 웹 클라이언트

#### Proxy
- HTTP 프록시 서버는 보안, 어플리케이션 통합, 성능 최적화를 위한 중요한 구성요소, 클라이언트와 서버 사이에 위차하여 클라이언트의 모든 HTTP 요청을 받아 서버에 전달
    - Proxy 는 주로 보안을 위해 사용
    - 요청과 응답을 필터링

#### Cache
- 웹 캐시와 캐시 프록시는 자주 찾는 것의 사본을 저장 해 두는 특별한 종류의 HTTP 프록시 서버, 클라이언트는 멀리 떨어진 웹 서버 보다 근처의 캐시에서 훨 씬 더 빨리 문서를 다운 받을 수 있다.

#### Gateway
- 게이트웨이는 다른 서버들의 중개자로 동작하는 특별한 서버이다. 주로 HTTP 트래픽을 다른 프로콜로 변환하기 위하여 사용

#### Tunnel
- 두 커넥션 사이에서 raw 데이터를 열어보지 않고 그대로 전달해주는 HTTP 어플리케이션이다. 주로 비 HTTP 데이터를 하나 이상의 HTTP 연결을 통해 그대로 전송하기 위해 사용

#### Agent
- 사용자 에이전트는 사용자를 위해 HTTP 요청을 만들어주는 클라이언트 프로그램
























