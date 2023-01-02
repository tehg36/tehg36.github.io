---
layout: single
title:  "알고리즘이론 - 버블정렬 (Bubble Sort)"
categories: Algorithm
tag: [Blog, Study, Algorithm, Python, Sort]
toc: true
---

## 1. 버블 정렬 (Bubble Sort)

* 두 인접한 데이터를 비교해서, 앞에 있는 데이터가 뒤에 있는 데이터보다 크면, 자리를 바꾸는 정렬 알고리즘

![BubbleSort](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif){: width="60%" height="50%"}{: .align-center}
> 출처 : <https://en.wikipedia.org/wiki/Bubble_sort>

> 실행해볼수 있는 사이트 : <https://visualgo.net/en/sorting>

* 데이터가 4개일때, 버블 정렬 간단 정리

![SimpleBubbleSort](/images/2023-01-02-SortingAlgorithm-BubbleSort_posting/BubbleSort_Simply.png){: .align-center}

## 2. 코드로 구현하기

* 함수 구현
```python
def BubbleSort(data):
    for index1 in range(len(data) - 1):
        swap = False
        for index2 in range(len(data) - index1 - 1):
            if data[index2] > data[index2 + 1]:
                data[index2], data[index2 + 1] = data[index2 + 1], data[index2]
                swap = True
        
        if swap == False: # 데이터 교체가 한번도 일어나지 않았다면 (정렬되어있다)
            break
    return data
```
* 실행 구현
```python
import random

data_list = random.sample(range(100), 50)

print(BubbleSort(data_list))
```

## 3. 알고리즘 분석

* 시간 복잡도 : O($n^2$) - 반복문이 두개
  * 최악의 경우, <font size=5em>$\frac { n * (n - 1)}{ 2 }$</font>
* 완전 정렬이 되어있는 상태라면 최선은 O(n)