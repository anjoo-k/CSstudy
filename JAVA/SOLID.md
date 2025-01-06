# 객체 지향 설계의 5원칙 SOLID
- 객체지항 설계에서 지켜야할 5개의 소프트웨어 개발 원칙
- 코드 확장, 유지 보수에 좋고, 유연성 증가, 개발 생산성 높히기 위함
- 단일 책임 원칙(SRP, Single Responsibility Principle)
- 개방 폐쇄 원칙(OCP, Open Closed Principle)
- 리스코프 치환 원칙(LSP, Liskov Substitution Principle)
- 인터페이스 분리 원칙(ISP, Interface Segregation Principle)
- 의존 역전 원칙(DIP, Dependency Inversion Principle)

### 단일 책임 원칙(SRP, Single Responsibility Principle)
- **클래스(객체)는 단 하나의 책임만 가져야 한다.**
- 책임 = 기능, 즉 하나의 클래스는 하나의 기능을 담당해 하나의 책임을 수행하도록 설계해야
- 만약 하나의 클래스에 기능(책임)이 여러개라면, 변경(수정)이 발생하면 수정할 코드가 많아짐
- 프로그램의 유지보수 성을 높이기 위함
- 책임의 범위는 어떤 프로그램인지, 개발자의 기준에 따라 달라질 수 있음

### 개방 폐쇄 원칙(OCP, Open Closed Principle)
-** 확장에는 열려있고, 수정에는 닫혀있어야 한다.**
- 기능 추가가 필요할 때, 클래스 확장을 통해 손쉽게 구현 but 수정은 최소화 되도록
- 추상화 사용을 통한 관계 구축을 말하는 것

### 리스코프 치환 원칙(LSP, Liskov Substitution Principle)
- **서브 타입은 언제나 기반(부모) 타입으로 교체할 수 있어야 한다.**   
= 부모 객체를 호출하는 동작에서 자식 객체가 부모 객체를 완전히 대체할 수 있다.   
- 다형성 원리를 이용하기 위한 원칙

### 인터페이스 분리 원칙(ISP, Interface Segregation Principle)
- **인터페이스를 각각 사용에 잘 맞게 분리해야 한다.**
- SRP 원칙이 클래스의 단일 책임을 강조, ISP는 인터페이스의 단일 책임 강조
- SRP 는 클래스 분리를 통해 설계, ISP는 인터페이스 분리 통해 설계

출처 : https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%EC%84%A4%EA%B3%84%EC%9D%98-5%EA%B0%80%EC%A7%80-%EC%9B%90%EC%B9%99-SOLID

### 의존 역전 원칙(DIP, Dependency Inversion Principle)
- 어떤 클래스를 참조해서 사용해야할 상황이 생긴다면, 그 클래스를 직접 참조하지 말고 그 대상의 상위 요소(추상 클래스, 인터페이스)로 참조해야 한다.
- **구현 클래스에 의존 X, 인터페이스에 의존 O**
