# block/non-block & sync/async

케이스 바이 케이스로 정리하는 두 개념. 

## Block과 Non-block의 의미

한 주체(caller)가 다른 주체(callee)에게 작업을 요청했을 때 caller에게 ***제어권***이 있는지 없는지 여부에 따라 결정된다.

- Block은 caller가 callee에게 작업 요청과 함께 제어권까지 줬기 때문에 callee에게 작업 결과가 올때까지 다른 일을 할 수 없다.
- Non-block은 caller가 callee에게 작업 요청과 함께 제어권을 주지 않았기 때문에 작업 요청 후에도 자기일을 계속 진행한다.

## Sync와 Async의 의미

한 주체(caller)가 다른 주체(callee)에게 작업을 요청했을 때 ***요청 결과의 순서/값***에 신경을 쓰는지 안 쓰는지에 따라 결정된다.

- Sync에서 caller는 callee가 주는 요청 결과를 받자마자 바로 처리한다.
- Async에서 caller는 callee가 주는 요청 결과를 바로 처리하는 것에 큰 관심이 없다. 예를 들어 Javascript에서 API 호출과 함께 콜백 함수를 같이 보내는 것이다. API 호출 결과에 대해 콜백 함수가 ***언젠가*** 실행만 되면 된다.