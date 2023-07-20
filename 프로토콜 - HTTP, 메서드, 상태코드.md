# 프로토콜

컴퓨터 간 데이터를 교환할 때(통신할 때) 사용하는 정해진 규칙 체계





## 인터넷 프로토콜 스택의 4계층

| 애플리케이션 계층 | 전송계층      | 인터넷 계층                 | 네트워크 인터페이스 계층 |
| ----------------- | ------------- | --------------------------- | ------------------------ |
| HTTP, FTP         | TCP, UDP      | IP                          | 인터페이스 계층          |
| 웹브라우저        | TCP 정보 생성 | IP 패킷 생성, TCP 데이터 포 | LAN 드라이버, LAN 장비   |

- 웹에서는 브라우저와 서버 간에 데이터를 교환할 때 HTTP(Hypertext Transfer Protocol)라는 프로토콜을 사용함

- 데이터 교환은 요청(Request)과 응답(Response)으로 이루어짐





## HTTP 요청 메서드

 HTTP 요청 메서드(Http Request Methods)

- **GET** : 존재하는 자원에 대한 **요청**
- **POST** : 새로운 자원을 **생성**
- **PUT** : 존재하는 자원에 대한 **변경**
- **PATCH** : 자원 **부분 변경**
- **DELETE** : 존재하는 자원에 대한 **삭제**





## HTTP 메서드 속성

- 안전(Safe Methods) 
- 멱등(Idempotent Methods)
- 캐시기능(Cacheable Methods)





## HTTP 상태 코드

- 1xx (informational) : 요청이 수신되어 처리중
- 2xx (Successful) : 요청 정상 처리
- 3xx (Redirection) : 요청을 완료하려면 추가 행동이 필요
- 4xx (Client Error) : 클라이언트 오류, 잘못된 문법 등으로 서버가 요청 수행 불가
- 5xx (Server Error) : 서버 오류, 서버가 정상 요청을 처리하지 못함