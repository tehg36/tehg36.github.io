---
layout: single
title:  "이론 공부 - 스레드(Thread) 와 코루틴(Coroutine) 차이"
categories: Theory Study
tag: [Study, Theory, Thread, Coroutine]
toc: true
---

> ## 동시성 vs 병렬성

* 동시성 (Concurrency)

동시성 프로그래밍은 말 그대로 `동시에 여러 작업` 을 수행하는 것이다. 하지만 눈으로 보기에 동시에 실행 되는 것이지, 사실 `시분할(Interleaving) 기법을 활용` 하여 여러 작업을 `조금씩 나누어서 번갈아가며 실행` 하는 것이다.

![Concurrency](/images/2023-04-11-ThreadVSCoroutine_posting/Concurrentcy.png){: align-center}

위 예제를 살펴보면, Task 1 과 Task 2를 `잘개 쪼개어 번갈아가며 수행` 하여 사용자 입장에선 두 작업이 `동시에 일어나는 것처럼 느껴지게` 된다.

* 병렬성 (Parallelism)

병렬성 프로그래밍은 시분할 기법없이 `여러 작업을 한 번에 동시에 수행`하는 것이다. 자원(CPU 코어)의 입장에서 할 일을 1개 하는 것 뿐이다. 즉, 병렬성은 자원(CPU 코어)이 여러개 일 때 가능하다.

![Parallelism](/images/2023-04-11-ThreadVSCoroutine_posting/Parallelism.png){: align-center}

위 예제를 보면, Task 1 과 Task 2 가 `병렬적으로 동시에 수행` 된다. 이는 멀티코어 시스템에서 가능하다. 코어 각각이 Task 1, Task 2 를 맡아 작업을 수행하면 동시에 수해잉 되는것이다.<br/><br/>

`스레드(Thread)` 와 `코루틴(Coroutine)` 은 모두 `동시성 프로그래밍` 을 위한 기술이다.

> ## 스레드(Thread) vs 코루틴(Coroutine)

`스레드(Thread)` 는 `각 테스크에 해당하는 스택 메모리를 할당` 받는다. 그리고 `여러 작업을 동시에 수행` 해야할 때 OS 는 어떤 스레드 작업을 먼저 수행할지, 어떤 스레드를 더 많이 수행해야 효율적인지에 대한 `스케줄링(선점 스케줄링, Preempting Scheduling)` 을 해야한다.<br/><br/>

`코루틴(Coroutine)` 은 `Lightweight Thread` 라고도 부른다. 마찬가지로 `작업 하나하나를 효율적으로 분배해서 동시성을 보장하는 것` 을 목표로 하지만, 작업 하나하나에 Thread 를 할당하는 것이 아닌 Object 를 할당해주고, `Object 를 자유롭게 스위칭함으로써 Context Switching 비용을 대폭 줄인 것` 이다.

* 스레드 (Thread)
  * 작업 하나 단위 : Thread
    * 각 Thread 가 독립적인 Stack 메모리 영역 가진다.
  * 동시성 보장 수단 : Context Switching
    * OS 커널에 의한 Context Switching 을 통해 동시성 보장
    * 블로킹 (Blocking) : Thread A 가 Thread B 의 결과가 나오기까지 기다려야 한다면, Thread A 는 블로킹되어 Thread B 의 결과가 나올 때 까지 해당 자원을 못쓴다.

![Thread](/images/2023-04-11-ThreadVSCoroutine_posting/Thread.png){: align-center}

Thread A 에서 Task 1 을 수행하다가 Task 2 의 결과가 필요할 때, 비동기적으로 Thread B 를 호출하게 된다. 이 때 Thread A 는 블로킹되고, Thread B 로 Context Switching 이 일어나 Task 2 를 수행한다. Task 2 가 완료되면, 다시 Thread A 로 Context Switching 이 일어나 결과값을 Task 1 에 반환한다.<br/><br/>

동시에 같이 수행할 Task 3, Task 4 는 각각 Thread C 와 D 에 할당되고, 총체적으로 봤을 때 커널 입장에서 Preempting Scheduling 을 통하여 각 테스크를 얼만큼 수행할지, 혹은 무엇을 먼저 수행할지를 결정하여 동시성을 보장한다.

* 코루틴 (Coroutine)
  * 작업 하나 단위 : Coroutine Object
    * 여러 작업 각각의 Object 할당
  * 동시성 보장 수단 : Programmer Switching (No-Context Switching)
    * 프로그래머의 코드를 통해 Switching 시점을 정한다.(OS 관여 X)
    * Suspend (Non-Blocking) : Object 1 이 Object 2 의 결과가 나오기까지 기다려야 한다면, Object 1 은 Suspend 되지만, Object 1 을 수행하던 Thread 는 그대로 유효하기 때문에 Object2 도 Object 1 과 동일한 Thread 에서 실행 가능하다.

![Coroutine](/images/2023-04-11-ThreadVSCoroutine_posting/Coroutine.png) {: align-center}

작업 단위는 Coroutine Object 이므로, Task 1 을 수행하다가 비동기 작업 Task 2 가 발생하더라도, Context Switching 없이 같은 Thread 에서 Task 2 를 수행할 수 있고, 맨 오른쪽 경우처럼 하나의 Thread 에서 여러 Coroutine Object 들을 같이 수행할 수도 있다. 한 쓰레드에서 다수의 Coroutine 을 수행할 수 있고, Context Switching 이 필요없는 특성에 따라 Coroutine 을 Light-weight Thread 라고 부르는 것이다.<br/><br/>

그런데 위 경우를 다시 보자. Thread A 와 C 가 동시에 수행되는 모습이다. 이러면 결국 동시성 보장을 위해서 Context Switching 이 필요한 경우다. 따라서, Coroutine 의 'No-Context Switching' 장점을 극강으로 끌어올리기 위해, 단일 `Thread 에서 여러 Coroutine Object 를 컨트롤하는 것`이 좋다.

> ## Unity 에서 스레드 (Thread) & 코루틴 (Coroutine)

* 스레드 (Thread)

```csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading;
using UnityEngine;

public class TheadTest : MonoBehaviour
{
	private void Start()
	{
		Thread thread1 = new Thread(() => DelayedHelloWorld(2f));
		Thread thread2 = new Thread(() => DelayedHelloWorld(1f));
		Thread thread3 = new Thread(() => DelayedHelloWorld(3f));

		thread1.Start();
		thread2.Start();
		thread3.Start();
	}

	private void DelayedHelloWorld(float seconds)
	{
		Thread.Sleep((int)(1000 * seconds));
		Debug.Log("Hello World!");
	}
}
```

* 코루틴 (Coroutine)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CoroutineTest : MonoBehaviour
{
	private void Start()
	{
		StartCoroutine(DelayedHelloWorld(2f));      // 2초 뒤에 출력
		StartCoroutine(DelayedHelloWorld(1f));      // 1초 뒤에 출력
		StartCoroutine(DelayedHelloWorld(3f));      // 3초 뒤에 출력
	}

	private IEnumerator DelayedHelloWorld(float seconds)
	{
		yield return new WaitForSeconds(seconds);
		Debug.Log("Hello World!");
    }
}
```

* 차이점

결과는 같은 결과를 출력하지만, 코루틴은 하나의 스레드에서 스케줄링으로 관리된다. 반면 멀티 스레드로 구성했을 경우, 예외 상황이 생기며 (주로 데드락), 각 프로세스 마다 우선권을 주기 위해 관리되는 기법이 있다. (Join(), 뮤택스, 셰마포어 등)

* 정리

코루틴은 단일 스레드로 매 프레임마다 코루틴 체크한다.

![UnityCoroutine](/images/2023-04-11-ThreadVSCoroutine_posting/UnityCoroutine.png) {: align-center}

반면 스레드는 아래와 같이 각각 프로세스가 돌아가면서 처리된다.

![UnityThread](/images/2023-04-11-ThreadVSCoroutine_posting/UnityThread.png){: align-center}

`스레드`는 순서가 보장되지않아서 의도하지 않은 상황 발생 가능하다.<br/>
`코루틴`은 프로그래머의 목적과 의도대로 효율성을 올릴 수 있는 동시성 보장 기법이다.