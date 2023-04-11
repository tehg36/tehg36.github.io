---
layout: single
title:  "알고리즘 자료구조 - HashTable"
categories: DataStructure
tag: [Study, Algorithm, DataStructure, HashTable]
toc: true
---

> ## 해시테이블(HashTable)이란?

* 해시테이블(HashTable) 이란?

해시 테이블은 `Key, Value` 한쌍으로 데이터를 저장하는 자료구조 중 하나로 빠르게 데이터를 검색할 수 있는 자료구조이다.

해시테이블이 빠른 검색속도를 제공하는 이유는 내부적으로 배열을 사용하여 데이터를 저장하기 때문이다.

해시테이블은 각각의 Key값에 해시함수를 적용해 배열의 고유한 Index를 생성하고, 이 Index를 활용해 값을 저장하거나 검색하게 된다.
여기서 실제 값이 저장되는 장소를 `버킷` 또는 `슬롯`이라고 한다

![HashTable](/images/2023-04-11-DataStructureHashTable_posting/HashTable.png){: align-center}

예를 들어 우리가 `Key, Vakue`가 `"John Smith", "521-1234"` 인 데이터를 크기가 16인 해시 테이블에 저장한다고 하자.
그러면 먼저 index = hash_function("John Smith") % 16 연산을 통해 index 값을 계산한다. 그리고 array[index] = "521-1234"로 전화번호를 저장하게 된다.<br/>
이러한 해싱구조로 데이터를 저장하면 Key값으로 데이터를 찾을 때 해시함수를 1번만 수행하면 되므로 매우 빠르게 데이터를 저장/삭제/조회 할 수 있다. `해시테이블의 평균 시간복잡도는 O(1)`이다.

> ## 해시(Hash) 값이 충돌하는 경우

* 해시(Hash) 값이 충돌하는 경우

만약 "John Smith"를 해시함수를 돌려 나온 값과 "Mang Kyu"를 해시함수를 돌려 나온 값이 동일하다면 어떻게 해야할까?<br/>
해시테이블에서는 충돌에 의한 문제를 `분리연결법(Separate Chaining) 과 개방 주소법(Open Addressing)` 크게 2가지로 해결하고 있다.

* 분리연결법(Separate Chaining)

![Separate Chaining](/images/2023-04-11-DataStructureHashTable_posting/SeparateChaining.png){: align-center}

`Separate Chaining` 이란 동일한 버킷의 데이터에 대해 자료구조를 활용해 추가 메모리를 사용하여 다음 데이터의 주소를 저장하는 것이다. 위의 그림과 같이 동일한 버킷으로 접근을 한다면 데이터들을 연결을 해서 관리해주고 있다.<br/>

이러한 Chaining 방식은 해시테이블의 확장이 필요없고 간단하게 구현이 가능하며, 손쉽게 삭제할 수 있다는 장점이 있다. 하지만 데이터의 수가 많아지면 동일한 버킷에 Chaining 되는 데이터가 많아지며 그에 따라 캐시의 효율성이 감소한다는 단점이있다.

* 개방주소법(Open Addressing)

`Open Addressing` 이란 추가적인 메모리를 사용하는 Chaining 방식과 다르게 비어있는 해시테이블의 공간을 활용하는 방법이다. Open Addressing을 구현하기 위한 대표적인 방법으로는 3가지 방식이 존재한다.

1. `선형탐사(Linear Probing)` : 현재의 버킷 index로부터 고정폭 만큼씩 이동하여 차례대로 검색해 비어있는 버킷에 데이터를 저장한다. 인접한 index에 데이터를 삽입해가기 때문에 클러스터링 문제 발생하고, 탐색과 삭제가 느려지게된다.
2. `제곱탐사(Quadratic Probing)` : 해시의 저장순서 폭을 제곱으로 저장하는 방식이다. 예를 들어 처음 충돌이 발생한 경우에는 1만큼 이동하고 그 다음 계속 충돌이 발생하면 2^2, 3^2 칸씩 옮기는 방식이다. 초기 해시값이 같을 경우, 클러스터링 문제 발생한다.
3. `Double Hasing Probing` : 해시된 값을 한번 더 해싱하여 해시의 규칙성을 없애버리는 방식이다. 해시된 값을 한번 더 해싱하여 새로운 주소를 할당하기 때문에 다른 방법들보다 많은 연산을 하게 된다.

![LinearProbingAndQuadraticProbing](/images/2023-04-11-DataStructureHashTable_posting/LinearProbingAndQuadraticProbing.png){: align-center}

Open Addressing 에서 데이터를 삭제하면 삭제된 공간은 Dummy Space로 활용되는데, 그렇기 때문에 `Hash Table을 재정리 해주는 작업` 이 필요하다.

* 해시함수(Hash Function) 개선

해시함수에서 중요한 것은 고유한 인덱스 값을 설정하는 것이다. 해시테이블에 사용되는 대표적인 해시함수로는 아래 3가지가 있다.

1. `Division Method` : 나눗셈을 이용하는 방법으로 입력값을 테이블의 크기로 나누어 계산한다. (주소 = 입력값 % 테이블의 크기) 테이블의 크기를 소수로 정하고 2의 제곱수와 먼 값을 사용해야 효과가 좋다
2. `Digit Folding` : 각 Key의 문자열을 ASCII 코드로 바꾸고 값을 합한 데이터를 테이블 내의 주소로 사용하는 방법이다.
3. `Multiplication Method` : 숫자로 된 Key값 K와 0과 1사이의 실수 A, 보통 2의 제곱수인 m을 사용하여 다음과 같은 계산을 해준다. h(k) = (kAmod1) * m
4. `Univeral Hasing` : 다수의 해시함수를 만들어 집합 H 에 넣어두고, 무작위로 해시함수를 선택해 해시값을 만드는 기법이다.

> ## 해시테이블(HashTable) 시간복잡도

* 해시테이블 (HashTable) 시간복잡도

각각의 Key값은 해시함수에 의해 고유한 index를 가지게 되어 바로 접근할 수 있으므로 `평균 O(1)의 시간복잡도` 로 데이터를 조회할 수 있다. 하지만 `데이터의 충돌이 발생한 경우 Chaining에 연결된 리스트들까지 검색을 해야하므로 O(N)까지 시간복잡도가 증가` 할 수 있다.<br/>

충돌을 방지하는 방법들은 데이터의 규칙성(클러스터링)을 방지하기 위한 방식이지만 공간을 많이 사용한다는 치명적인 단점이 있다.<br/>

만약 테이블이 꽉 차있는 경우라면 테이블을 확장해주어야 하는데, 이는 매우 심각한 성능의 저하를 불러오기 때문에 가급적이면 확장을 하지 않도록 테이블을 설계해주어야 한다.<br/>
(통계적으로 해시테이블의 공간 사용률이 70~80% 정도가 되면 해시의 충돌이 빈번하게 발생하여 성능이 저하되기 시작한다고 한다.)<br/>

또한 해시 테이블에서 자주 사용하게 되는 데이터를 Cache 에 적용하면 효율을 높일 수 있다.

> ## 해시테이블(HashTable) 구현

* C++ 로 구현한 해시테이블

충돌처리로는 체이닝 방식을 사용하고, 해시함수로는 모듈러 연산을 사용

```cpp
#include <iostream>
#incldue <list>
using namespace std;

class HashTable {
    private:
        static const int hashSize = 10; // 해시 테이블 크기
        list<pair<int, int>> table[hashSize]; // 해시 테이블

    public:
        void insert(int key, int value) {
            int index = hashFunction(key);
            table[index].push_back(make_pair(key, value));
        }

        int search(int key) {
            int index = hashFunction(key);
            for (auto& elem : table[index]) {
                if (elem.first == key) {
                    return elem.second;
                }
            }
            return -1; // 찾는 값이 없는경우 -1 반환
        }

        void remove(int key) {
            int index = hashFunction(key);
            for (auto it = table[index].begin(); it != table[index].end(); it++) {
                if (it->first == key) {
                    table[index].erase(it);
                    return;
                }
            }
        }
    private:
        int hashFunction(int key) {
            return key % hashSize;
        }
}

int main() {
    HashTable ht;
    ht.insert(1, 10);
    ht.insert(2, 20);
    ht.insert(3, 30);
    cout << hit.search(1) << endl; // 10 출력
    cout << hit.search(4) << endl; // -1 출력
    ht.remove(2);
    cout << hit.search(2) << endl; // -1 출력

    return 0;
}
```