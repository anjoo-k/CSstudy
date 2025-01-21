### 자바의 객체는 기본적으로 힙 영역에 할당, 스택 영역에 참조값(주소값) 가짐

# Immutable(불변) 객체
- 데이터 변경이 불가능한 객체
- 객체 생성 이후 내부 상태가 변하지 않으며, read-only 메소드만 제공
- 정확히는 힙 영역에 저장된 값을 수정할 수 없음
- 대표적인 예시 String, Boolean, Integer, Float, Long, Double 등
    - 우리는 이 객체들을 수정 가능하게 생각함
    - 하지만 메모리상에서는 저장된 값이 수정된 것이 아니라 힙 영역에 새로운 객체가 생성된 것
    - 수정 시 기존 할당되었던 객체는 GC로 처리
- 자바에서는 불변성 확보를 위해 final 키워드 제공

### Immutable(불변) 객체 장단점
- 장점 : Thread-Safe, 멀티스레드 프로그래밍에 유용, 동기화 처리 없이 공유 가능, 예외가 발생해도 메소드 호출 전의 상태를 유지
- 단점 : 객체 값이 할당될 때마다 새로운 객체 필요 -> 메모리 누수, 성능저하 발생

# Mutable(가변) 객체
- 불변 객체와 반대
- 힙 영역에 생성된 객체 변경 가능
- 멀티스레드 환경에서 사용하기 위해서는 별도 동기화 처리 필요   

![image](https://github.com/user-attachments/assets/5c15b36e-1574-49ef-a4f7-4258ad3aece3)   

      
출처1 : https://choiblack.tistory.com/47   
출처2 : https://mangkyu.tistory.com/131   
출처3(그림) : https://velog.io/@guswlsapdlf/Java%EC%9D%98-Mutable%EA%B3%BC-Immutable   
출처4 : https://velog.io/@dabeen-jung/Java-Mutable%EA%B3%BC-Immutable-%EC%B0%A8%EC%9D%B4
