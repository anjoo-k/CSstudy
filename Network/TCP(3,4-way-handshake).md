# 3-way-handshake : 연결수립
3-way-handshake는 **네트워크 계층에서 안정적인 연결을 위한 TCP 연결 수립 과정**을 의미합니다.   
예를 들어 클라이언트와 서버가 3-way-handshake를 한다고 가정한다면,     
아래의 그림과 같이 **세단계를 거쳐 본격적인 송수신이 시작**됩니다.     

먼저, **클라이언트는 연결을 시작하기 위해서 서버에 SYN(Synchronize) 세그먼트를 보냅니다.**     
(이 때, 클라이언트가 임의로 선택한 초기 시퀀스 번호(Sequence Number, 예: x)를 포함)    
**다음으로 서버에서는 요청을 확인했고 시작하자는 의미로 SYN + ACK(Synchronize-Acknowledge) 세그먼트로 응답**합니다.    
(서버는 자체 초기 시퀀스 번호(예: y)를 생성하고, 클라이언트의 시퀀스 번호 x에 대해 +1을 더한 값을 확인 응답 번호(Acknowledgement Number)로 보냄)    
**마지막으로 클라이언트는 서버에서 온 세그먼트를 확인했다는 의미로 ACK 세그먼트를 보낸 후     
본격적인 송수신이 시작**됩니다.     
(클라이언트는 서버의 시퀀스 번호 y에 대해 +1을 더한 값을 확인 응답 번호로 보냄)    

![image](https://github.com/user-attachments/assets/5e65d074-a320-491f-95ff-85acd8883d51)     
     
(Client----------------------------------------Server)        
   |--------------- SYN (Seq=x) ------------------->|      
   |<-------- SYN-ACK (Seq=y, Ack=x+1) ---------|     
   |-------------- ACK (Ack=y+1) ----------------->|        
                연결 설정 완료         
   
[그림출처](https://jingyu91.github.io/network/network-TCP%EC%99%80-UDP/)

### 3-way-handshake 목적
1. 양쪽이 통신을 시작할 준비가 되었는지 확인    
2. 클라이언트와 서버 간의 초기 시퀀스 번호를 동기화하여 데이터의 순서와 중복을 방지    
3. 양쪽 모두의 네트워크 연결 상태를 확인    
        
# 4-way-handshake : 연결종료
**3-way-handshake를 통해 연결을 수립한 후 데이터 송수신이 끝났다**면,   
이제는 **연결을 종료**해야 합니다. **연결을 종료하기위해 필요한 절차**가 4-way-hanshake 입니다.   
TCP가 연결을 종료할 때는 **클라이언트와 서버가 각자 한번씩 FIN과 ACK를 주고 받으면서 이루어**집니다.

![image](https://github.com/user-attachments/assets/1097735d-1c51-45f9-b5b3-8e466b22de03)
[그림출처](https://www.linkedin.com/pulse/tcp-4-way-termination-handshake-ibraham-ajazz)      

      
+++추가
