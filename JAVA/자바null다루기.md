# 자바에서 null을 다루는 방법
### null
- 값이 없다는 의미인 null, 개발자들의 영원한 숙제 NullpointerException
- 원시형 자료는 개별적으로 0이나 공백을 통해 값이 없다는 것을 표현. 하지만 참조형은 null 발생 가능
- 참조형 변수(포인터)에 메모리의 주소값이 들어와야 되지만, 그 값이 없을 때 아무 것도 없다는 것을 표현하기 위한 키워드가 NULL
- = 주소값이 없다, 아무것도 가리키고 있지 않다.

### null 방어법
1. 조건문 중첩 코딩
   ```
   Person p = new Person("홍길동");
   // p.getPhone().getOS().printOS();
    
   Phone ph = p.getPhone();
   if (ph != null) {
       OS o = ph.getOS();
       if(o != null) {
           String n = o.printOS();
       }
   }
   ```
2. Optional 클래스 사용
   - Java8이 등장하며 null에 대한 처리를 정식적으로 지원하는 클래스 추가
   ```
   import java.util.Optional; // Optional 클래스 사용하기 위해 import

   class Person { ... }
   class Phone { ... }
   class OS { ... }
  
   public class Main {
       public static void main(String[] args) {
           Person p = new Person("홍길동");
           
           Optional.ofNullable(p)
                   .map(Person::getPhone)
                   .map(Phone::getOS)
                   .map(OS::printOS);
       }
   }
   ```


출처1 : https://le2ksy.tistory.com/65   
출처2 : https://bbbicb.tistory.com/71   
출처3 : https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%93%A4%EC%9D%84-%EA%B4%B4%EB%A1%AD%ED%9E%88%EB%8A%94-NULL-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0
