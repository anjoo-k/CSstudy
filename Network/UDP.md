# UDP(User Datagram Protocol)
### UDP의 특징   
1. TCP와 달리 비연결형 프로토콜로 데이터그램 방식 사용
   - 데이터 전송 순서 변경될 수 있음
2. 데이터 수신 여부 확인 X
3. 신뢰성이 낮음
   - 연결 수립 및 해제, 재전송을 위한 오류 제어, 흐름 제어 등을 수행하지 않음
4. TCP보다 속도가 빠름
   - 실시간 스트리밍 서비스 등에 이용
5. 1:1, 1:N, N:N 통신 가능(TCP는 1:1만 가능)
-> 즉, 신뢰성보다는 연속성 있는 전송이 필요할 때 사용

![image](https://github.com/user-attachments/assets/ad361dee-3f2c-4dfb-9359-f76910924445)    
[표&내용출처](https://dev-coco.tistory.com/144)

### UDP 데이터그램 구조
- 송신지포트, 수신지포트, 길이, 체크섬 4가지로 이루어짐
![image](https://github.com/user-attachments/assets/5bc4b54f-3a36-4461-b606-41f6e6df7dd2)    
[이미지출처](https://blog.naver.com/wnrjsxo/221246846379)
- 송신지포트(출발지 포트 번호, Source Port Number)
  - 출발지 장치가 사용하는 포트 번호
- 수신지포트(목적지 포트 번호, Destination Port Number)
  - 목적치 장치의 포트 번호
  - 출발지에서 목정지 장치상의 어떤 서비스에 접속하느냐에 따라 미리 정해져 있음
- 길이(Total Length)
  - 헤더와 UDP 데이터그램 전체 길이 나타냄(8byte)
- 체크섬(Checksum)
  - 헤더와 데이터를 포함한 사용자의 데이터 그램 오류 검사 위한 필드
  - 수신자는 이 필드값을 토대로 정보 훼손 여부 판단 후, 문제 있을 경우 폐기
    -> 데이터그램이 훼손되었는지를 판단하는 것으로 수신지까지 잘 도달했는지를 나타내는 신뢰성/비신뢰성과는 연관x
