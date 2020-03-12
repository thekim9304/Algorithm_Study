# TREE

<p align="center">
  <img src="img/treeimg.jpg" width=50%>
</o>

- root / 부모 노드(parent node) / 자식 노드(child node) / 형제 노드(sibling node) / leaf
- 레벨(level) / 높이(height)
- 차수(degree)
  :: 서브 트리(또는 자식 노드)의 개수
  :: 모든 노드의 차수가 2 이하면 이진 트리(binary tree)
- 순회(traverse) 알고리즘
  1. **깊이 우선 순회(Depth First Traversal), DFS**
    전위 순회(pre-order traverse), 중위 순회(in-order traverse), 후위 순회(post-order traverse)
      - 전위 : Root > 왼 > 오
        ```
        A -> B -> D -> G -> H -> E -> C -> F -> I
        ```
        ![](http://ceadserv1.nku.edu/longa//classes/mat385_resources/docs/traversal_files/PreOrderTrav.gif)
      - 중위 : 왼 > Root > 오
        ```
        G -> D -> H -> B -> E -> A -> C -> I -> F
        ```
        ![](http://ceadserv1.nku.edu/longa//classes/mat385_resources/docs/traversal_files/InorderTrav.gif)
      - 후위 : 왼 > 오 > Root
        ```
        G -> H -> D -> E -> B -> I -> F -> C -> A
        ```
        ![](http://ceadserv1.nku.edu/longa//classes/mat385_resources/docs/traversal_files/PostorderTrav.gif)

  ###
  2. **너비 우선 순회(Breadth First Traversal), BFS**
    레벨 순회(level-order traversal)

  ***Code***
  - 구현은 밑에 Binary Search Tree랑 같이  

## Binary Tree
- 최대 두 개의 자식 노드를 가지는 트리 형태의 자료구조
- 단순히 값을 저장하는 용도보다는 효율적인 탐색 or 정렬을 위하여 사용함
- 재귀 함수 사용

#### Binary Search Tree
  - 이진 트리의 특수 케이스 중 하나
  - 모든 노드에 대해 왼쪽 자식 노들의 값이 현재 노드 값보다 적거나 같으며, 오른쪽 자식 노드들의 값이 현재 노드의 값보다 크다는 조건을 만족하면 이진 탐색 트리
  ######

  - 이진 탐색 트리 구축 과정
    ![](https://t1.daumcdn.net/cfile/tistory/99AD154D5C5C50D932)
  ######

  - 이진 탐색 트리 탐색 과정
    ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99631E4B5C5C511D38)

  ***Code***
  ```python
  class Node(object):
    def __init__(self, data):
      self.data = data
      self.left = self.right = None

  class BinarySearchTree(object):
    def __init__(self):
      self.root = None

    def insert(self, data):
      self.root = self._insert_value(self.root, data)
      return self.root is not None

    # 새로 추가할 원소의 값을 현재 노드의 값과 비교하여
    # 왼쪽/오른쪽 중 알맞은 위치로 노드를 옮겨가면서 삽입 위치를 확인
    def _insert_value(self, node, data):
      if node is None:
        node = Node(data)
      else:
        if data <= node.data:
          node.left = self._insert_value(node.left, data)
        else:
          node.right = self._insert_value(node.right, data)
      return node

    def find(self, key):
      return self._find_value(self.root, key)

    def _find_value(self, root, key):
      if root is None or root.data == key:
        return root is not None
      elif key < root.data:
        return self._find_value(root.left, key)
      else:
        return self._find_value(root.right, key)

    def delete(self, key):
      self.root, deleted = self._delete_value(self.root, key)
      return deleted

    # 삭제할 Node의 자식이 없으면 그냥 삭제
    # 자식이 하나면 자식 노드를 삭제한 노드 위치로 가져온다
    # 자식이 둘 이면 오른쪽 서브트리에서 제일 왼쪽 아래 노드를 가져온다
    def _delete_value(self, node, key):
      if node is None:
        return node, False

      deleted = False
      if key == node.data:
        deleted = Tru
        if node.left and node.right:
          parent, child = node, node.right
          while child.left is not None:
            parent, child = child, child.left
          child.left = node.left
          if parent != node:
            parent.left = child.right
            child.right = node.right
          node = child
        elif key < node.data:
          node.left, deleted = self._delete_value(node.left, key)
        else:
          node.right, deleted = self._delete_value(node.right, key)
      return node, deleted

    def pre_order_traversal(self):
      def _pre_order_traversal(root):
        if root is None:
          pass
        else:
          print(root.data)
          _pre_order_traversal(root.left)
          _pre_order_traversal(root.right)
      _pre_order_traversal(self.root)

    def in_order_traversal(self):
      def _in_order_traversal(root):
        if root is None:
          pass
        else:
          _in_order_traversal(root.left)
          print(root.data)
          _in_order_traversal(root.right)
      _in_order_traversal(self.root)

    def post_order_traversal(self):
      def _post_order_traversal(root):
        if root is None:
          pass
        else:
          _post_order_traversal(root.left)
          _post_order_traversal(root.right)
          print(root.data)
      _post_order_traversal(self.root)

    def level_order_traversal(self):
      def _level_order_traversal(root):
        queue = [root]
        while queue:
          root = queue.pop(0)
          if root is not None:
            print(root.data)
            if root.left:
              queue.append(root.left)
            if root.right:
              queue.append(root.right)
      _level_order_traversal(self.root)
  ```

[참고1***** + 코드](https://geonlee.tistory.com/72)
[참고2](http://ceadserv1.nku.edu/longa//classes/mat385_resources/docs/traversal.htm)
