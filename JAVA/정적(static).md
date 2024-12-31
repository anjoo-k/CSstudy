# 정적(static)이란?
- 메모리에 한 번 할당되어 프로그램이 종료될 때 해제되는 것
- static 키워드를 통해 static 영역에 할당된 메모리는 모든 객체가 공유
- BUT Garbage Collector의 관리 영역 밖이므로 사용 시 주의(프로그램 종료 시까지 메모리가 할당된 채로 존재, 시스템 성능에 영향)   
![image](https://github.com/user-attachments/assets/150dc607-9fcf-4673-9130-4ba618ba2741)
- 런타임 데이터의 영역의 메서드 영역에 static 영역이 있음
- 메서드 영역은 프로그램 시작 전에 로드되고 프로그램 종료 시 소멸됨

### static 변수
- static 변수 = 클래스 변수
- 객체를 생성하지 않고 Static 자원에 접근 가능
- 클래스 이름으로 접근 가능
```
public class Student{
    public static int age = 14;
    // -> 즉, 이 때 외부에서 Example.num 으로 이 값에 접근 가능
}
```
- static 변수 사용 이유? 공통되는 값을 중복 생성하지 않고 쓰기 위해
    - 그래서 public, final과 함께 사용되는 경우가 많음
    - 위의 예제에서 age가 14인 학생인 객체를 100개 만든다고 가정한다면, static을 쓰지 않으면 age = 14인 값이 100개 생성
    - static을 써서 여러 객체가 하나의 메모리를 참조하도록 하면 메모리 효율 높아질 것

### static 메소드
- 객체 호출 없이 생성 가능 But 지양
- 유틸리티 관련 함수들에서 자주 사용(java.util.Math 등)
- static 메소드에서는 static이 아닌 변수에 접근 불가 BUT 객체 생성 후에는 접근 가능
```
public class Student{

    public int age1 = 14;
    punlic static int age2 = 14;

    public static print(){
        System.out.println(age1); // 오류! 불가!
        System.out.println(age2); // 가능

        Student student = new Student();   // 객체 생성
        System.out.println(student.age1); // 가능: 객체를 통해 접근
    }
}
```
     
출처1 : https://mangkyu.tistory.com/47    
[출처2 Golden rabbit](https://goldenrabbit.co.kr/2021/11/03/%EC%9E%90%EB%B0%94-%EC%BD%94%EB%93%9C%EC%99%80-%EB%A9%94%EC%84%9C%EB%93%9C-%EC%8A%A4%ED%83%9C%ED%8B%B1-%EB%B3%80%EC%88%98-%EB%93%B1%EC%9D%80-%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%9D%98-%EC%96%B4%EB%94%94/)
