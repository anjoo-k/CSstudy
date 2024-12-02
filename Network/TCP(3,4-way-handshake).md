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

![image](https://github.com/user-attachments/assets/4ef1b0d2-57e4-477c-80a8-c1509007f9e3)     

     
(Client----------------------------------------Server)        
   |--------------- SYN (Seq=x) ------------------->|      
   |<-------- SYN-ACK (Seq=y, Ack=x+1) ---------|     
   |-------------- ACK (Ack=y+1) ----------------->|        
                연결 설정 완료         
   
[그림출처](https://www.geeksforgeeks.org/tcp-3-way-handshake-process/)

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

### 4-Way Handshake의 목적 및 단계(그림설명)
- TCP는 양방향으로 동시에 통신하는 전이중(full-duplex) 방식으로 작동
- 따라서 한쪽 연결이 끊어지면 해당 측에서 데이터를 더 이상 보낼 수 없음
- **BUT** 반대쪽에서 보내는 데이터는 여전히 받을 수 있음
1. FIN(Finish) : It is sent by client or server can also sent it in order to terminate the session. It is called FIN_WAIT_1 state.
     - 데이터를 전송한 측(클라이언트 또는 서버)에서 연결을 종료하기 위해 FIN 플래그가 설정된 패킷을 보냅니다.
     - 이 패킷은 "이제 데이터를 더 이상 보내지 않겠다"는 의도를 상대방에게 알립니다.
3. ACK(Acknowledge) : Sent by the server in response for FIN.
At this time, the connection has been terminated from client side only since FIN has been sent from client only and it has received ACK from Server but Server still has TCP connection open because server hasnt sent its FIN yet. This state is called FIN_WAIT_2 State because the client is expected to get FIN from server as well.
     - FIN 패킷을 받은 측은 이를 확인하는 ACK 패킷을 보냅니다.
     - 이 패킷은 "FIN 패킷을 잘 받았다"는 의미입니다.
     - 그러나 이 단계에서 연결이 완전히 종료되는 것은 아닙니다.
5. FIN-ACK : It is sent by the server to client stating i am also closing the connection.
     - FIN을 처음 받은 측도 자신의 데이터 전송을 종료하기 위해 FIN 플래그가 설정된 패킷을 보냅니다.
     - 이는 "나도 데이터를 더 이상 보내지 않겠다"는 의도를 전달합니다.
7. ACK : This is sent by client to server acknowledges the FIN from server. It is called TIME_WAIT state. The TIME_WAIT state lets the client resend the final acknowledgment in case the ACK is lost.
     - 마지막으로, 처음 FIN을 보낸 측이 이를 확인하는 ACK 패킷을 보냅니다.
     - 이로써 양쪽 모두 연결이 종료되었음을 확인하고, TCP 연결이 완전히 닫힙니다.    
     
      
**++ 추가**
- **sequence 번호란?**
     - TCP에서 데이터는 큰 덩어리가 아니라 작은 조각(세그먼트)으로 나뉘어 전송됩니다.     
     - 시퀀스 번호는 각 세그먼트가 전체 데이터 스트림에서 어느 위치에 해당하는지를 나타내는 번호
     - 데이터를 전송할 때마다 시퀀스 번호는 전송된 데이터 바이트의 크기만큼 증가 -> 수신 측에서는 시퀀스 번호를 보고 데이터 순서 맞춤
     - 수신 측은 데이터를 정상적으로 받았을 때, 다음에 기대하는 시퀀스 번호를 확인 응답 번호(Acknowledgment Number)로 보냄
          - 예를 들어, 송신 측이 Seq=1000에서 500바이트를 전송했다면, 수신 측은 Ack=1500을 반환
          - ![image](https://github.com/user-attachments/assets/f9d7d095-85c0-41f6-96c4-522822633c99)    
          [그림출처](https://www.pixelstech.net/article/1727412048-Why-TCP-needs-3-handshakes)
     - 역할: 데이터의 순서를 보장하고 중복 전송을 방지
          1. 데이터 순서 보장
               - 인터넷에서 데이터가 여러 경로를 통해 전송되다 보니 도착 순서가 뒤섞일 수 있습니다.
               - 시퀀스 번호를 사용하면 수신 측에서 데이터를 원래의 순서대로 재조립할 수 있습니다.
          2. 데이터 손실 감지
               - 인터넷에서 데이터가 여러 경로를 통해 전송되다 보니 도착 순서가 뒤섞일 수 있습니다.
               - 시퀀스 번호를 사용하면 수신 측에서 데이터를 원래의 순서대로 재조립할 수 있습니다.
          3. 중복 제거
               - 네트워크 문제로 일부 데이터가 손실될 수 있습니다.
               - 수신 측은 시퀀스 번호를 보고 어떤 데이터가 누락되었는지 알아낼 수 있습니다.
          4. 연결 초기화
               - 3-Way Handshake에서 클라이언트와 서버는 서로 초기 시퀀스 번호를 교환하여 데이터 전송의 시작점을 설정
               - 3-Way Handshake에서 클라이언트와 서버는 각각의 **초기 시퀀스 번호(ISN)**를 무작위로 선택합니다.
               - 이 번호는 데이터 스트림의 시작점을 의미하며, 보안을 위해 무작위로 설정
       

