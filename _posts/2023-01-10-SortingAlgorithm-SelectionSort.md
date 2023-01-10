---
layout: single
title:  "알고리즘이론 - 선택정렬 (Selection Sort)"
categories: Algorithm
tag: [Blog, Study, Algorithm, Python, Sort]
toc: true
---

## 1. 선택 정렬 (Selection Sort)
* 아래 순서를 반복하여 정렬하는 알고리즘
    1. 주어진 데이터 중, 최소값을 찾는다
    2. 해당 최소값을 맨 앞에 위치한 값과 교체한다
    3. 맨 앞의 위치를 뺀 나머지 데이터를 동일한 방법으로 반복한다

![SelectionSort](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif){: .align-center}

> 출처 : <https://en.wikipedia.org/wiki/Selection_sort>

> 실행해볼수 있는 사이트 : <https://visualgo.net/en/sorting>

* 데이터가 4개일 때, 선택 정렬 간단 정리

![SelectionSortSimply](/images/2023-01-10-SortingAlgorithm-SelectionSort_posting/SelectionSort_Simply.png){: align-center}

## 2. 코드 구현

* 함수 구현

```python
def SelectionSort(data):
    for stand in range(len(data) - 1):
        lowest = stand
        for index in range(stand + 1, len(data)):
            if data[lowest] > data[index]:
                lowest = index
        data[lowest], data[stand] = data[stand], data[lowest]
    return data
```

* 실행 구현

```python
import random

dataList = random.sample(range(100), 10)

SelectionSort(dataList)
```

## 3. 알고리즘 분석

* 시간 복잡도 : 반복문이 두개
$O(n^2)$
  * 상세하게 계산하면 , 
  <font size=5em>
  $\frac{ n * (n - 1)}{ 2 }$
  </font>
$O(n)$