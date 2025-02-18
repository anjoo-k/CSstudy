# 트랜잭션의 ACID 속성과 격리(Isolation)
### ACID : 데이터베이션 트랙잭션이 가져야 할 4가지 속성
- Atomicity 원자성
- Consistency 일관성
- **Isolation 격리성  →  이번에 공부할 것**
- Durability 지속성
> **Isolation 이란?**
> 동시에 실행되는 여러 트랜잭션이 서로 영향 주지 않도록 방지, 격리 수준에 따라 데이터 일관성 달라짐

###

트랜잭션 격리 수준이란?

동시 실행되는 트랜잭션 간 간섭을 방지하는 데이터베이스의 중요한 기능.
격리 수준이 낮으면?

Dirty Read, Non-Repeatable Read, Phantom Read 같은 문제가 발생할 수 있음.
MySQL vs PostgreSQL 차이점

PostgreSQL은 의존성 검사를 통해 데이터 무결성을 보장하며,
MySQL은 Locking 기반으로 격리 수준을 구현함.
🚀 즉, 데이터 일관성과 성능 사이에서 적절한 격리 수준을 선택하는 것이 중요
