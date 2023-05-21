# block/non-block & sync/async

여러 관점으로 정리하는 두 개념. 

## 의미적 관점에서 Block과 Non-block

한 주체(caller)가 다른 주체(callee)에게 작업을 요청했을 때 caller에게 ***제어권***이 있는지 없는지 여부에 따라 결정된다. Block/Non-block 이라는 단어가 나오면 ***제어권***을 떠올리자. 

- Block은 caller가 callee에게 작업 요청과 함께 제어권까지 줬기 때문에 callee에게 작업 결과가 올때까지 다른 일을 할 수 없다.
- Non-block은 caller가 callee에게 작업 요청과 함께 제어권을 주지 않았기 때문에 작업 요청 후에도 자기일을 계속 진행한다.

## 의미적 관점에서 Sync와 Async

한 주체(caller)가 다른 주체(callee)에게 작업을 요청했을 때 ***요청 결과의 순서/값***에 신경을 쓰는지 안 쓰는지에 따라 결정된다. Sync/Async 라는 단어가 나오면 ***시점의 일치***를 생각하자. 

- Sync에서 caller는 callee가 주는 요청 결과를 받자마자 바로 처리한다.
- Async에서 caller는 callee가 주는 요청 결과를 바로 처리하는 것에 큰 관심이 없다. 예를 들어 Javascript에서 API 호출과 함께 콜백 함수를 같이 보내는 것이다. API 호출 결과에 대해 콜백 함수가 ***언젠가*** 실행만 되면 된다.

![https://velog.velcdn.com/images%2Ftess%2Fpost%2F7f1e8bff-032f-4709-a965-f1271d02d733%2F2021-03-07T20_37_39.png](https://velog.velcdn.com/images%2Ftess%2Fpost%2F7f1e8bff-032f-4709-a965-f1271d02d733%2F2021-03-07T20_37_39.png)

## 동시에 여러 일을 하기 위한 방법

- Multiprocessing : 여러 개의 프로세스를 띄운다. Context Switching 시 많은 Overhead 발생
- Multithreading : 하나의 프로세스 안에 여러 개 쓰레드를 생성한다. Context Switching 시 Multiprocessing 보다는 적은 Overhead가 발생하지만 Race condition 같은 동기화 문제가 발생할 수 있다.
- Async programming + Non blocking I/O : 하나의 쓰레드 안에서 실행되기 때문에 Context Switching이 발생하지 않는다. Race condition을 쉽게 피할 수 있고 더 적은 Computing 작원을 사용할 수 있다.

![https://velog.velcdn.com/images%2Fcarrykim%2Fpost%2F16b41eb5-c556-48d4-82e5-7b2c0fe70d32%2Fimage.png](https://velog.velcdn.com/images%2Fcarrykim%2Fpost%2F16b41eb5-c556-48d4-82e5-7b2c0fe70d32%2Fimage.png)

## ****SYNC VS ASYNC COMMUNICATION (ARCHITECTURE)****

- Sync Communitcation : Sender가 Receiver에게 요청을 보내고 결과를 기다린다. 결과가 오면 다음 로직을 처리한다. Receiver에 장애가 발생하면 Sender에게도 영향이 발생한다.
- Async Communication : Sender는 처리하고 싶은 이벤트를 메세지 큐에 생성한다. Receiver는 메세지 큐에서 메세지를 소비하고 그에 맞는 처리를 한다. Receiver에 장애가 발생해도 Sender에는 아무런 영향이 없다. 메세지 큐는 Receiver와 Sender 사이 버퍼 메모리로 둘 간의 결합력을 끊는다.

![https://serverlessland.com/assets/visuals/eda/sync-vs-async.png](https://serverlessland.com/assets/visuals/eda/sync-vs-async.png)