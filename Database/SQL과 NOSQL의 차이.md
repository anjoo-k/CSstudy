# SQL? NoSQL?
### 먼저 알아두어야 할 내용
    - **RDB(Relational Database, 관계형 데이터 베이스)**   
      : 테이블의 행과 열을 통해 정보를 구조화하고 테이블간 관계를 키(예: 기본키, 외래키)를 통해 연결
    - **DBMS(Database Management System)**   
      : 데이터베이스를 관리하고 운영하는 소프트웨어
    - **RDBMS(Relational Database Management System)**   
      : RDB를 관리하기 위한 소프트웨어 또는 그것이 설치된 시스템
- **SQL(Structured Query Language)**   
  : SQL(구조화 질의어, S-Q-L)은 관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리하기 위해 설계한 특수 목적의 프로그래밍 언어
- **NoSQL(Non-relational database)**   
  : Not only SQL. 문서, 그래프 데이터베이스, 키-값 저장소와 같은 비관계형 데이터 구조를 사용하여 데이터를 저장하고 검색하는 데이터베이스   
![image](https://github.com/user-attachments/assets/d82e3a13-0b32-4196-bcd0-50e59c83f151)

### NoSQL의 3가지 주요 유형
**1. 문서(Document) 데이터베이스**
    - 예: MongoDB
    - JSON 형식으로 데이터를 저장 → 데이터 구조의 유연성이 높음.
    - SQL처럼 테이블 구조를 강제하지 않음.

**2. 키-값(Key-Value) 데이터베이스**
    - 예: CassandraDB, DynamoDB
    - 빠른 데이터 읽기/쓰기 속도 제공.
    - Netflix, Uber, Apple 같은 대규모 서비스에서 사용.

**3. 그래프(Graph) 데이터베이스**
    - 예: Neo4j, Facebook의 Tao
    - 데이터 간의 관계를 저장하고 조회하는 데 최적화됨.
    - 소셜 네트워크 서비스에서 주로 활용됨.
![image](https://github.com/user-attachments/assets/b28b98aa-239d-4cad-abca-ddc88899ca30)


# SQL과 NoSQL의 차이
### SQL
- 고정된 열과 행으로 구성된 테이블에 데이터 구조와 타입 등을 사전에 정의하고 그에 맞는 정보만 저장 가능
- 정보 요청 시 SQL과 같이 구조화된 쿼리 언어를 사용
- 수직적 확장
### NoSQL
- SQL 기반이 아닌, 다양한 형태의 데이터 저장 가능 = SQL보다 유연
- 정보 요청 시 구조화되지 않은 쿼리 언어로도 사용 가능
- 수평적 확장

# 둘 중 어느 것을 선택?
### 기본적으로 SQL
- 데이터베이스의 ACID를 준수해야 하는 경우(Atomicity 원자성, Consistency 일관성, Isolation 격리성, Durability 지속성)
- 즉, 트랜잭션 수행할 때 안전성 보장 필요 = 예외 상황 줄이고 **데이터 무결성 보장**
### 특정한 상황에서 NoSQL
- 데이터 구조가 없는 대용량 데이터 저장
- 데이터베이스 확장성이 중요할 때
- 데이터 구조를 자주 업데이트 해야하는 경우


### 출처
https://ko.wikipedia.org/wiki/%EA%B4%80%EA%B3%84%ED%98%95_%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%EA%B4%80%EB%A6%AC_%EC%8B%9C%EC%8A%A4%ED%85%9C   
https://ko.wikipedia.org/wiki/SQL    
https://velog.io/@thehill_hannam/RDB-vs-NoSQL   
https://www.integrate.io/ko/blog/the-sql-vs-nosql-difference-ko/   
**https://gowithcode.com/sql-vs-nosql**   
https://velog.io/@thehill_hannam/RDB-vs-NoSQL   
https://ittrue.tistory.com/195   
https://hanamon.kr/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-sql-vs-nosql/
