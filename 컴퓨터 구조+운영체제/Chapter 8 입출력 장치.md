# 입출력장치

**입출력 장치(주변 장치)** : 키보드, 마이크, 마우스, 프린터 등 컴퓨터 외부에 연결되어 내부와 소통하는 장치.

---

# 장치 컨트롤러(입출력 제어기, 입출력 모듈)

### **입출력 장치를 다루기 까다로운 이유**

1. **너무나 많은 종류**
    
    키보드, 모니터, USB, 마우스, 스피커 등 
    
    장치마다 속도, 데이터 전송 형식이 다양하기 때문에 정보를 주고받는 방식을 규격화 하기가 어렵다.
    
2. **입출력 장치의 데이터 전송률은 낮다.**
    
    **전송률** : 데이터를 얼마나 빨리 교환할 수 있는지를 나타내는 지표
    
    전송률의 차이는 CPU와 메모리, 입출력 장치 간의 통신을 어렵게 한다.
    

**장치 컨트롤러** : 입출력 장치를 컴퓨터에 연결해주는 하드웨어

1. **CPU와 입출력 장치 간의 통신 중개**
    
    일종의 번역가 역할
    
2. **오류 검출**
    
    번역 과정에서 연결된 입출력 장치의 오류 검출
    
3. **데이터 버퍼링**
    
    **버퍼링** : 전송률이 높은 장치와 낮은 장치 사이에 주고받는 데이터를 **버퍼**라는 임시 저장 공간에 저장하여 전송률을 비슷하게 맞추는 방법
    
    전송률 차이를 완화
    

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-1.png)

### 장치 컨트롤러의 기본 내부 구조

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-2.png)

**데이터 레지스터** : CPU와 입출력 장치 사이에 주고받을 데이터가 담기는 레지스터, 버퍼 역할

**상태 레지스터** : 입출력 장치의 상태 정보 저장

**제어 레지스터** : 입출력 장치가 수행할 내용에 대한 제어 정보와 명령 저장

---

# 장치 드라이버

**장치 드라이버** : 장치 컨트롤러의 동작을 감지, 제어함으로써 장치 컨트롤러가 컴퓨터 내부와 정보를 주고받을 수 있게 하는 프로그램, 입출력 장치를 연결하기 위한 소프트웨어적인 통로

연결된 장치의 드라이버를 인식하고 실행할 수 있다면 어떤 회사에서 만들어진 제품이든 상관없이 컴퓨터 내부와 정보를 주고받을 수 있다.

---

# 프로그램 입출력

**프로그램 입출력** : 프로그램 속 명령어로 입출력 장치를 제어하는 방법

CPU가 프로그램 속 명령어를 실행하는 과정에서 입출력 명령어를 만나면 입출력 장치에 연결된 장치 컨트롤러와 상호 작용하며 입출력 작업을 수행한다.

ex) 하드 디스크에 백업하는 상황

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-3.png)

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-4.png)

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-5.png)

프로그램 입출력 방식에서의 입출력 작업은 CPU가 장치 컨트롤러의 레지스터 값을 읽고 씀으로써 이루어진다.

1. **메모리 맵 입출력**
    - 메모리에 접근하기 위한 주소 공간과 입출력 장치에 접근하기 위한 주소 공간을 하나의 주소 공간으로 간주하는 방법
    - n개의 주소 공간이 있을 때 **n/2개**는 메모리 주소를, 나머지 **n/2개**는 장치 컨트롤러의 레지스터를 표현하기 위해 사용된다.
    
    ![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-6.png)
    
    - CPU는 메모리의 주소들이나 장치 컨트롤러의 레지스터들이나 모두 똑같이 메모리 주소를 대하듯 하면 되기 때문에 명령어가 다를 필요 없다.

1. **고립형 입출력**
    - 메모리를 위한 주소 공간과 입출력 장치를 위한 주소 공간을 분리하는 방법
    - 주소 공간이 n개가 있다면 메모리용 주소 공간은 **n개**, 입출력 장치용 주소 공간도 **n개**가 존재
    
    ![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-7.png)
    
    - 주소 공간이 분리되어 있기 때문에 메모리 접근을 위한 명령어와 입출력 장치에 접근하기 위한 명령어가 다르다.

---

# 인터럽트 기반 입출력

**인터럽트 기반 입출력** : 인터럽트를 기반으로 하는 입출력

- 입출력 장치가 아닌 장치 컨트롤러에 의해 입출력 장치에 의한 하드웨어 인터럽트 발생
- 장치 컨트롤러가 발생시킨 인터럽트 요청 신호로 CPU는 하던 일을 백업하고 인터럽트 서비스 루틴을 실행한다.
- 여러 입출력 장치에서 발생하는 인터럽트의 경우 우선순위에 따라서 인터럽트를 처리
- **NMI(Non-Maskable Interrupt)** : 플래그 레지스터 속 인터럽트 비트를 비활성화해도 무시할 수 없는 인터럽트, 우선순위가 가장 높음
- **PIC(프로그래머블 인터럽트 컨트롤러)** : 여러 장치 컨트롤러에 연결되어 장치 컨트롤러에서 보낸 하드웨어 인터럽트 요청들의 우선순위를 판별한 뒤 CPU에 지금 처리해야 할 하드웨어 인터럽트가 무엇인지 알려주는 장치
    
    ![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/8-8.png)
    
    각 핀에는 약속된 하드웨어가 연결되어 있다.
    

- **PIC의 다중 인터럽트 처리 과정**
    1. PIC가 장치 컨트롤러에서 인터럽트 요청 신호들을 받아들임.
    2. 우선순위를 판단해 CPU에 처리해야 할 인터럽트 요청 신호를 보냄.
    3. CPU가 PIC에 인터럽트 확인 신호를 보냄.
    4. PIC가 데이터 버스로 CPU에게 인터럽트 벡터를 보냄.
    5. CPU는 해당 장치의 인터럽트 서비스 루틴 실행

---

# DMA 입출력

**프로그램 기반 입출력과 인터럽트 기반 입출력의 공통점**

입출력 장치와 메모리 간의 데이터 이동은 CPU가 주도, 이동하는 데이터도 반드시 CPU를 거침.

**DMA** : 직접 메모리에 접근할 수 있는 입출력 기능

- DMA 입출력을 하기 위해서 시스템 버스에 연결된 DMA 컨트롤러라는 하드웨어가 필요하다.

- **DMA 입출력 과정**
    1. CPU는 DMA 컨트롤러에 여러 정보로 입출력 작업을 명령.
    2. DMA 컨트롤러는 CPU 대신 장치 컨트롤러와 상호 작용하며 입출력 작업 수행. 필요한 경우 메모리에 직접 접근함.
    3. 작업이 끝나면 CPU에 인터럽트를 걸어 작업이 끝났음을 알림.

- 입출력 장치와 메모리 사이에 주고받을 데이터는 CPU를 거치지 않고, 오로지 입출력의 시작과 끝에만 관여한다.
- 시스템 버스는 공용 자원이기에 동시 사용이 불가능하다. DMA 컨트롤러는 CPU가 시스템 버스를 이용하지 않을 때마다 조금씩 이용하거나, CPU가 일시적으로 시스템 버스를 이용하지 않도록 허락을 구하고 집중적으로 이용한다.

### 입출력 버스

- DMA 컨트롤러의 시스템 버스 사용 빈도가 증가하면 그만큼 CPU가 시스템 버스를 이용하지 못하는 문제를 해결하기 위함.
- 대부분의 입출력 장치는 입출력 버스와 연결.
- PCI 버스, PCI Express 버스 등 여러 종류 존재.

### DMA 입출력의 단점

- CPU의 개입에서 독립적이기 때문에 제어가 불가능하다.
- **사이클 스틸** : CPU가 작업을 하고 있는 와중에 DMA에 의해서 인터럽트가 발생하여 입출력 작업이 우선권을 갖게 되는 것
- 입출력만을 담당하는 입출력 채널(입출력 프로세서)을 만들게 됐다.
