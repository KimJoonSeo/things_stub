# Task scheduling model

## 정리

- Task scheduling model은 Task나 Process의 실행을 관리하기 위한 프레임워크이다. OS나 소프트웨어 시스템에서 사용한다.
- Task scheduling model은 Task(혹은 Process)의 선택, 우선 순위, 시스템 리소스(CPU 시간, 메모리) 할당 방법에 대해 정의한다.
- 크게 Preemptive Scheduling와 Cooperative Scheduling 방식이 있다.

![https://miro.medium.com/v2/resize:fit:1400/format:webp/1*lge5ThmwAKQxVejEisY0uA.png](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*lge5ThmwAKQxVejEisY0uA.png)

## Preemptive scheduling

- Task 자신이 자발적으로 CPU 제어권을 포기하는 것이 아니라 다른 것에 의해 강제로 조정되는 방식.
- 현대 OS의 대다수가 이 모델을 사용하고 있다.
- 예시) OS 커널이 CPU 를 사용중인 프로세스에게 제어권을 강제로 뺏고 다른 프로세스에게 CPU 제어권을 넘겨준다. (Context Switching)

![https://ars.els-cdn.com/content/image/3-s2.0-B9780128013144000235-f23-01-9780128013144.jpg](https://ars.els-cdn.com/content/image/3-s2.0-B9780128013144000235-f23-01-9780128013144.jpg)

## Cooperative scheduling

- Task 자신이 자발적으로 CPU 제어권을 포기하는 방식.
- 구형 OS에서 이 모델을 사용했다.
- 예시) CPU를 사용중인 프로세스가 다 사용하거나 idle 상태에 들어가면 OS에게 돌려주는 방식이 있다.
- Python이나 Javascript 같은 언어에서 Event loop기반으로 Task Scheduling을 한다. Task가 자발적으로 제어권을 넘기면 Event loop은 다른 Task에게 제어권을 스케줄링한다.

![https://tech.buzzvil.com/blog/asyncio-no-1-coroutine-and-eventloop/flow_of_example.png](https://tech.buzzvil.com/blog/asyncio-no-1-coroutine-and-eventloop/flow_of_example.png)