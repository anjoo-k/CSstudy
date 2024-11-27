# Flow Control(흐름제어)
- 송신자가 데이터를 너무 빠르게 보내서 수신자가 처리하지 못하는 문제를 방지
- Stop and wait 방법
    - 송신측에서 패킷을 보내면, 수신측에서 응답(ACK)이 와야 다음 패킷 전송
    - 응답을 기다려야하니 느리다는 단점
- Sliding Window 방법
    - 수신측에서 설정한 윈도우 크기만큼 송신측에서 확인 응답 없이 세그먼트를 전송
    - 송신측에서는 Ack 프레임을 수신하지 않더라도 여러 개의 프레임을 연속적으로 전송 가능
    - 윈도우 크기(window size) : 송신자가 ACK를 기다리지 않고 연속적으로 보낼 수 있는 데이터의 최대 양

# Congestion Control(혼잡제어)
- 네트워크 자체의 혼잡(즉, 너무 많은 데이터가 전송되어 네트워크가 과부하 상태에 빠지는 것)을 방지
- AIMD(Additive Increase / Multiplicative Decrease)
    - 처음에 패킷을 하나씩 보내고 이것이 문제없이 도착하면 window 크기(단위 시간 내에 보내는 패킷의 수)를 1씩 증가시켜가며 전송하는 방법
    - 패킷 전송에 실패하거나 일정 시간을 넘으면 패킷의 보내는 속도를 절반으로
    - 오랜 시간이 걸리게 되고, 네트워크가 혼잡해지는 상황을 미리 감지하지 못함
- Slow Start(느린 시작)
    - 초기에는 전송 속도 느리게, 네트워크 상태에 따라 점진적으로 속도 늘림
    - AIMD와 마찬가지로 패킷을 하나씩 보내면서 시작하고, 패킷이 문제없이 도착하면 각각의 ACK 패킷마다 window size를 1씩 늘려줌
    - 즉, 한 주기가 지나면 window size가 2배
    - 혼잡 현상이 발생하면 window size를 1로 떨어뜨림
- Fast Retransmit (빠른 재전송)
    - 패킷 손실이 발생했다고 판단되면(ACK 손실 등), 손실된 패킷을 즉시 재전송
- Fast Recovery (빠른 복구)
    - 혼잡한 상태가 되면 window size를 1로 줄이지 않고 반으로 줄이고 선형증가시키는 방법
          
           

       
         
[출처1](https://land-turtler.tistory.com/154)         
[출처2](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Network/TCP%20(%ED%9D%90%EB%A6%84%EC%A0%9C%EC%96%B4%ED%98%BC%EC%9E%A1%EC%A0%9C%EC%96%B4).md)
