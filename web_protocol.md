# URL (Uniform Resource Locator)

웹에서 웹 페이지를 정의하고 접근하기 위해 URL 을 사용한다.
```java
프로토콜://도메인_이름:포트/디렉토리_경로/디렉토리_경로/문서_이름?파라미터_이름=파라미터
```
- 프로토콜 : 문서를 접근하기 위해 사용하는 프로토콜 이름
- 도메인_이름 : 문서가 있는 컴퓨터의 도메인 이름
- 포트 : 서버가 어떤 포트 숫자를 바라보고 있는지 (선택 사항)
- 문서_이름 : 서버 컴퓨터에 있는 특정 문서의 이름
- 파라미터_이름 : 페이지에 넘기는 변수 (선택 사항)
- 파라미터 : 파라미터_이름에 매칭시킬 값


# HTTP (Hyper Text Transfer Protocol)

HTTP 는 브라우저가 웹 서버와 통신하기 위해 사용하는 주요 프로토콜이다. HTTP 4가지 요청 형식은 아래와 같다.

- GET : 문서를 요청. 서버가 클라이언트에 상태 정보와 복제된 문서를 보냄으로써 응답을 함. (조회)
- HEAD : 상태 정보를 요청. GET 과 동일한 형태로 응답을 하지만, 문서를 복제하지는 않는다.
- POST : 데이터를 서버로 송신. 서버는 해당 데이터를 특정 아이템에 덧붙인다. (생성)
- PUT : 데이터를 서버로 송신. 서버가 특정 아이템을 완전히 대체한다. (수정)


# HTTP GET 요청 동작과정

```java
GET /item versionCRLF
```

위 형식을 해석해보면,

- item : 요청한 문서의 URL
- version : 프로토콜의 버전을 의미. 보통은 HTTP/1.0 이나 HTTP/1.1 이다.
- CRLF : 텍스트 줄의 끝을 의미하는 2 개의 아스키 코드를 의미 (Carriage Return : 커서를 행의 맨 좌측 이동, Line Feed : 커서를 다음 행으로 이동)
여기서 version 이 중요한 이유가 클라이언트와 서버 모두 이해 가능한 버전으로 맞추어 호환하기 때문이다. 응답 헤더에서 상태 정보를 포함하기 때문에, 해당 요청이 서버에서 제대로 처리가 되었는지 확인할 수 있다. 자주 쓰이는 상태 정보로는 404 (해당 문서 못 찾음), 200 (요청 처리 완료) 등이 있다.


# HTTP 응답 헤더

```java
HTTP/1.0 status_code status_string CRLF
Server: server_identification CRLF
Last-Modified : date_document_was_changed CRLF
Content-Length : datasize CRLF
Content-Type : document_type CRLF
CRLF
```

위를 자세히 살펴 보면,

- status_code : 상태를 나타내는 숫자 값
- status_string : 사람이 식별 가능한 상태 문자 값
- server_identification : 서버정보 설명
- datasize : 데이터의 크기 (바이트 단위)
- document_type : 문서 유형 (html 문서는 text/html, jpeg 파일은 image/jpeg)
