# Blocking I/O & Non-Blocking IO
- 네트워크 소켓의 동작방식을 두 개로 크게 나누면 Blocking I/O와 Non-Blocking I/O
- Blocking은 요청한 작업이 성공하거나 에러가 발생하기 전까지는 응답 X
  - 애플리케이션 커널에 시스템 호출을 요청했을 때 데이터가 준비되지 않았다면 호출한 스레드가 대기 상태로 들어감
  - 대기 상태로 들어가면 다른 동작 할 수 었음
- Non-Blocking은 요청한 작업의 성공여부와 관련없이 응답 O
  - 데이터가 준비될 때까지 멈춰 있지 않고 다른 작업 계속 할 수 있음

# Blocking I/O - in java
1. **싱글 스레드 Blocking**
   - 메인 스레드가 Blocking
   - 다중 클라이언트 요청 동시 처리 불가
   - 사실상 사용 불가한 서버 구조   
2. **멀티 스레드 Blocking**
   - 클라이언트 1 : 스레드 1
   - 커넥션 수에 따라 요청 스레드도 증가 -> 무한 리소스 증가 -> 서버가 죽을 수 있음
   - 스레드 컨텍스트 스위칭 비용 증가
   - 매번 스레드 생성 비용 발생
   - 즉, 요청이 증가하면 서버 부하   
3. **멀티 스레드 with 스레드풀 Blocking**
   - 클라이언트 1 : 스레드 1
   - 스레드풀에 특정 갯수 스레드 미리 만들어 두고 새 커넥션이 오면 만들어둔 스레드 할당
   - 웹 MVC 구조 기초 : 현재 가장 많은 서버가 이 방식 사용
   - 다중 커넥션 동시 처리 가능, 리소스 과사용 방지
   - 하지만 동시 접속자 수 스레드 풀에 지정된 스레드 수에 의존
   - 스레드풀 크기가 정해져 있음, 스레드가 미리 만들어져 있음 + Blocking 방식 사용   
     -> CPU, 메모리 활용도 떨어짐 + 스레드 하나가 Blocking 되고 다른 커넥션 처리 불가
     
# Non-Blocking I/O - in java
- Blocking 방식의 스레드 모델 서버는 이해 쉽고 구현 용이
- 하지만 컴퓨터 리소스 제대로 사용 X
- 문제 해결법 : I/O 작업을 Non-Blocking 하게 변경해 주는 것   
  = 적은 수의 스레드로 여러 개의 커넥션 처리하게 하자
- 자바에서도 이 문제를 해결하는 I/O 작업을 위해 New I/O(NIO) 도입
    - 현재 다양한 라이브러리, 프레임워크에서 사용중(Netty, Kafka)
### 지금까지 java I/O가 느렸던 이유
- Java 어플리케이션이 커널 버퍼를 직접 핸들링 X
- 소켓에서 Stream이 들어오면 OS 커널은 데이터를 커널 버퍼에 씀
- 즉, Java 코드로 이 커널 버퍼에 접근 불가   
  - NIO전까지는 JVM 내부 메모리(프로세스별로 할당되는 스택이나 힙 메모리)에 커널 버퍼 데이터 복사해 데이터에 접근   
    -> 이 때 복사하며 GC, CPU 낭비 발생
- JVM이 직접 커널 버퍼에 접근한다면 효율적일 것
### NIO Non-Blocking
- Polling 방식은 스레드가 직접 소켓을 순회하며 읽을 데이터 여부 체크 -> 비효율적
- 이벤트 기반 방식은 특정 소켓이 변경되었다고 이벤트 만들어 알림! -> 컴퓨터 자원 효율적 사용 가능!
- 이벤트 리스너 역할을 하는 Selector를 사용해 Non-Blocking 작업 처리 가능
  - Selector는 멀티 채널의 작업을 싱글 스레드에서 처리할 수 있도록 해주는 멀티플렉서(multiplexor)역할   
![image](https://github.com/user-attachments/assets/04dc754a-6f44-4cbc-88a2-bc3438f24012)   
[ref1](https://mark-kim.blog/understanding-non-blocking-io-and-nio/)
[ref2](https://dev-coco.tistory.com/44)    
[이미지출처](https://dev-coco.tistory.com/44)   
