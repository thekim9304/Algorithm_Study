# STACK
- LIFO(Last Input First Out, 선입후출)
- 데이터 저장소에서 새로 들어오는 데이터의 위치가 저장소의 끝 부분(Top 혹은 Top pointer)이고, 내보내는 데이터 역시 저장소의 Top에서 나간다.   
- 입력은 push, 출력은 pop, peek은 Top의 위치에 있는 데이터를 확인하는 것
<center><img src=https://wayhome25.github.io/assets/post-img/cs/stack.jpg width=40%></center>

### 추상 자료형(ADT : Abstact Data Type)
- 기능의 구현 부분을 나타내지 않고 순수한 기능이 무엇인지 나열한 것을 추상 자료형이라고 한다.
  > 예를 들면, 사용 설명서와 같다.
  선풍기의 사용 설명서를 본다고 가정하자. 사용 설명서에는 정지, 미풍, 약풍, 강풍, 회전, 타이머 등의 기능 설명과 사용 방법이 나와있다.
  하지만 버튼을 눌렀을 때 선풍기 내부회로에서 어떤 일이 발생하는지에 대해서는 전혀 나와있지 않다.
  추상 자료형은 선풍기의 사용 설명서와 같이 기능과 사용 방법을 정희한 것이다.

  **Ex**
  - Data
    : Power, LeftButton, RightButton
  - Operation
    : Power_On()
    : Power_Off()
    : Left_Button_Click()
    : Right_Button_Click()
  - Code (c++)
    ```c++
      typedef struct{
        int power
        int leftButton;
        int rightButton;
      } WirelessMouse

      void PowerOn();
      void PowerOff();
      void LeftButtonClick();
      void RightButtonClick();
    ```
> 앞으로 모든 개념은 맨 첨에 추상 자료형으로 정리하자   
##
#### [구현] python list 사용

##### ADT
>def is_empty() - 검사 (데이터 유무 확인)   
def push - 삽입 (맨 위에 데이터 입력)   
def pop - 삭제 (맨 위 데이터 반확하고 삭제)    
def peek - 확인 (맨 위 값 반환만 하고 삭제 안함)   

##### Code
```python
class Stack(list):
  def __init__(self):
    self.stack = []

  def push(self, data):
    self.stack.append(data)

  def pop(self):
    if self.is_empty():
      return -1
    return self.stack.pop()

  def peek(self):
    return self.stack[-1]

  def is_empty(self):
    if len(self.stack) == 0:
      return True
    return False

if __name__=="__main__":
  s = Stack()
  s.push(1)
  s.push(2)
  s.push(3)
  print(s.peek())
  print(s.pop())
  print(s.pop())
  print(s.pop())
  print(s.pop())
```
#### [구현] python node 사용 (Singly linked list)

<center><img src=https://github.com/thekim9304/Algorithm_Study/blob/master/img/SinglyLinkedList.JPG?raw=true width=40%></center>

##### ADT
>class Node - 데이터를 저장 할 노드 클래스 (데이터와 가리킬 노드 저장 공간 초기화)   
def is_empty() - 검사 (데이터 유무 확인)   
def push - 삽입 (맨 위에 데이터 입력)   
def pop - 삭제 (맨 위 데이터 반확하고 삭제)   
def peek - 확인 (맨 위 값 반환만 하고 삭제 안함)   

##### Code
```python
class Node:
  def __init__(self, data):
    self.data = data
    self.next = None

class Stack:
  def __init__(self):
    self.head = None

  def push(self, data):
    new_node = Node(data)
    new_node.next = self.head
    self.head = new_node

  def pop(self):
    if self.is_empty():
      return -1
    data = self.head.data
    self.head = self.head.next
    return data

  def is_empty(self):
    if self.head:
      return False
    return True

  def peek(self):
    if self.is_empty():
      return -1
    return self.head.data
```

#
####참고
[초보몽키의 개발공부로그](https://wayhome25.github.io/cs/2017/04/18/cs-20/)
[구현 참고](https://daimhada.tistory.com/105)
