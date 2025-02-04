# SQL injection
- SQL을 조작하여 해킹하는 기법
- 웹 애플리케이션의 입력 필드(예: 로그인 페이지)에 악의적인 SQL 문을 삽입하여 데이터 탈취, 변경, 삭제 등을 수행
- 해커가 로그인 우회, 데이터 유출, 관리자 권한 획득 등의 공격 시도 가능

# SQL Injection 공격 원리
### 해커가 로그인 창에 특수 문자열을 입력하여 쿼리를 조작하는 것
- 일반적인 로그인 동작
```
SELECT * FROM users WHERE username = 'admin' AND password = '1234';
```
- SQL Injection 공격 예제1
> '1'='1'은 항상 참(True)이므로 모든 사용자 데이터 조회 가능, 
> 결과적으로 비밀번호를 몰라도 로그인 가능
```
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
```
- SQL Injection 공격 예제2
> -- 이후의 내용이 주석 처리되어 모든 사용자의 데이터가 조회
```
ID: ' OR '1'='1' --  
PW: (아무 값 입력)
```
```
SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '';
```

# SQL Injection 방어 방법
### 1. 입력값 검증 필터(Input Valication)
- 사용자가 입력하는 특수 문자(예: ', ", --, ;, = 등)를 제거 또는 필터링
- 완벽한 안전 보장 X
```
public static String sanitizeInput(String input) {
    return input.replaceAll("['\";--]", "");  // 특수 문자 제거
}
```

### 2. SQL 쿼리에 바인딩 변수(PreparedStatement) 사용
- 가장 효과적인 방법
- 변수를 SQL 쿼리와 분리하여 안전하게 처리
```
// 취약한 방식
String query = "SELECT * FROM users WHERE username = '" + username + "' AND password = '" + password + "'";
Statement stmt = connection.createStatement();
ResultSet rs = stmt.executeQuery(query);

// PreparedStatement 사용
String sql = "SELECT * FROM users WHERE username = ? AND password = ?";
PreparedStatement pstmt = connection.prepareStatement(sql);
pstmt.setString(1, username);
pstmt.setString(2, password);
ResultSet rs = pstmt.executeQuery();
```

### 3. ORM(JPA, Hibernate) 사용
-  JPA는 내부적으로 바인딩 변수를 사용하므로 SQL Injection 방어 가능
