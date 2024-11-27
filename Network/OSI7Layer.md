# Open System Interconnection 7 Layer(OSI 7계층)
- 응표세전네데물
- 왜? 네트워크간 연결의 표준을 마련하기 위함 & 네트워크 문제를 단계별로 해결할 수 있도록 설계

  **7.응용계층(Application Layer)**     
  - 사용자에게 도달하는 마지막 목적지, 응용프로그램 수행
  - 사용자 인터페이스, 전자우편, 파일전송 등의 서비스 제공
  - HTTP, FTP, SMTP, SSH(for 외부에서 서버 원격 접속) 프로토콜
        
  **6.표현계층(Presentation Layer)**
  - 입출력 데이터를 표현 형식만 변환
  - 파일 인코딩, 압축 작업 등
  - MIME(파일 형식을 의미) 인코딩
  - JPG, MPEG
         
  **5.세션계층(Session Layer)**
  - 응용 프로그램간 연결 관리
  - 즉, 기기간 세션을 열고 닫는 역할
        
  **4.전송계층(Transport Layer) - 세그먼트**
  - UDP와 TCP 프로토콜을 이용해 데이터 전송, 데이터 흐름 제어
  - TCP : 연결형(연결확립), 신뢰
  - UDP : 비연결형(연결확립x), 비신뢰성
         
  **3.네트워크계층(Network Layer) - 패킷**
  - IP 프로토콜 이용, 일단 목적지까지 빠르게 패킷 전달
  - 서로 다른 네트워크 간에 라우팅
  - 라우팅? 네비게이션 역할 : 데이터가 출발지에서 목적지까지 가장 효율적인 경로 찾아 이동
  - IP : 비연결형, 비신뢰성
        
  **2.데이터링크계층(Data Link Layer) - 프레임**
  - 같은 네트워크 상에 있는 기기끼리(= 인접한 노드간) 신뢰성 있는 정보 전달
  - MAC 주소로 통신
  - Ethernet
       
  **1.물리계층(Physical Layer) - 비트**
  - 데이터를 전기신호인 비트로 바꿔
  - 물리적인 통신케이블, 리피터 등으로 전송

  [출처및참고](https://bluecatnetworks.com/glossary/what-is-the-osi-model/)

    ![OSI 7 Layer_정리](https://github.com/user-attachments/assets/08cdc917-52cc-4320-9df2-b5370ada36e4)
  [그림출처](https://kangkoon.blogspot.com/2016/07/osi-7-layer.html)
