![image](https://github.com/user-attachments/assets/3e1acaa0-cec3-4ad7-bcd6-b2b0e7de94c8)

### 자바의 예외
- Error
    - 시스템에 비정상적인 상황 발생
    - 메모리 부족(OutofMemoryError), 스택오버플로우(StackOverFlowError), ThreadDeath 등
    - try-catch로 대응 불가, 개발자 예측 불가
- Checked Exception
- UnChecked Exception

# Checked Exception : 컴파일러가 체크
- RuntimeException의 하위 클래스 X, Exception의 하위 클래스
- 반드시 에러 처리를 해야(try-catch)
- 컴파일 단계에서 발생할 수 있는 예외
- 컴파일되기 위한 선택지 두 가지 : try-catch, throws 중 하나를 처리해줘야 컴파일 가능(아니면 컴파일 에러)
  → 자바에서 보통 IDE에서 선택 강제함
- 예시) IOException, ClassNotFoundException 등
- **Rollback 하지 않고 commit까지 완료**
    - Checked Exception은 복구 가능한 상황에서 발생
    - 이를 처리한 후 정상적인 처리가 가능한 상태로 간주
    - 트랜잭션의 관점에서는, 예외가 발생했더라도 이를 적절히 처리한 경우 비즈니스 로직을 완료 가능

# Unchecked Exception
- RuntimeException의 하위 클래스
- 에러 처리를 강제하진 않음 : try-catch 하지 않아도 컴파일됨
  → 에러 처리를 강제한다면 단순 배열을 하나 출력하는데도 try-catch문을 사용해야 하는 등 불편
- 실행 중에(runtime) 발생할 수 있는 예외
- 별도의 throws가 필요 없음
- 예시) NullPointerException, IllegalArgumentException, IndexOutOfBoundException 등
- **Rollback 함**
  - 복구가 어려운 심각한 오류 상황에서 발생, 프로그램의 로직에 문제가 있다고 간주
  - 트랜잭션을 커밋하면 데이터의 일관성이 깨질 위험


출처 : https://devlog-wjdrbs96.tistory.com/351
