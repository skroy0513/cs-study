# Network
## Index
1. [HTTP & HTTPS](#1-http--https)
2. [CORS 정책](#2-cors정책)
3. [쿠키와 세션](#3-쿠키와-세션)
4. [TCP/UDP](#4-tcpudp)
5. [HTTP Method](#5-http-method)
6. [HTTP 상태코드](#6-http-상태코드)
7. [OSI 7계층](#7-osi-7계층)

-- -- --

### 1. [HTTP & HTTPS](https://skroy0513.tistory.com/43)
<details>
  <summary>❓ <b><i>CORS에 대해서 설명해 주세요.</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;CORS는 출처가 다른 자원들을 공유한다는 뜻으로, 한 출처에 있는 자원에서 다른 출처에 있는 자원에 접근하도록 하는 개념입니다. 출처란 "Protocol, Host, Port" 3가지가 모두 같으면 동일 출처라고 합니다. CORS가 없이 모든 데이터를 요청할 수 있게 된다면, 은행  도메인에 들어가서 계좌를 삭제하는 <script> 파일이 심어진 악성 브라우저를 열람했을 때, 해당 <script> 파일이 ajax 요청을 통해 나의 계좌를 삭제하는 일이 발생할 수 있습니다.<br>
    &nbsp;&nbsp;CORS의 동작 방식에는 단순 요청 방법과 예비 요청을 먼저 보내는 방법 2가지가 있습니다. 단순 요청 방법은 HTTP의 메서드와, Header의 타입, Content-Type의 종류에 조건을 걸어 위 조건이 모두 만족하면 요청을 직접 받는 것을 말합니다. 예비 요청을 먼저 보내는 방법은 OPTIONS 메서드로 요청을 보내 안전한지 파악이 되면 본 요청을 보내고 자원을 받는 것을 말합니다.
  </div>
</details>
      
### 2. [CORS정책](https://skroy0513.tistory.com/40)
### 3. [쿠키와 세션](https://skroy0513.tistory.com/42)
### 4. [TCP/UDP](https://skroy0513.tistory.com/41)
### 5. [HTTP Method](https://skroy0513.tistory.com/50)
### 6. [HTTP 상태코드](https://skroy0513.tistory.com/55)
### 7. [OSI 7계층](https://skroy0513.tistory.com/56)
