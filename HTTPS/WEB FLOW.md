WEB FLOW
---

#### _http://www.google.com:443/search?q=hyrki&hl=ko___

## HTTP 요청 메세지
---
GET/search?q=hyrkii&hl=ko HTTP/1.1   
Host:www.google.com
>


## HTTP 응답 메세지
---

HYYP/1.1 200 OK   
Content-Type:text/html;charset=UTF-8   
Content-Length:3423   
-html   
 body   
-html
   

-----

1. 웹브라우저가 HTTP메세지 생성
2. SOCKET 라이브러리를 통해 전달
    - A : TCP/IP 연결(IP, PORT)
    - B : 데이터 전달
3. TCP/IP 패킷 생성, (전송데이터)HTTP 메세지 포함