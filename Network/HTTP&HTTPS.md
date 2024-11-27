# HTTP(HyperText Transfer Protocol)
- TCP/IP에서 appication 계층의 프로토콜
- 웹상에서 정보를 주고받는 프로토콜
- 클라이언트인 웹 브라우저가 서버에 HTTP를 통해서 정보를 요청하면,   
  서버는 이 요청에 응답해서 웹 브라우저가 요청한 정보를 준다.
- 즉, 웹브라우저와 서버간에 자원을 주고받을 때 쓰는 통신규약
**하지만 HTTP는 암호화 되지 않은 평문(clear text)로 전송**
- 중요한 정보가 제3자에게 노출될 가능성
- 이 단점을 보완하기 위해 개발된 것이 HTTPS

# HTTPS(HyperText Transfer Protocol Secure)
- HTTP에 보안을 강화한 프로토콜
- HTTP로 전송되는 데이터를 암호화

  [출처1](https://mangkyu.tistory.com/98)
  [출처2](https://www.youtube.com/watch?v=hExRDVZHhig&t=267s)
           
         
        
-------------------------------------- 나중에 따로 정리해야 할 듯
  - 암호화 할 때 두 가지 프로토콜을 사용
  - SSL(Secure Sockets Layer) 혹은 TLS(Tranport Layer Security)
  - TLS는 SSL의 후속버전
  - SSL은 공개키 암호화를 사용
    - 컴퓨터가 웹 브라우저를 통헤 SSL이 있는 웹사이트에 연결을 시도하면 웹 브라우저는 웹사이트에 "네가 안전한 사이트라는걸 증명해라!"
    - 웹사이트는 자신의 SSL 인증서를 웹 브라우저로 보내는 것
    - 즉, 웹 사이트가 안전한 곳인지 알 수 있는 것이 SSL 증명서

