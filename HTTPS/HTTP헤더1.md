HTTP 헤더
===========


## 용도
- HTTP 전송에 필요한 모든 부가정도
    + 메세지 바디의 내용
    + 메시지 바디의 크기
    + 압축
    + 인증
    + 요청 클라이언트
    + 서버 정보
    + 캐시관리정보 등등
- 표준헤더 필드가 굉장히 많음
- 필요시 임의의 헤더 추가 가능
    + helloworld: hihi  

 
  

 ## RFC723x 변화
 - 엔티티 -> 표현(Representation)
 - Representation = representation Metadata + Representation Data
 - 표현 = 표현 메타데이터 + 표현 데이터
  
  
 ## HTTP BODY
 - 메세지 본문을 통해 표현 데이터 전달
 - 메시지 본문 = 페이로드(payload)
 - 표현은 요청이나 응답에서 전달할 실제 데이터
 - 표현 헤더는 표현데이터를 해석할 수 있는 정보 제공
    + 데이터 유현(html,json), 데이터 길이, 압축 정보 등등