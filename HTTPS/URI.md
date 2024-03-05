URI
---
Uniform Resource Identifier

URI는 로케이터(locator), 이름(name) 또는 둘다 추가로 분류될 수 있다.

>   URI
>   - URL : example.com:8042/over
>   - URN : example:animal:ferret

- Uniform : 리소스 식별하는 통일된 방식
- Resource : 자원, URI로 식별할 수 있는 모든 것 (제한없음)
- Identifier : 다른 항목과 구분하는데 필요한 정보

## URL (전체문법)

- scheme://[userinfo@]host[:port][/path][?query][#fragment]
- https://www.google.com:443/search?q=hyrki09&hl=ko
### scheme
- 주로 프로토콜 사용
- 프로토콜: 어떤 방식으로 자원에 접근할 것인가 하는 약속 규칙
    - 예) http,https,ftp 등등
- http는 80포트, https는 443 포트를 주로 사용, 포트는 생략 가능
- https는 http에 보안 추가 (HTTP Secure)

### userinfo
- URL에 사용자정보를 포함해서 인증
- 거의 사용하지 않음

### host
- 호스트명
- 도메인명 또는 IP주소를 직접 사용가능

### port
- 포트
- 접속 포트
- 일반적으로 생략, 생략시 http는 80, https는 443

### path
- 리소스 경로(path), 계층적 구조
- 예)
    - /home/fileX.jpg
    - /members
    - /members/100
### query
- key = value 형태
- ?로 시작, &로 추가 가능 ?keyA=valueA&keyB=valueB
- query parameter,query string 등으로 불림, 웹서버에서 제공하는 파라미터, 문자형태

### fragment
- html 내부 북마크 등에 사용
- 서버에 전송하는 정보 아님
