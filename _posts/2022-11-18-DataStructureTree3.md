---
layout: single
title:  "알고리즘 자료구조 - Tree (노드삭제 - 이론)"
categories: DataStructure
tag: [Study, Algorithm, DataStructure, Tree]
toc: true
---

> ## 이진탐색트리의 삭제

### 삭제에는 여러가지 경우의 수를 생각해야한다
  * __Leaf Node 삭제__
        - `Leaf Node`: Child Node 가 없는 Node
        - 삭제할 노드의 Parent Node 가 대상을 가르키지않게 한다
    
<p align="center"><img src="http://www.fun-coding.org/00_Images/tree_remove_leaf.png" width="600" /></p>

  * __Child Node 가 하나인 Node 삭제__
        - 삭제할 Node 의 Parent Node 가 삭제할 Node 의 Child Node 를 가르키도록 한다

<p align="center"><img src="http://www.fun-coding.org/00_Images/tree_remove_1child.png" width="600" /></p>

* __Child Node 가 두 개인 Node 삭제__
    - 삭제할 Node 의 오른쪽 자식 중, 가장 작은 값을 삭제할 Node 의 Parent Node 가 가리키도록 한다
    - 삭제할 Node 의 왼쪽 자식 중, 가장 큰 값을 삭제할 Node 의 Parent Node 가 가리키도록 한다.

<p align="center"><img src="http://www.fun-coding.org/00_Images/tree_remove_2child.png" width="600" /></p>

