---
layout: single
title:  "알고리즘 자료구조 - Tree (노드탐색 - 구현)"
---

<link rel="icon" type="image/png" href="favicon.png" />
<link rel="stylesheet" href="https://pyscript.net/latest/pyscript.css" />
<script defer src="https://pyscript.net/latest/pyscript.js"></script>

* ## Linked List 로 Tree 구현

> Node Class

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```

> Binary Search Tree

```python
class NodeManagement:
    def __init__(self, head):
        self.head = head

    def insert(self, value):
        self.current_node = self.head
        while True:
            # 비교값이 현재 노드의 값보다 작은지 비교 (트리 왼쪽)
            if value < self.current_node.value:
                if self.current_node.left != None:
                    self.current_node = self.current_node.left
                else
                    self.current_node.left = Node(value)
                    break
            # 비교값이 현재 노드의 값보다 큰지 비교 (트리 오른쪽)                    
            else:
                if self.current_node != None:
                    self.current_node = self.current_node.right
                else:
                    self.current_node.right = Node(value)
                    break
    
    def search(self, value):
        self.current_node = self.head
        while self.current_node:
            # 찾고자 하는 값이 현재 노드의 값과 같다면
            if self.current_node.value == value:
                return True
            # 찾고자 하는 값이 현재 노드의 값보다 작다면 왼쪽으로 이동
            elif value < self.current_node.value:
                self.current_node = self.current_node.left
            # 찾고자 하는 값이 현재 노드의 값보다 크다면 오른쪽으로 이동
            else:
                self.current_node = self.current_node.right
        return False
```

> 코드 실행 구문

``` python
Node(1)
BST = NodeManagement(Node) # 생성한 노드를 Head로 지정

# 트리에 값 넣어보기
BST.insert(3)
BST.insert(0)
BST.insert(8)
BST.insert(2)

# 트리에 값이 잘 들어갔는지 확인
BST.search(3) # True 반환
BST.search(-1) # False 반환
```

<body>
    <h2><b>코드 직접 실행해보기</b></h2>
    Tip: Shift-ENTER를 누르면 코드가 실행됩니다
    <br>
    <div>
      <py-repl id="my-repl" auto-generate="true"> </py-repl>
    </div>
</body>