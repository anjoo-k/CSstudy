### String
- Stirng은 불변 = 한 번 할당된 공간이 변하지 않음
```
String str = "Hello";
str = str + " World";
```
- 위와 같은 연산을 한다면, 메모리에서는 아래 그림과 같이 "Hello" 저장 영역과 "Hello World" 저장 영역이 따로 만들어짐   
![image](https://github.com/user-attachments/assets/d6fc7b6c-606d-42a4-b2cc-3bf0c743b9e5)   
- 따라서 초기 공간과 다른 값에 대한 연산에서 시간과 자원을 많이 사용하게 됨

### StringBuilder/StringBuffer
- StringBuilder, StringBuffer는 가변
- 객체의 공간이 부족해지는 경우 버퍼의 크리글 유연하게 늘려줌
- 두 클래스는 Buffer(데이터를 임시로 저장하는 메모리)에 문자열을 저장해 두고 그 안에서 수정 작업함   
![image](https://github.com/user-attachments/assets/174ef361-5440-4ca0-be3b-2a0fc7825d06)   
- 가변성이라 .append(), .delete() 등으로 동일 객체 내에서 문자열 크기 변경 가능
- String에 비해 값이 변경될 때 더 빠르므로 문자열 수정이 빈번하게 발생하는 경우 사용하는 것이 좋음

### String과 StringBuilder/StringBuffer 값 동등성 비교
- String은 equals() 메서드 통해 문자열 데이터 동등 비교 가능
- StringBuilder/StringBuffer는 equals() 메서드 오버라이딩 하지 않아 '=='결과가 나오므로 toString()으로 객체를 변환 후 equals() 비교

### StringBuilder/StringBuffer 차이점
- 멀티쓰레드에서 안전한지
- StringBuilder는 안전 -> 동기화(Synchronization) 지원하지 않음
- StringBuffer는 안전하지 않음 -> 동기화 지원해 멀티스레드 환경에서 안전하게 동작 가능   
   
    
출처 : https://inpa.tistory.com/entry/JAVA-%E2%98%95-String-StringBuffer-StringBuilder-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EC%84%B1%EB%8A%A5-%EB%B9%84%EA%B5%90#stringbuffer_/_stringbuilder_%ED%81%B4%EB%9E%98%EC%8A%A4
