# CORS

**교차 출처 리소스 공유(Cross-Origin Resource Sharing, CORS**(=Access-Control-Allow-Origin)**)**

 :  한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 허락을 구하는 체제

- 브라우저는 보안의 이유로 cross-origin HTTP 요청들을 제한
    
    →브라우저에서 요청을 구해야함
    
    ---
    
    ![URL 구조](CORS%2012a389191ada47a89d8846d48be17c4a/Untitled.png)
    
    URL 구조
    
    origin이란? → Protocal, Host, Port를 합친 것
    
    cross-origin → 한가지라도 다른 경우
    
    1. 프로토콜 ( http와 https는 )다름
    2. 도메인( domain.com과 other-domain.com은 )다름
    3. 포트 번호 (8080과 3000은) 다름
    
    ---
    

### 필요 이유

모든 곳에서 데이터 요청 가능시, 다른 사이트가 원래 사이트 흉내 가능함

예) 기존 사이트와  동일하게 동작하도록 하여 악의적으로 정보 추출 가능

→ 공격 할 수 없도록 브라우저에서 보호

---

### 단순 동작 원리

**Simple request (단순 요청)** : 서버에게 바로 요청을 보내는 방법

**Preflighted request(프리플라이트 요청)** : 메서드를 통해 HTTP 요청을 보내  실제 내용이 전송하기에 안전한지 확인

**Preflighted request(예비 요청)** : 본 요청을 보내기 전 브라우저 스스로 요청을 보내는 것이 안적한지 확인

1. 클라이언트 HTTP 요청
    
    요청 헤더에 Origin 정보를 담아서 보냄
    
2. Server 응답
    
    서버에서 해당 요청에 대한 응답 시 헤더에 Access-Control-Allow-Origin 정보를 담아 보냄
    
3. 비교
    
    Origin 정보와 서버에서 보낸 Access-Control_Allow-Origin 정보를 비교 → 서버에서 보내준 Access-Control_Allow-Origin를 차단할지 말지 정함