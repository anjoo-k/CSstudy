# Synchronous&Asynchronous 그리고 Blocking&Non-Blocking
- 동기(Synchronous): 하나가 끝나야 다음 작업을 실행할 수 있음
- 비동기(Asynchronous): 작업이 끝날 때까지 기다리지 않고, 나중에 처리
- 차단(Blocking): 작업이 끝날 때까지 기다리며, 다른 작업을 못 함
- 비차단(Non-Blocking): 작업을 기다리는 동안 멈추지 않고 다른 작업을 처리 가능   


![image](https://github.com/user-attachments/assets/a218cd73-7b4c-4290-ac4c-e310ddc6f1c0)   
[그림출처](https://homoefficio.github.io/2017/02/19/Blocking-NonBlocking-Synchronous-Asynchronous/)    

### 함수 호출 단위일 때, 차단/비차단, 동기/비동기의 개념 적용
1. 동기 vs 비동기 (Sync vs Async)
- 동기(Sync): 함수 호출이 반환될 때까지 기다림
- 비동기(Async): 함수 호출이 즉시 반환되고, 나중에 결과를 처리   
2. 차단 vs 비차단 (Blocking vs NonBlocking)
- 차단(Blocking): 작업이 끝날 때까지 해당 실행 흐름이 멈춤
- 비차단(NonBlocking): 작업이 끝나지 않아도 바로 다음 코드를 실행


[출처](https://musma.github.io/2019/04/17/blocking-and-synchronous.html)
