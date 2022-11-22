---
layout: single
title:  "알고리즘 자료구조 - Tree (노드탐색 - 이론)"
categories: DataStructure
tag: [Blog, Study, Algorithm, DataStructure, Tree]
toc: true
---

> # 대표적인 데이터 구조 : 트리 (Tree)

## 1. 트리 (Tree) 구조
* 트리 : Node의 Branch를 이용해서, 사이클을 이루지 않도록 구성한 데이터 구조
* 트리 중 이진 트리 (Binary Tree) 형태의 구조로, 탐색(검색) 알고리즘 구현시 많이 사용된다

## 2. 트리 관련 용어
- __Node__: 트리에서 데이터를 저장하는 기본 요소 (데이터와 다른 연결된 노드에 대한 Branch 정보 포함한다)
- __Root Node__: 트리 최상위 노드
- __Level__: 최상위 노드를 Level 0으로 하였을 때, 하위 Branch로 연결된 노드의 깊이를 나타낸디
- __Parent Node__: 어떤 노드의 상위에 연결된 노드
- __Child Node__: 어떤 노드의 하위에 연결된 노드
- __Leaf Node__ (Terminal Node): Child Node가 하나도 없는 노드
- __Sibling__ (Brother Node): 동일한 Parent Node를 가진 노드
- __Depth__: 트리에서 Node가 가질 수 있는 최대 Level<br/><br/>

![Tree](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-11-15-DataStructureTree_posting/treeDesc.png?raw=true)

## 3. 이진 트리 (Binary Tree) 와 이진 탐색 트리 (Binary Search Tree)
- 두 개가 같아보이지만 서로 다른것이므로 알고가자
    - __이진트리(Binary Tree)__ : 노드의 최대 Branch가 2인 트리
    - __이진 탐색 트리(Binary search Tree, BST)__ : 이진 트리에 추가적인 조건이 있는 트리
        - 왼쪽 노드는 비교 노드보다 작은 값, 오른쪽 노드는 비교 노드보다 큰 값을 가지고 있다
<figure >
<img src="https://blog.penjee.com/wp-content/uploads/2015/11/binary-search-tree-insertion-animation.gif" alt="BinarySearchTree" style="display: block; margin: 0 auto" />
<figcaption>
출처: https://www.mathwarehouse.com/programming/gifs/binary-search-tree.php#binary-search-tree-insertion-node
</figcaption>
</figure>

## 4. 이진 탐색 트리 (Binary Search Tree)
- 주 용도 : 데이터 탐색
- 장점 : 빠른 탐색 속도

* ### 이진탐색트리와 정렬된 배열간의 탬색비교
<figure>
<img src="https://www.mathwarehouse.com/programming/images/binary-search-tree/binary-search-tree-sorted-array-animation.gif" style="display: block; margin: 0 auto" />
<figcaption>
출처: https://www.mathwarehouse.com/programming/gifs/binary-search-tree.php#binary-search-tree-insertion-node
</figcaption>
</figure>