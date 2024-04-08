# JAVA & Spring
## Index
### JAVA
1. [Call By Reference](#1-call-by-reference)
2. [Override & Overload](#2-override--overload)
3. [JVM](#3-jvm)
4. [Java의 컴파일 과정](#4-java의-컴파일과정)
5. [JVM의 스택과 힙 메모리 영역](#5-jvm의-스택과-힙-메모리-영역)
6. [클래스와 인스턴스](#6-클래스와-인스턴스)
7. [Garbage Collector](#7-garbage-collector)
8. [Java Map의 내부구현](#8-java-map의-내부구현)
9. [IoC와 DI](#9-ioc와-di)
10. [N+1과 해결방법](#10-n1과-해결방법)
11. [즉시로딩&지연로딩](#11-즉시로딩지연로딩)
12. [Generic](#12-generic)
13. [HashTable, HashMap, HashSet](#13-hashtable-hashmap-hashset)
14. [추상클래스와 인터페이스](#14-추상클래스와-인터페이스)
15. [Java의 버전별 차이](#15-java의-버전별-차이)
16. [Java 직렬화](#16-java-직렬화)
17. [Thread Pool](#17-thread-pool)
18. [Concurrent Collection](#18-concurrent-collection)

-- -- --
## JAVA
### 1. [Call by Reference](https://skroy0513.tistory.com/18)
<details>
  <summary>❓ <b><i> Call by Reference에 대해 간략히 설명해주세요</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;Call by Reference는 참조에 의한 호출로, 메소드에 변수를 전달할 때 변수의 참조값인 메모리 주소 값이 전달되며, 메소드 내에서 변수를 수정하면 호출자의 변수도 수정됩니다. Call by Reference는 복사하지 않고 직접 참조를 하기 때문에 상당히 빠른 장점이 있지만, 직접 참조를 하기 때문에 원래의 값이 영향을 받는 리스크가 존재한다. <br>
    &nbsp;&nbsp;자바는 객체 지향 프로그래밍이기 때문에 Call by Value를 지향하며 그 방식으로 동작합니다. Call by Value는 값에 의한 호출로, 함수가 인수로 전달받은 값을 복사하여 처리 하기 때문에 원본 값은 변경되지 않는 특징이 있습니다. 하지만 Java의 참조타입인 경우 Heap영역에 객체가 들어있고 Stack에는 해당 객체의 주소값을 바라보는데 그 주소값을 복사하여 동작하기 때문에 Call by Reference처럼 동작한다고 느낄 수 있습니다.
  </div>
</details>

### 2. [Override & Overload](https://skroy0513.tistory.com/19)
### 3. [JVM](https://skroy0513.tistory.com/22)
### 4. [Java의 컴파일과정](https://skroy0513.tistory.com/23)
### 5. [JVM의 스택과 힙 메모리 영역](https://skroy0513.tistory.com/25)
### 6. [클래스와 인스턴스](https://skroy0513.tistory.com/26)
### 7. [Garbage Collector](https://skroy0513.tistory.com/27)
### 8. [Java Map의 내부구현](https://skroy0513.tistory.com/28)
### 9. [IoC와 DI](https://skroy0513.tistory.com/29)
### 10. [N+1과 해결방법](https://skroy0513.tistory.com/33)
### 11. [즉시로딩&지연로딩](https://skroy0513.tistory.com/34)
### 12. [Generic](https://skroy0513.tistory.com/51)
### 13. [HashTable, HashMap, HashSet](https://skroy0513.tistory.com/52)
### 14. [추상클래스와 인터페이스](https://skroy0513.tistory.com/53)
### 15. [Java의 버전별 차이](https://skroy0513.tistory.com/57)
### 16. [Java 직렬화](https://skroy0513.tistory.com/60)
### 17. [Thread Pool](https://skroy0513.tistory.com/61)
<details>
  <summary>❓ <b><i> Thread Pool에 대해 간략히 설명해주세요</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;작업의 단위인 스레드는 한 번 생성할 때마다 OS가 해당 스레드를 위한 메모리를 확보하고, 필요 없을 땐 이 메모리영역을 회수하는 작업이 일어납니다. 이러한 작업은 큰 비용이 발생하기 때문에 반복적으로 일어나게 된다면 성능상의 영향을 끼칠 수 밖에 없습니다. 이러한 일을 방지하기 위해 Thread Pool에 미리 스레드를 많이 생성해 놓아서 작업이 요청되면 그때마다 Thread Pool에 있는 적절한 스레드에게 작업을 할당합니다.
    &nbsp;&nbsp;이 방식을 사용함으로서 프로그램의 성능 저하를 방지할 수 있으며, 다수의 요청을 효율적으로 처리할 수 있다는 장점이 있습니다. 하지만 Thread Pool을 생성할 때 적절한 양의 스레드를 만들어야 한다는 단점이 있습니다. 너무 많은 스레드를 만들면 일을 하지 않는 스레드가 메모리를 차지하는 일이 일어나며, 너무 적은 스레드를 만들게 되면 리소스 경합이 발생하여 성능에 문제가 생길 수도 있습니다.
  </div>
</details>

### 18. [Concurrent Collection](https://skroy0513.tistory.com/62)
<details>
  <summary>❓ <b><i> Concurrent Collection에 대해 간략히 설명해주세요</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;Concurrent Collection은 직역하면 병렬 컬렉션으로, 스레드가 병렬적으로 작업을 할 수 있도록 접근이 가능한 Collection을 말합니다. 여러 스레드가 한 번에 접근이 가능하기 때문에 각 스레드의 대기 시간을 줄여주며, 한 번에 하나의 스레드가 접근 가능한 Synchronized 컬렉션보다 성능이 좋습니다. 또한, 하나 이상의 스레드가 병렬적으로 read, write 연산을 할 수 있습니다. <br>
    &nbsp;&nbsp;대표적인 예로는 CopyOnWriteArrayList와 ConcurrentHashMap이 있습니다. ArrayList는 모든 쓰기 작업 시 원본 배열의 요소를 복사하여 새로운 임시 배열을 만들고 이 임시 배열에 쓰기 작업을 한 뒤 원본 배열을 갱신합니다. 동시성을 보장하기 위하여 쓰기 작업인, add() 메소드에 Lock을 겁니다. HashMap은 내부에 16개의 버킷을 가지고 있으며, 각 버킷 마다 자체적으로 Lock을 가지고 있으므로 총 16개의 Lock을 가지고 있습니다. 따라서 16개의 스레드가 동시에 접근이 가능한 HashMap입니다.
  </div>
</details>

## Spring
### 1. [JPA](https://skroy0513.tistory.com/20)
### 2. [JPA의 더티체킹](https://skroy0513.tistory.com/21)
### 3. [MVC 모델](https://skroy0513.tistory.com/30)
### 4. [Annotation](https://skroy0513.tistory.com/31)
### 5. [Spring Security의 구조(feat.JWT)](https://skroy0513.tistory.com/32)
### 6. [Spring Container, Bean](https://skroy0513.tistory.com/35)
### 7. [Filter, Interceptor, AOP](https://skroy0513.tistory.com/36)
