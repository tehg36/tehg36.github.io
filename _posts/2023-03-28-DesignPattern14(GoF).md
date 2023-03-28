---
layout: single
title:  "이론 공부 - 많이 쓰는 14가지 핵심 Gof 디자인 패턴 종류"
categories: Theory Study
tag: [Study, Theory, Design Pattern, GoF]
toc: true
---

`디자인 패턴`을 활용하면 코드만 `재사용`하는 것이 아니라, 더 큰 그림을 그리기 위한 디자인도 재사용할 수 있다.

`디자인 패턴`은 프로그램을 개발하는 과정에서 빈번하게 발생하는 디자인 문제를 정리해서 상황에 따라 간편하게 적용할 수 있게 정리한 것이다. 잘 활용하면 시간과 노력, 시행착오를 줄일 수 있다.

## 디자인 패턴 용도에 따라 나누기
대부분의 카탈로그에서 몇 가지 범주에 맞춰서 디자인 패턴을 분류하는데, 가장 유명한 분류 방법은 `패턴 카탈로그`에서 제시한 `생성, 행동, 구조`라는 3가지 범주로 `용도에 따라 나누기`이다.

![Pattern_Category](/images/2023-03-28-DesignPattern14(GoF)_posting/pattern_category.png){: align-center}

## 패턴을 범주 별로 왜 나눌까?
점점 더 많은 디자인 패턴이 발견됨에 따라 디자인 패턴을 찾거나 같은 그룹에 속하는 패턴끼리 비교하기 좋게, 종류에 따라 분류할 필요성이 생겼다.

## 생성 패턴 (Creational Pattern)
객체 인스턴스를 생성하는 패턴으로, 클라이언트와 그 클라이언트가 생성해야 하는 객체 인스턴스 사이의 연결을 끊어 주는 패턴

### 싱글턴 패턴 (Singleton Pattern)
`특정 클래스에 객체 인스턴스가 하나만 만들어지도록 해주는 패턴`이다. 싱글턴 패턴을 사용하면 전역 변수를 사용할 때와 마찬가지로 객체 인스턴스를 어디서든지 엑세스 할 수 있게 만들 수 있다. 클래스 인스턴스를 하나만 만들고 그 인스턴스로의 전역 접근을 제공한다.

![SingletonPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/SingletonPattern.png){: align-center}

### 추상 팩토리 패턴 (Abstract Factory Pattern)
구상 클래스에 의존하지 않고도 서로 연관되거나 의존적인 객체로 이루어진 제품군을 생산하는 인터페이스 제공합니다.

![AbstractFactoryPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/AbstractFactoryPattern.png){: align-center}

### 팩토리 메소드 패턴 (Factory Method Pattern)
객체를 생성할 때 필요한 인터페이스를 만든다. 어떤 클래스의 인스턴스를 만들지는 서브클래스에서 결정한다. 팩토리 메소드 패턴을 사용하면 클래스 인스턴스를 만드는 일을 서브클래스에게 맡기게 된다.

![FactoryMethodPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/FactoryMethodPattern.png){: align-center}

## 행동 패턴 (Behavioral Pattern)
클래스와 객체들이 상호작용하는 방법과 역할을 분담하는 방법을 다루는 패턴이다.

### 템플릿 메소드 패턴 (Template Method Pattern)
알고리즘의 골격을 정의한다. 템플릿 메소드를 사용하면 알고리즘 일부 단계를 서브클래스에서 구현할 수 있고, 알고리즘의 구조는 그대로 유지하면서 알고리즘의 특정 단계를 서브클래스에서 재정의 할 수 있다.

![TemplateMethodPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/TemplateMethodPattern.png){: align-center}

### 상태 패턴 (State Pattern)
상태 패턴을 사용하면 객체의 내부 상태가 바뀜에 따라 객체의 행동을 바꿀 수 있다. 마치 객체의 클래스가 바뀌는 것과 같은 결과를 얻을 수 있다.

![StatePattern](/images/2023-03-28-DesignPattern14(GoF)_posting/StatePattern.png){: align-center}

### 반복자 패턴 (Iterator Pattern)
컬렉션의 구현 방법을 노출하지 않으면서 집합체 내의 모든 항목에 접근하는 방법을 제공한다.

![IteratorPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/IteratorPattern.png){: align-center}

### 전략 패턴 (Strategy Pattern)
알고리즘군을 정의하고 캡슐화해서 각각의 알고리즘군을 수정해서 쓸 수 있게한다. 전략패턴을 사용하면 클라이언트로부터 알고리즘을 분리해서 독립적으로 변경할 수 있다.

### 옵저버 패턴 (Observer Pattern)
한 객체의 상태가 바뀌면 그 객체에 의존하는 다른 객체에게 연락이 가고 자동으로 내용이 갱신되는 방식으로 일대다 의존성을 정의한다.

![ObserverPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/ObserverPattern.png){: align-center}

## 구조 패턴 (Structural Pattern)
클래스와 객체를 더 큰 구조로 만들 수 있게 구상을 사용하는 패턴이다.

### 데코레이터 패턴 (Decorator Pattern)
데코레이터 패턴으로 객체에 추가 요소를 동적으로 더할 수 있다. 데코레이터를 사용하면 서브클래스를 만들 때보다 훨씬 유연하게 기능을 확장할 수 있다.

![DecoratorPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/DecoratorPattern.png){: align-center}

### 프록시 패턴 (Proxy Pattern)
특정 객체로의 접근을 제어하는 대리인(특정 객체를 대변하는 객체)을 제공한다.

![ProxyPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/ProxyPattern.png){: align-center}

### 컴포지트 패턴 (Composite Pattern)
컴포지트 패턴으로 객체를 트리구조로 구성해서 부분-전체 계층구조를 구현한다. 컴포지트 패턴을 사용하면 클라이언트에서 개별 객체와 복합 객체를 똑같은 방법으로 다룰 수 있다.

![CompositePattern](/images/2023-03-28-DesignPattern14(GoF)_posting/CompositePattern.png){: align-center}

### 어댑터 패턴 (Adapter Pattern)
특정 클래스 인터페이스를 클라이언트에서 요구하는 다른 인터페이스로 변환한다. 인터페이스가 호환되지 않아 같이 쓸 수 없었던 클래스를 사용활 수 있게 도와준다

![AdapterPattern](/images/2023-03-28-DesignPattern14(GoF)_posting/AdapterPattern.png){: align-center}

### 퍼사드 패턴 (Facade Pattern)
서브시스템에 있는 일련의 인터페이스를 통합 인터페이스로 묶어준다. 또한 고수준 인터페이스도 정의하므로 서브시스템을 더 편리하게 사용할 수 있다.

![FacadePattern](/images/2023-03-28-DesignPattern14(GoF)_posting/FacadePattern.png){: align-center}

<br/><br/>
> 내용 출처 : 한빛출판네트워크 <https://www.hanbit.co.kr/channel/category/category_view.html?cms_code=CMS8616098823>