# 로드밸런싱(Load Balancing)
- 로드밸런싱이란 이름 그대로 일을 균형있게 나눠주는 것을 뜻함
- 네트워크에서는 접속자가 몰릴 때 동일한 서버를 여러 대 구비해 두고 트래픽을 분산해서 처리하는 것을 말함
- 이 때 한대의 서버에 트래픽이 몰리지 않도록 적절하게 처리해 주는 기술을 로드밸런싱이라 함
- 로드밸런싱은 주로 L4/L7에서 이루어짐

  ### 로드 밸런서
  - L4 : OSI 7계층에서 전송계층인 4계층에서 이루어짐
     - IP주소와 포트번호 등을 이용해 트래픽을 나눠줌
  - L7 : OSI 7계층에서 응용계층인 7계층이서 이루어짐
     - HTTP 헤더, URL, 쿠키 등 사용자 요청 정보를 이용해 트래픽을 나눔
     - 따라서 클라이언트 요청을 더 세분화 해서 서버에 전달할 수 있으며,
     - 보안 기능이 내장되어 있어 DDOS 공격이나 특정 패턴의 바이러스 등을 감지할 수 있음

  ### 로드 밸렁싱 기법
  - 라운드 로빈(Round Robin)
      - 들어오는 요청을 순차적으로 서버에 보내는 법(1번요청-1번서버, 2번요청-2번서버...)
      - 모든 서버의 스펙이 동일하고, 세션 지속시간이 짧을 경우 적합
  - 가중 라운드 로빈(Weighted Round Robin)
      - 가중치가 높은 서버부터 트래픽을 할당
      - 특정 서버의 스펙이 높을 때 사용
  - IP 해시
     - 클라이언트의 IP주소를 해싱해 개별서버에 매핑하여 특정 클라이언트는 항상 동일한 서버로 가도록 할당
     - 모든 연결에 모든 서버에 대해 동일한 처리 능력이 필요하다고 가정
  - 최소 연결(Least connection)
     - 요청이 들어온 시점에 가장 적게 연결되어 있는 서버로 요청 전송
  - 최소 응답 시간(Least Response Time)
     - 서버의 현재 연결 상태와 응답 시간을 모두 고려하여, 가장 짧은 응답 시간을 보내는 서버로 트래픽을 할당
     - 각 서버의 가용 가능한 리소스와 성능, 처리 중인 데이터양 등이 상이할 경우 적합
     - 조건에 잘 들어맞는 서버가 있을 시 여유 있는 서버보다 먼저 할당      
   

[출처1](https://www.smileshark.kr/post/what-is-a-load-balancer-a-comprehensive-guide-to-aws-load-balancer)
[출처2](https://twojun-space.tistory.com/158)
[출처3](https://habitus92.tistory.com/22)