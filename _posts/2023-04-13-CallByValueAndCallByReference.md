---
layout: single
title:  "이론 공부 - Call By Value & Call By Reference"
categories: Theory Study
tag: [Study, Theory]
toc: true
---

> ## 값에 의한 호출 (Call By Value)

* 함수가 호출될 때 메모리 공간 안에서는 __임시의 공간__ 이 생성된다. 그리고 함수가 종료되면 해당 공간은 사라진다.
* 함수 호출시 전달되는 변수의 값을 __복사__ 하여 함수의 인자로 전달한다.
* 복사된 인자는 함수 안에서 __지역적으로 사용하는 변수__ 이다.
* 원본값을 바꿀 필요가 없는 경우 사용한다.

```cpp
#include <stdio.h>

void swap(int a, int b)
{
   int temp;

   temp = a;
   a = b;
   b = temp;
}

int main()
{
   int a, b;
   a = 10;
   b = 20;
   printf("Swap 전 : %d %d\n", a, b);
   swap(a,b);
   printf("Swap 후 : %d %d\n", a, b);

   return 0;
}
```
> 위의 C++ 로 구현된 코드는 Swap을 진행해도 변수 a, b의 값은 변하지 않는다.

> ## 참조에 의한 호출 (Call By Reference)

* 함수가 호출될 때, 메모리 공간 안에서는 함수를 위한 __별도의 임시 공간__ 이 생성된다.
* __Call By Reference__ 는 함수 호출시 인자로 전달되는 변수의 주소값를 전달한다.
* 함수 안에서 인자의 값이 변경되면, 함수 호출시 전달된 변수들의 값이 변한다.

```cpp
#include <stdio.h>

void swap(int *a, int *b)
{
	int temp;

	temp = *a;
	*a = *b;
	*b = temp;
}

int main()
{
	int a, b;
	a = 10;
	b = 20;
	printf("swap 전 : %d %d\n", a, b);
	swap(&a, &b);
	printf("swap 후 : %d %d\n", a, b);
	return 0;
}
```
> 위의 C++ 로 구현된 코드는 Swap을 진행하면 변수 a, b의 값이 변했다.

> ### Call By Value VS Call By Reference
  * Call By Value : 값을 직접 넘기기 때문에 원본 유지 가능, 추가 메모리 사용
  * Call By Reference : 값이 아닌 주소값을 넘기기 때문에 원본 변경 가능성있다, 추가 메모리를 사용하지 않는다.