# 보조기억장치

# 하드 디스크

**하드 디스크** : 자기적인 방식으로 데이터를 저장하는 보조 기억 장치

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-1.png)

**플래터** : 실질적으로 데이터가 저장되는 곳, 더 많은 양의 데이터를 저장하기 위해 여러 겹 사용. 양면 모두 사용 가능.

**스핀들** : 플래터를 회전시키는 구성 요소

**RPM** : 스핀들이 플래터를 돌리는 속도, 분당 회전수

**헤드** : 플래터를 대상으로 데이터를 읽고 쓰는 구성 요소

**디스크 암(액츄에이터 암)** : 원하는 위치로 헤드를 이동시키는 구성 요소 

플래터는 **트랙**과 **섹터**라는 단위로 데이터를 저장한다.

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-2.png)

**트랙** : 플래터를 여러 동심원으로 나누었을 때 그중 하나의 원

**스택** : 피자처럼 여러 조각으로 나누어질 때 한 조각 

**실린더** : 여러 겹의 플래터 상에서 같은 트랙이 위치한 곳을 모아 연결한 논리적 단위

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-3.png)

연속된 정보는 디스크 암을 움직이지 않고도 바로 데이터에 접근할 수 있기 때문에 보통 한 실린더에 기록된다.

- **탐색 시간** : 접근하려는 데이터가 저장된 트랙까지 헤드를 이동시키는 시간
    
    ![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-4.png)
    
- **회전 지연** : 헤드가 있는 곳으로 플래터를 회전시키는 시간
    
    ![Untitled](
https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-5.png)
    
- **전송 시간** : 하드 디스크와 컴퓨터 간에 데이터를 전송하는 시간

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-6.png)

접근 시간

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-7.png)

- 탐색 시간, 회전 지연, 전송 시간은 성능에 큰 영향을 끼친다.
- 하드 디스크에서 데이터를 탐색하고 읽어 들이는 시간은 생각보다 길다.

성능 향상 방법

- 플래터를 빨리 돌려 RPM을 높인다.
- 접근하려는 데이터가 플래터 혹은 헤드를 조금만 옮겨도 접근할 수 있는 곳에 위치시킨다.

---

# 플래시 메모리

**플래시 메모리** : 전기적으로 데이터를 읽고 쓸 수 있는 반도체 기반의 저장 장치

- 보조 기억 장치 범주에 속하기보단 다양한 곳에 널리 사용되는 저장 장치.
- 일상적으로 접하는 거의 모든 전자 제품 안에 내장되어 있다.

**플래시 메모리 종류**

1. NAND 플래시 메모리
    - NAND 연산 수행
    - 대용량 저장 장치로 많이 사용
2. NOR 플래시 메모리
    - NOR 연산 행

**셀** : 플래시 메모리에서 데이터를 저장하는 가장 작은 단위

**SLC(Single Level Cell)** : 한 셀에 1비트를 저장할 수 있는 플래시 메모리

**MLC(Multiple Level Cell)** : 한 셀에 2비트를 저장할 수 있는 플래시 메모리

**TLC(Triple Level Cell)** : 한 셀에 3비트를 저장할 수 있는 플래시 메모리

### SLC 타입

- 한 셀로 두 개의 정보 표현 가능
- MLC나 TLC 타입에 비해 비트의 빠른 입출력이 가능.
- MLC나 TLC 타입보다 수명이 길어 수만에서 수십만 번 가까이 데이터를 쓰고 지우고 반복 가능.
- 용량 대비 가격이 높음.
- 데이터를 읽고 쓰기가 매우 많이 반복되며 고성능의 빠른 저장 장치가 필요한 경우 사용.

### MLC 타입

- 한 셀로 네 개의 정보 표현 가능.
- SLC 타입보다 속도와 수명은 떨어짐.
- 한 셀에 두 비트씩 저장 가능해 SLC타입보다 대용화 유리.
- SLC 타입보다 용량 대비 가격이 저렴.
- 시중에 사용되는 많은 플래시 메모리 저장 장치들은 MLC / TLC 타입으로 만들어짐.

### TLC 타입

- 한 셀로 여덟 개의 정보 표현 가능.
- 대용화 유리.
- SLC / MLC 타입보다 수명과 속도가 떨어짐.
- 용량 대비 가격 저렴.

**페이지** : 셀들이 모여 만들어진 단위

**블록** : 페이지가 모여 만들어진 단위

**플레인** : 블록이 모여 만들어진 단위

**다이** : 플레인이 모여 만들어진 단위

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-8.png)

- 읽기와 쓰기는 페이지 단위로 이루어짐.
- 삭제는 블록 단위로 이루어짐.
- 페이지는 세 개의 상태를 가질 수 있음.
    - **Free 상태** : 어떠한 데이터도 저장하고 있지 않아 새로운 데이터를 저장할 수 있는 상태
    - **Valid 상태** : 이미 유효한 데이터를 저장하고 있는 상태
    - **Invalid 상태** : 쓰레기 값이라 부르는 유효하지 않은 데이터를 저장하고 있는 상태
- 플래시 메모리는 덮어쓰기가 불가능해 Valid 상태인 페이지에는 새 데이터를 저장할 수 없음.

### 플래시 메모리 동작 예시

1. **데이터 C 저장**

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-9.png)

1. **A → A’으로 수정**
    
    ![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-10.png)
    
    덮어쓰기가 불가능 하기 때문에 기존에 저장된 A는 Invalid 상태로 변해 쓰레기 값이 되고, A’데이터 저장
    
    삭제는 블록 단위로 수행되기 때문에 A만 삭제 불가능
    
2. **가비지 컬렉션 이용**
    
    **가비지 컬렉션** : 쓰레기 값을 정리하기 위해 사용하는 기능
    
    ![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-11.png)
    
    가비지 컬렉션은 유효한 페이지들만 새로운 블록으로 복사하고, 기존 블록을 삭제한다.
    
    ---
    

# RAID의 정의

**RAID** : 하드 디스크와 SSD를 사용해 데이터의 안정성 혹은 높은 성능을 위해 여러 개의 물리적 보조 기억 장치를 마치 하나의 논리적 보조 기억 장치처럼 사용하는 기술

**RAID 레벨** : RAID 구성 방법

- 대표적으로 RAID 0-6, 10, 50이 있다.
- RAID 2, 3은 현재 잘 사용되지 않음.

### RAID 0

- 여러 개의 보조 기억 장치에 데이터를 단순히 나누어 저장하는 구성 방식
- 하드 디스크 개수 만큼 나뉘어 저장됨.
- **스트라입** : 줄무늬처럼 분산되어 저장된 데이터
- **스트라이핑** : 분산하여 저장하는 것
- 스트라이핑되면 저장된 데이터를 읽고 쓰는 속도가 빨라짐.
- 저장된 정보가 안전하지 않다는 단점이 있음.
- RAID 0으로 구성된 하드 디스크 중 하나에 문제가 생긴다면 다른 모든 하드 디스크의 정보를 읽는 데 문제가 생길 수 있음.

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-12.png)

### RAID 1

- 복사본을 만드는 방식
- **미러링** : 거울처럼 완전한 복사본을 만드는 구성
- 데이터를 쓸 때는 원본과 복사본 두 군데에 쓰기 때문에, 쓰기 속도는 RAID 0보다 느림.
- 복구가 매우 간단함.
- 하드 디스크 개수가 한정되었을 때 사용 가능한 용량이 적어지는 단점이 있음.
- 복사본이 만들어지는 용량만큼 사용자가 사용하지 못하므로, 많은 양의 하드 디스크가 필요하게 되고, 그에 따른 비용 증가가 발생함.

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-13.png)

### RAID 4

- 완전한 복사본을 만드는 대신 오류를 검출하고 복구하기 위한 정보를 저장한 장치를 두는 구성 방식
- **패리티 비트** : 오류를 검출하고 복구하기 위한 정보
- 패리티를 저장한 장치를 이용해 다른 장치들의 오류를 검출하고, 오류가 있다면 복구함.
- RAID 1보다 적은 하드 디스크로도 데이터를 안전하게 보관 가능.
- 새로운 데이터가 저장될 때마다 패리티를 저장하는 디스크에도 데이터를 쓰게 되므로 패리티를 저장하는 장치에 병목 현상이 발생하는 문제가 있음.

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-14.png)

### RAID 5

- 패리티 정보를 분산하여 저장하는 방식
- RAID 4의 병목 현상 해소가능

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-15.png)

### RAID 6

- 구성은 기본적으로 RAID 5와 같지만, 서로 다른 두 개의 패리티를 두는 방식
- 오류를 검출하고 복구할 수 있는 수단이 두 개.
- RAID 4 / 5 보다 안전한 구성.
- 새로운 정보를 저장할 때마다 함께 저장할 패리티가 두 개이므로, 쓰기 속도는 RAID 5보다 느림.
- 데이터 저장 속도를 조금 희생해 데이터를 더욱 안전하게 보관하고 싶을 때 사용하는 방식.

![Untitled](https://github.com/DongHyeon1004/Computer-Structure/blob/main/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B5%AC%EC%A1%B0%2B%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C/image/7-16.png)
