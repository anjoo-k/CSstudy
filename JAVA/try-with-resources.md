# try-with-resources
### 자바 Resource 예외 처리
- resource란? 외부 데이터(DB, Network, File) 등
    - 리소스는 자바 외부에 위치한 요소들
    - 이 외부요소에 자바가 접근할 때 문제(예외) 발생 가능
- resource 사용 후 닫아 주는 것이 중요
    - 닫아주지않아서 리소스를 사용이 중복되면 프로그램 오작동 가능성 발생
    - 따라서 finally 문으로 파일을 close() 처리 해 주어야
    - **BUT** close() 동작 자체도 예외 발생 가능! 예외 처리 해 줘야
      ```
      import java.io.FileWriter;
      import java.io.IOException;
      
      public class Main {
          public static void main(String[] args) {
              FileWriter file = null;
              try {
                  file = new FileWriter("data.txt");
                  file.write("Hello World");
              } catch (IOException e) {
                  throw new RuntimeException(e);
              } finally {
                // 작업중에 예외가 발생하더라도 파일이 닫히도록 finally블럭에 넣음
                // 근데 close()가 예외를 발생시키면 문제가 됨
                // close()에서 발생하는 예외를 처리하기 위해
                // 아래와같이 바꿀수도 있지만 코드가 복잡해져 가독성 저하
                  try {
                      file.close();
                  } catch (IOException e) {
                      throw new RuntimeException(e);
                  }
              }
          }
      }
      ```
### 그래서 좀 더 간편하게 구성한 예외 처리 문법 자바7 버전에서 출시
- 주로 입출력(I/O)과 관련된 클래스 사용 시 유용
- 입출력 사용 객체를 자동 반환해 주기 때문
- try-with-resource 문의 () 안에 객체 생성 문장을 넣으면
  따로 close() 호출 없이 try문 벗어나면 자동 close() 호출
  ```
  import java.io.FileWriter;
  import java.io.IOException;
  
  public class Main {
      public static void main(String[] args) {
          try (FileWriter file = new FileWriter("data.txt")) {
              file.write("Hello World");
          } catch (IOException e) {
              e.printStackTrace();
          }
      }
  }
  ```



출처 : https://inpa.tistory.com/entry/JAVA-☕-예외-처리-Try-With-Resource-문법 [Inpa Dev 👨‍💻:티스토리]
