---
layout: single
title:  "알고리즘이론 - 삽입정렬 (Insertion Sort)"
categories: Algorithm
tag: [Blog, Study, Algorithm, Python, Sort]
toc: true
---

## 1. 삽입 정렬 (Insertion Sort)
* k번째 원소를 1부터 k-1까지와 비교해 적절한 위치에 끼워넣고 그 뒤의 자료를 한 칸씩 뒤로 밀어내는 방식

![InsertionSort](https://upload.wikimedia.org/wikipedia/commons/9/9c/Insertion-sort-example.gif){: .align-center}
> 출처 : <https://commons.wikimedia.org/wiki/File:Insertion-sort-example.gif>

> 실행해볼수 있는 사이트 : <https://visualgo.net/en/sorting>

* 데이터가 4개일때, 삽입 정렬 간단 정리

![Insertion Sort](/images/2023-01-02-SortingAlgorithm-InsertionSort_posting/InsertionSort_Simply.png){: .align-center}

## 2. 코드로 구현하기

* 함수 구현
  
```python
def InsertionSort(data):
    for index1 in range(len(data) - 1):
        for index2 in range(index + 1, 0, -1):
            if data[index2] < data[index2 - 1]:
                data[index2], data[index2 - 1] = data[index2 - 1], data[index2]
            else:
                break
```

* 실행 구현

```python
import random

data_list = random.sample(range(100), 50)

print(InsertionSort(data_list))
```

## 3. 알고리즘 분석

* 시간 복잡도 : O($n^2$) - 반복문이 두개
  * 최악의 경우, <font size=5em>$\frac { n * (n - 1)}{ 2 }$</font>
* 완전 정렬이 되어있는 상태라면 최선은 O(n)