# Java LTS
- 자바에서 가장 많이 사용되는 버전이 자바8, 현재 21버전 까지 출시
    - 주요 Java LTS 버전은 자바 8, 11, 17 이 있음
- 스프링부트3 버전부터 자바17 이상만 지원되며 8 → 17 전환 많아짐

# Java8 추가 기능
- 2014년 릴리즈
- 람다식, 스트림 API, Interface Default Method, Optional, new Date and Teim API 등 추가

### 람다식(Lambda Expression)
- 메서드의 이름과 반환값(return) 생략으로 익명함수로 불림
- 코드가 간결해지나, 남발 시 오히려 코드 이해 어려워질 수 있음
- 전통적인 방식
```
int old(int a, int b){
    return a > b ? a : b;
}

for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```
- 람다식 방식
```
(a, b) -> a > b ? a : b;

IntStream.range(0, 10).forEach((int value) -> System.out.println(value));
```

### 스트림 API(java.util.stream)
- 컬렉션, 배열 등의 저장 요소를 하나씩 순회하며 처리하는 API
- 최종 연산이 호출되기 전까진 중간 연산 실행 X
- 전통적인 방식
```
List<String> list = Arrays.asList("newver1", "newver2", "oldver1", "newver4", "oldver5");
```
- Stream 방식
```
List.stream()
    .filter(name -> name.startWith("n"))
    .map(String::toUpperCase)
    .sorted()
    .forEach(System.out::println);
```

### Interface Default Method
- 자바8 이전에는 인터페이스 메서드 정의만 가능, 구현 불가
    - 즉, public abstract method만 가질 수 있었고, 인터페이스에 메서드를 하나 추가하면 그 인터페이스를 구       현한 모든 클래스에 그 메서드를 추가하고 구현해 줘야했었음
- 자바8 이후부터 default method 개념을 통해 구현 내용도 인터페이스 포함 가능
- static 메서드를 추가하는 것도 가능해짐

### Optional
- 예상치 못한 NullPointerException이 발생될만한 상황에서 사용
    - 자바8 이전 개발자들은 NullPointerException 발생 가능성 때문에 이에 대한 유효성 검사 및 에러 방지를        위한 코드를 추가해야 했었음
- null이 올 수 있는 값을 감싸는 컨테이너 클래스
- NullPointerException 발생하지 않도록 도와줌

### StringJoiner
- 접두사, 접미사 추가 가능
