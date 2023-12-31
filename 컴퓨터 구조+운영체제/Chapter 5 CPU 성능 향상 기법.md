# CPU 성능 향상 기법

# 클럭

- 컴퓨터 부품들은 클럭 신호에 맞춰 움직인다.
- CPU는 명령어 사이클이라는 정해진 흐름에 맞춰 명령어들을 실행한다.

클럭 속도가 높아지면 CPU는 명령어 사이클을 더 빠르게 반복하고, 다른 부품들도 그에 맞춰 더 빠르게 작동한다.

클럭 속도가 높은 CPU는 일반적으로 성능이 좋기 때문에 클럭 속도는 CPU 속도 단위로 간주되기도 한다.

**클럭 속도** : ****1초에 클럭이 몇번 반복되는지. 단위는 Hz(헤르츠)

- 클럭 속도를 무작정 높이면 발열 문제가 더 심각해짐
- 클럭 속도만으로 CPU의 성능을 올리는 것에는 한계가 있다.

---

# 코어와 멀티코어

**코어** : 명령어를 실행하는 부품

**멀티코어 CPU(멀티코어 프로세서)** : 코어를 여러 개 포함하고 있는 CPU

싱글 코어의 클럭 속도가 더 높아도 멀티 코어의 성능이 더 좋다.

코어가 몇 개 포함되어 있는지에 따라 CPU의 종류가 나뉜다.

CPU의 연산 속도는 코어 수에 비례하여 증가하지는 않는다.

코어마다 처리할 명령어들을 어떻게 분배할지가 중요하고 그에 따라서 연산 속도는 크게 달라진다.

---

# 스레드와 멀티스레드

1. **하드웨어적 스레드**

**하드웨어적인 정의** : 하나의 코어가 동시에 처리하는 명령어 단위

**멀티스레드 프로세서(멀티스레드 CPU)** : 하나의 코어로 여러 명령어들을 동시에 처리하는 CPU

ex) 

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/5-1.png)

**하이퍼스레딩** : 인텔의 멀티스레드 기술

![제목 없음.png](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/5-2.png)

메모리 속 프로그램 입장에서 봤을 때 하드웨어 스레드는 한 번에 하나의 명령어를 처리하는 CPU이다. 그래서 하드웨어 스레드를 **논리 프로세서**라고 부르기도 한다.

실제 CPU 속에 코어는 12개지만, 프로그램 입장에서 봤을 때는 한 번에 하나의 명령어를 처리하는 CPU가 16개 있는 것처럼 보여서 논리 프로세서가 16이라고 나온다.

1. **소프트웨어적 스레드**

**소프트웨어적인 정의** : 하나의 프로그램에서 독립적으로 실행되는 단위

---

# **명령어 병렬 처리 기법**

명령어를 동시에 처리하여 CPU를 한시도 쉬지 않고 작동시키는 기법

---

# 명령어 파이프라인

클럭 단위로 나눈 명령어 처리 과정

1. 명령어 인출
2. 명령어 해석
3. 명령어 실행
4. 결과 저장

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/5-3.png)

**명령어 파이프라이닝** : 같은 단계가 겹치지 않으면 여러 명령어를 동시에 처리할 수 있게 해주는 기법

### 파이프라인 위험

1. **데이터 위험**

명령어 간 데이터 의존성에 의해 발생

ex)

명령어 1 : R1 ← R2 + R3

명령어 2 : R4 ← R1 + R5

R1에 R2 + R3가 저장되어야만 명령어 2를 수행할 수 있다. 만약 명령어 1 실행이 끝나기 전에 명령어 2를 인출한다면 원하지 않는 R1 값으로 명령어 2를 수행하게 된다. 따라서 명령어 2는 명령어 1에 의존적이다.

**데이터 위험** : 의존적인 두 명령어를 무작정 동시에 실행하려고 해 파이프라인이 제대로 작동하지 않는 것 

1. **제어 위험**

주로 분기 등으로 인한 프로그램 카운터의 갑작스러운 변화에 의해 발생

프로그램 카운터는 현재 실행 중인 명령어의 다음 주소로 갱신되지만, 프로그램 실행 흐름이 바뀌어 명령어가 실행되면서 프로그램 카운터 값에 갑작스러운 변화가 생기면 미리 가지고 와서 처리 중이었던 명령어들이 아무 쓸모 없어지게 된다.

**분기 예측** : 프로그램이 어디로 분기할지 미리 예측한 후 그 주소를 인출하는 기술

1. **구조적 위험(자원 위험)**

명령어들을 겹쳐 실행하는 과정에서 서로 다른 명령어가 동시에 같은 CPU 부품을 사용하려고 할 때 발생

---

# 슈퍼스칼라

**슈퍼스칼라** : CPU 내부에 여러 개의 명령어 파이프라인을 포함한 구조

**슈퍼스칼라 프로세서(슈퍼스칼라 CPU)** : 슈퍼스칼라 구조로 명령어 처리가 가능한 CPU

---

# 비순차적 명령어 처리

**비순차적 명령어 처리** : 명령어를 순차적으로만 실행하지 않고 순서를 바꿔 시행해도 무방한 명령어를 먼저 실행하여 명령어 파이프라인이 멈추는 것을 방지하는 기법

```java
순차적으로 처리하는 경우 
1. M(100) <- 1
2. M(101) <- 2
3. M(102) <- M(100) + M(101)
4. M(150) <- 1
5. M(151) <- 2
6. M(152) <- 3
```

순차적으로 처리하는 경우 3번 명령어를 실행하기 위해서는 1,2,번 명령어 실행이 끝날 때까지 기다려야 한다. 2번 명령어 실행이 끝날 때까지 3,4,5,6번 명령어들은 기다려야 한다.

```java
비순차적으로 처리하는 경우 
1. M(100) <- 1
2. M(101) <- 2
4. M(150) <- 1
5. M(151) <- 2
6. M(152) <- 3
3. M(102) <- M(100) + M(101)
```

3번 명령어의 처리 순서를 바꾸어 실행해도 문제될 것이 없다. 이렇게 순서를 바꿔 실행해도 무방한 명령어를 먼저 실행하여 명령어 파이프라인이 멈추는 것을 방지할 수 있다.

하지만 아무 명령어나 순서를 바꿔서 수행할 수 없고, 비순차적 명령어 처리가 가능한 CPU는 명령어들이 어떤 명령어와 데이터 의존성을 가지고 있는지, 순서를 바꿔 실행할 수 있는 명령어가 어떤 것인지 판단해야 한다.

---

# 명령어 집합

**명령어 집합(명령어 집합 구조, ISA)** : CPU가 이해할 수 있는 명령어들의 모음이자 하드웨어가 소프트웨어를 어떻게 이해할지에 대한 약속

CPU마다 ISA가 다를 수 있다.

ISA가 달라지면 사용되는 레지스터의 종류와 개수, 해석 방식, 메모리 관리 등 많은 것이 달라진다.

---

# CISC(Complex Instruction Set Computer)

다양하고 강력한 기능의 명령어 집합을 활용하기 때문에 명령어의 형태와 크기가 다양한 **가변 길이 명령어**를 활용

**CISC의 장점**

- 상대적으로 적은 수의 명령어로도 프로그램을 실행할 수 있다.
- 메모리를 효율적으로 사용할 수 있다.
- 명령어가 다양하기 때문에 다양한 기능을 제공한다.

**CISC의 단점**

- 활용하는 명령어가 워낙 복잡하고 다양한 기능을 제공 하는 탓에 명령어의 크기와 실행되기까지의 시간이 일정하지 않다.
- 복잡한 명령어 때문에 명령어 하나를 실행하는 데에 여러 클럭 주기가 필요하다.
    
    → 명령어 파이프라인을 구현하는 데에 큰 걸림돌 
    
- 복잡하고 다양한 명령어를 활용할 수 있지만, 대다수의 복잡한 명령어는 사용 빈도가 낮다.

---

# RISC(Reduced Instruction Set Computer)

1. 빠른 처리를 위해 명령어 파이프라인을 십분 활용해야 한다. 원활한 파이프라이닝을 위해 명령어 길이와 수행 시간이 짧고 규격화되어 있어야 한다.
2. 자주 쓰이는 명령어만 사용되므로, 복잡한 기능을 지원하는 명령어를 추가하기보다 자주 쓰이는 기본적인 명령어를 작고 빠르게 만드는 것이 중요하다.

두 가지 원칙 하에 등장.

RISC는 CISC에 비해 명령어의 종류가 적고, 짧고 규격화된 명령어, 되도록 1클럭 내외로 실행되는 명령어인 **고정 길이 명령어**를 활용한다. 명령어 파이프라이닝에 최적화되어 있다.

메모리에 직접 접근하는 명령어를 load, store 두 개로 제한할 만큼 메모리 접근을 단순화화고 최소화하는 대신 레지스터를 적극적으로 활용한다. 때문에 CISC보다 레지스터 이용 연산이 많고, 범용 레지스터 개수도 더 많다.

CISC보다 명령어 개수가 적기 때문에 많은 명령으로 프로그램을 작동 시킨다.
