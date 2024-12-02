# HTTPS: SSL(Secure Sockets Layers)과 TLS(Transport Layer Security)
- SSL과 TLS는 대칭 키 암호화, 공개 키 암호화 그리고 공개 키 인증서를 기반으로 동작하는 프로토콜
- SSL/TLS를 사용하는 대표적인 프로토콜이 HTTPS
- HTTPS의 송수신 단계
  
    1 . TCP-3-way-handshake   
    2 . TLS handshake   
    3 . 암호화된 메세지 송수신

# TLS hansshake
- 클라이언트가 서버에 요청을 보내고 인증서를 응답받는 상황   
    1 . 암호화 통신을 위한 키를 교환
    2 . 인증서 송수신과 검증이 이루어짐
- ClientHello(클라이언트 to 서버)
    - 암호화 하기 전, 암호화될 통신을 위해 서로 맞춰봐야할 정보 제시하는 메시지
    - 지원되는 TSL 버전, **사용가능한 암호화 방식과 해시 함수**, 키를 만들기 위해 사용할 클리어언트 난수 등이 포함
        - 사용가능한 암호화 방식과 해시 함수 = 암호 스위트(cipher suite)
- ServlerHello(서버 to 클라이언트)
    - ClientHello 메시지에 대한 응답
    - 제시된 벙보를 선택하는 메시지
    - 선택된 TLS 버전, 암호 스취트 등의 정보, 키를 만들기 위해 사용할 서버의 난수 등
    - Certificate, CertificateVerify 메시지도 전송
        - 인정서, 검증을 위한 디지털 서명 의미
        - 클라이언트는 이 메시지 토대로 서버의 공개 키 검증
- 서버와 클라이언트는 TLS handshake 마지막을 의미한s Finished 메시지 주고 받고,
- 이 단계 이후부터 클라이언트와 서버는 키로 암호화된 메시지(암호문, Application Data) 주고 받을 수 있게 됨
![image](https://github.com/user-attachments/assets/3411167b-6923-4cf7-bef3-72d84f39b611)    
[그림출처](https://ptuladhar3.medium.com/testing-ssl-tls-handshake-latency-using-ssl-handshake-6a0c497890d1)
![image](https://github.com/user-attachments/assets/94756367-c717-4d4a-83a0-254d9c0def11)
[그림출처](https://www.researchgate.net/figure/SSL-TLS-Handshake-Process-3_fig1_379144405)
   
출처 : 혼자 공부하는 네트워크, 강민철
