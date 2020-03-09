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

#

- Queue는 리스트로 구현하는 것도 가능하지만 효율적이지 않다.
- 리스트는 끝에 원소를 덧붙이거나, 끝에서 꺼내는(pop()) 작업은 빠르지만 리스트의 맨 처음에 원소를 추가하거나 빼는 것은 느리다.

#### [구현] python list 사용

##### ADT
>def enqueue - 삽입 (Rear에 데이터 입력)   
def dequeue - 삭제 (Front에 있는 데이터 추출)   

```python
class ListQueue(list):
  def __init__(self):
    self.queue = []

  def enqueue(self, data):
    self.queue.append(data)

  def dequeue(self):
    if len(self.queue) == 0:
      return -1
    return self.queue.pop(0)

  def printQueue(self):
    print(self.queue)

if __name__=="__main__":
  lq = ListQueue()
  lq.enqueue(1)
  lq.enqueue(2)
  lq.printQueue()
  print(lq.dequeue())
  print(lq.dequeue())
  lq.printQueue()
```
##
#### [구현] python Queue 모듈 사용

| class                        | content      |
|------------------------------|--------------|
| queue.Queue(maxsize)         | 큐 객체 생성   |
| queue.LifoQueue(maxsize)     | 스택 객체 생성 |
| queue.PriorityQueue(maxsize) | 우선순위 큐 객체 생성 입력되는 아이템의 형식은 (순위, 아아템)의 튜플로 입력되며, 우선 순위는 숫자가 작을수록 높은 순위를 갖는다. |

##### ADT
>queue.Queue().put(data) - 삽입 (Rear에 데이터 입력)   
queue.Queue().get() - 삭제 (Front에 있는 데이터 추출)   
```python
import queue

q = queue.Queue()

q.put(1)
q.put(2)
q.put(3)
print(q.get())
print(q.get())
print(q.get())
```

##
#### [구현] python Linked list 사용

##### ADT
> class Node - 데이터를 저장 할 노드 클래스 (데이터와 가리킬 노드 저장 공간 초기화)   
class SinglyLinkedList - 링크드 리스트를 이용한 큐   
SinglyLinkedList.enqueue - 데이터 입력 (제일 뒤에, Rear)   
SinglyLinkedList.dequeue - 데이터 삭제 (제일 앞에서, Front)
```python
class Node(list):
  def __init__(self, data):
    self.data = data
    self.next = None

class SinglyLinkedList(list):
  def __init__(self):
    self.head = None
    self.tail = None

  def enqueue(self, data):
    newNode = Node(data)

    if self.head == None:
      self.head = newNode
      self.tail = newNode
    else:
      self.tail.next = newNode
      self.tail = self.tail.next

  def dequeue(self):
    if self.head == None:
      return -1

    v = self.head.data
    self.head = self.head.next

    if self.head == None:
      self.tail = None

    return v

  def printQue(self):
    curn = self.head
    string = ""
    while curn:
      string += str(curn.data)
      if curn.next:
        string += "->"
      curn = curn.next
    print(string)

if __name__=="__main__":
  slq = SinglyLinkedList()

  s.enqueue(1)
  s.enqueue(2)
  s.enqueue(3)
  s.printQue()

  print(s.dequeue())
  print(s.dequeue())
  print(s.dequeue())
```
