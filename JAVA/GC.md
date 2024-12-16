# 가비지 컬렉션(Garbage Collection, GC)
### 가비지 컬렉터란?
- 자바의 메모리 관리 방법
- JVM(자바 가상 머신) Heap 영역에서 동적으로 할당했던 메모리 중 필요 없게 된 메모리 객체를 모아 주기적으로 제거
- 장점
  - C/C++ 언어에서는 프로그래머가 수동으로 메모리 할당과 해제를 해줘야 했음
  - JAVA에서는 GC가 대신 해주기 때문에 개발에만 집중 가능
- 단점
  - 메모리가 언제 해제되는지 알 수 없어 제어 힘듬
  - GC가 동작하는 동안 다른 동작 멈추기 때문에 오버헤드 발생(Stop-The-World)
    
### 가비지 컬렉션의 영역
- JVM의 Heap 영역을 처음 설계할 때 전제한 두가지
   - 대부분의 객체는 금방 접근 불가능한 상태(Unreachable)가 된다.
   - 오래된 객체에서 새로운 객체로의 참조는 아주 적게 존재한다.
   -     Reachable : 객체가 참조되고 있는 상태
         Unreachable : 객체가 참조되고 있지 않은 상태(GC의 대상)
- 즉, 객체는 대부분 일회성, 메모리에 오래 남아 있는 경우 드물어
- 따라서 객체의 생존 기간에 따라 물리적인 Heap 영역 쪼갬 → Young, Old(Perm 영역도 있었으나 자바 8부터 제거)
- **Young 영역(Minor GC)**
    - 새로운 객체 할당(Allocaition) 되는 영역
    - 대부분의 객체가 Unreachable 상태 되기 때문에 많은 객체가 Young 영역에 생성되었다가 사라짐
    - 이 영역에 대한 가비지 컬렉션을 Minor GC라고 부름
    - 이 부분을 또 3가지 영역(Eden, survivor 0, survivor 1)로 나눔
       - Eden : new를 통해 새로 생성된 객체 위치, 꽉 차면 Minor GC 발생
       - survivor 0/survivor 1 : 최소 1번 GC 이상 살아남은 객체 존재, 2개지만 반드시 1개 영역에만 데이터 존재해야
       - 1. 새로 생성된 객체가 Eden 영역에 할당
         2. Eden 영역이 꽉 차면 Minor GC가 실행
         3. 이 때 살아남은 객체는 Survivor 영역이로 이동
         4. 1 ~ 3번 반복 -> Survivor 영역이 가득 차면 객체들을 다른 Survivor 영역으로 이동(1개의 Survivor 영역은 반드시 비어있어야)
         5. 이 과정이 반복되다가 계속해서 살아남은 객체는 Old 영역으로 이동(Promotion)
            - 객체의 생존 횟수 카운터는 Object Header에 age 기록, Minor GC 때 기록된 age 보고 Promotion 여부 결정
![image](https://github.com/user-attachments/assets/f87662db-7168-49ce-b16a-70644bb9ad49)

- **Old 영역(Major GC)**
    - Young 영역에서 Reachable 상태를 유지하며 살아남은 객체 복사되는 영역
    - Young 영역보다 크게 할당, 영역 크기가 큰 만큼 가비지는 적게 발생
    - 이 영역에 대한 가비지 컬렉션을 Mojor GC라고 부름

### 가비지 컬렉션은 어떤 객체를 Garbage로 판단해서 지울까?
![image](https://github.com/user-attachments/assets/a1d575f3-3be2-4161-8fd8-7460559d3f54)
- 위 그림을 보면 JVM 메모리에서 객체들은 실질적으로 Heap 영역에서 생성되고 Method Area나 Stack Area에서는 Heap Area에 생성된 객체의 주소만 참조하는 형식으로 구성
- 참조하고 있지 않은 객체를 가비지 컬렉터가 제거해 주는 것
- 즉, 여기서 객체에 레퍼런스가 있으면 Reachable, 유효한 레퍼런스가 없으면 Unreachable로 구분해 수거
- Heap Area의 객체들이 메서드가 끝나거나 메모리 주소 참조 변수가 삭제되면 -> Unreachable이 발생
- 이러한 객체들을 지워 주는 것

### 가비지 컬렉션의 동작 방식
- Young 영역과 Old 영역은 서로 다른 메모리 구조, 세부적인 동작 방식도 다름
- 하지만 아래의 공통된 작업을 수행함
1. Stop The World
   - 가비지 컬렉션을 실행하기 위해 JVM이 애플리케이션의 실행을 멈추는 작업
   - GC가 실행될 때는 GC를 실행하는 쓰레드를 제외한 모든 쓰레드들의 작업 중단, GC 완료 후 작업 재개
   - GC 성능 개선을 위해 튜닝한다고 하면 이 구간의 시간을 줄이는 작업을 하는 것
2. Mark and Sweep
   - Mark : 사용되는 메모리와 사용되지 않는 메모리 식별
   - Sweep : Mark 단계에서 사용되지 않음으로 식별된 메모리 해체
   - Stop The World를 통해 모든 작업 중단 -> GC는 스택의 모든 변수, Reachable 객체 스캔하며 탐색   
     -> 사용되고 있는 메모리 식별(Mark) -> Mark되지 않은 객체 제거(Sweep)
3. Compact : 가비지 컬렉터 종류에 따라 실행 여부 갈림
  
### 가비지 컬렉션이 필요한 이유


### 가비지 컬렉션 청소 방식


질문1. 가비지 컬렉션이 어떤 객체를 Garbage로 고르는가?
질문2. 가비지 컬렉션의 Young 영역에 대해 아는데로 설명해 보시오.
