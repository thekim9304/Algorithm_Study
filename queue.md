# QUEUE

<center><img src=https://image.shutterstock.com/image-vector/people-long-queue-vector-illustration-260nw-1142178392.jpg width=50%></center>

- FIFO (First Input First Out, 선입선출)
- `Rear`에서 삽입, `Front`에서 삭제가 발생
- 영어 단어 queue는 표를 사러 일렬로 늘어선 사람들로 이루어진 줄을 말하기도 한다.
- 프린터의 출력 처리나 윈도우 시스템의 메시지 처리기, 프로세스 관리 등 데이터가 입력된 시간 순서대로 처리해야 할 필요가 있는 상황에 이용된다.   
> 파이썬에서는 queue 모듈에서 큐(Queue), 우선순위큐(PriorityQueue), 스택(LifoQueue)을 제공하고 있다. 
####

- 선형큐, 환형큐, 우선순위큐

#### Enqueue

- 데이터 입력
<center><img src=https://wayhome25.github.io/assets/post-img/cs/queue1.jpg width=50%></center>

- `queue overflow` : 큐가 꽉 차서 더이상 자료를 넣을 수 없는 경우

#### Dequeue

- 데이터 삭제
<center><img src=https://wayhome25.github.io/assets/post-img/cs/queue2.jpg width=50%></center>

- `queue underflow` : 큐가 비어있어 자료를 꺼낼 수 없는 경우
