#  Redis(Remote Dictionary Server)
- "키-값" 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반 비관계형 데이터베이스 관리 시스템(DMBS)
- 일반적인 데이터베이스가 아니라 캐싱(Cache) 용도로 많이 사용
- 서브 밀리초(ms) 단위의 응답 속도를 자랑하는 인메모리 멀티 모델 데이터베이스
> **Redis는 속도가 빠른 key-value 형태 저장 데이터베이스**

## Redis 탄생 배경
> 트위터 같은 애플리케이션이 폭발적으로 성장하던 시기, 기존의 관계형 데이터베이스(RDBMS)는 증가하는 트래픽을 감당하기 어려웠고 빠른 데이터 전달이 가능하면서도 확장성이 뛰어난 솔루션이 필요 = Redis 탄생

## Redis 핵심 개념
### RAM에서 직접 데이터 읽고 쓴다(In-Memory) = 빠름
### RAM은 휘발성 BUT 지속성(Persistence)보장
- 스냅샷(snapshot), 백업 기능
- 스냅샷? 특정 시점 데이터 그대로 저장하는 방식
- Redis에서는 RDB(Redis Database) 방식 사용해 데이터를 일정한 간격으로 파일에 저장
- **단점** : 최신 데이터 유실 가능, 실시간 데이터 저장 필요 시 부적합
### "키-값" 저장 방식
- 문자열(String), 리스트(List), 해시(Hash), 집합(Set), 정렬된 집합(Sorted Set) 등 다양한 데이터 구조 지원

## 언제 캐싱이 필요할까?
✔ 웹 캐싱(Cache) → 빠른 데이터 제공   
✔ 세션 관리(Session Store) → 로그인 데이터 저장   
✔ 분산 락(Distributed Lock) → 여러 서버의 동시 접근 제어   
✔ 속도 제한(Rate Limiter) → API 요청 속도 제한   
✔ 메시지 큐(Message Queue) & 스트림 처리 → 실시간 데이터 처리   


출처 : https://youtu.be/G1rOthIU-uo?si=LeLkWAap00p8jqXP   
출처 : https://youtu.be/a4yX7RUgTxI?si=iPh9IBbqfDVSPMdD
