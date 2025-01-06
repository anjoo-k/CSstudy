# JAVA 실행 방식
### JVM(Java Virtual Machine, 자바 가상 머신) 이란?
  - 자바 프로그램 실행 환경을 만들어주는 소프트웨어
  - 자바 코드를 컴파일해 .class 바이트 코드로 만들면 이 코드가 자바 가상 머신 환경에서 실행
  - 현재 사용하는 컴퓨터의 운영체제에 맞는 자바 실행 환경(Java Runtime Environment;JRE)이 설치되어 있다면 자바 가상 머신이 설치되어 있는 것
  - JVM(자바 가상 머신)은 자바 언어에서만 사용하는 것이 아니다. 코틀린, 스칼라 언어에서도 JVM 동작 방식을 그대로 따름!   
    -> 파생 언어 이해 높힐 수 O
  ![image](https://github.com/user-attachments/assets/e1c35228-8d65-4f1f-991a-2c47dc83c337)
  - 위 그림은 자바 애플리케이션의 구동원리를 간략하게 그려본 것인데, 지금부터 우리가 배울 JVM(자바 가상 머신) 실행 부분은 빨간 박스를 친 부분인, 컴파일된 .class 파일을 어떠한 처리를 거쳐 프로그램을 실행하는 과정
   
### 자바 가상 머신(JVM)의 동작 방식
  - .class 파일은 어떤 방식을 거쳐 실행되는가?
  ![image](https://github.com/user-attachments/assets/c89780cf-79b2-4427-8340-98cb7e1035c5)
  - JVM의 역할은 자바 애플리케이션을 클래스 로더를 통해 읽어 자바 API와 함께 실행하는 것
  - 자바 프로그램을 실행하면
     - JVM은 OS로부터 메모리 할당받음
     - 자바 컴파일러(javac)가 자바 소스코드(.java)를 자바 바이트코드(.class)로 컴파일
     - Class Loader는 동적 로딩 통해 필요한 클래스들을 로딩 및 링크해 Runtime Data Area(실제 메모리 할당받아 관리하는 영역)에 올림
     - Runtime Data Area에 로딩 된 바이트 코드는 Execution Engine 통해 해석
     - 이 과정에서 Execution Engine에 의해 Gargabe Collector의 작동과 Thread 동기화 이루어짐
### JVM의 구조
  ![image](https://github.com/user-attachments/assets/b96a99f0-7498-40d4-9667-cfd76376dad5)
  - 위 그림은 Class Loader <-> Execution Engine <-> Runtime Data Area 부분을 상세화 한 것
  - **클래스 로더(Class Loader)**
      - JVM 내로 클래스 파일 로드(*.class), 링크 통해 배치   
        = 로드된 바이트 코드(*.class)들을 JVM 메모리 영역인 Runtiem Data Areas
      - 클래스를 메모리에 올릴 때 어플리케이션에서 필요한 경우 동적으로 적재
  - **실행 엔진(Execution Engine)** : 바이트 코드를 명령어 단위로 읽어 실행
  -      자바 바이트 코드(.class)는 기계가 바로 수행할 수 있는 언어 X, 가상머신이 이해할 수 있는 중간 레벨로 컴파일된 코드
         실행 엔진은 이런 바이트 코드를 실제 JVM 내부에서 기계가 실행 가능한 형태로 변경
     - 인터프리터(InterPreter)
         - 명령어를 하나씩 읽어서 해석, 실행
         - JVM 안에서 기본 방식 BUT 같은 메소드도 매번 재호출되어 속도가 느림
     - JIT 컴파일러(Just-in-Time)
         - 인터프리터 단점 보완 : 반복되는 코드를 컴파일하여 Native Code로 변경 후 캐싱해 두었다가 네이티브 코드로 직접 실행
         - 인터프리팅 방식보다 빠름
     - Garbage Collector
         - 힙 메모리 영역에서 더 사용하지 않는 메모리 자동 회수
  - **런타임 데이터 영역(Runtime Data Area)**
  -     JVM 메모리 영역으로 자바 애플리케이션 실행할 때 사용되는 데이터 적재하는 영역
  ![image](https://github.com/user-attachments/assets/e2b5ffda-9d91-40ea-a993-1f18b457034d)   
     - **메소드 영역** : JVM에서 읽어드린 클레스와 인터페이스에 대한 상수 풀, 메서드와 필드, Static 변수, 메서드 바이트 코드 등 보관
     - **힙 영역** : 프로그램 상에서 데이터 저장, 런타임 시 동적으로 할당해 사용하는 메모리 영역, new 연산자를 통한 객체 또는 인스턴스, 배열 저장
     - **PC register** : 현재 실행 중인 JVM 주소 가지고 있음, CPU 명령어 수행
     - **스택영역** : 선입선출, 메서드 호출 시 생성되는 스레드 수행정보 기록하는 Frame 저장, 메서드 정보, 지역변수, 매개변수, 연산 중 발생하는 임시 데이터 저장
     - **네이티브 메소드** : 자바 외 언어올 작성된 네이티브 코드 위한 메모리
  - JNI : 네이티브 메소드 인터페이스(Native Method Interface)
  - 네이티브 메소드 라이브러리(Native Method Library)   

  
그림, 내용출처: https://inpa.tistory.com/entry/JAVA-☕-JVM-내부-구조-메모리-영역-심화편#자바_가상_머신jvm의_구조 [Inpa Dev 👨‍💻:티스토리]
