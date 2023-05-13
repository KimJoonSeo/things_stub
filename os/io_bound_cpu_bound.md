# CPU Bound & I/O Bound

## Burst

Burst는 프로세스가 특정 Task의 실행을 완료하는데 걸리는 시간을 의미한다. `CPU Scheduling` 관점에서 2가지 Burst가 있다.

- CPU Burst : 프로세스가 CPU를 점유하고 한번에 연산을 연속적을 실행하는 시간
- I/O Burst : I/O 작업의 결과를 기다리는데 걸리는 시간

프로세스의 실행은 CPU Burst와 I/O Burst가 번갈아 발생한다.

![cpu burst and io burst](https://www.cs.odu.edu/~price/cs471/public_html/spring17/lectures/Scheduling_files/image002.jpg)


## Comparison

- CPU Bound Process는 CPU Burst가 상대적으로 많은 Process 이다. 복잡한 알고리즘을 수행하는 머신러닝 프로그램을 그 예로 볼 수 있다.
- I/O Bound Process는 I/O Burst가 상대적으로 많은 Process 이다. 일반적인 API 서버가 그 예라고 할 수 있는데 DB, Cache, API 서버와 같은 외부 서비스와의 네트워크 I/O가 많기 때문이다.