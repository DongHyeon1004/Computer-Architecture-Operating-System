# 데이터

# 데이터란?

**비트(bit)** : 0과 1을 나타내는 가장 작은 정보 단위

n비트로 2<sup>n</sup>개의 수 표현 가능 ex) 7bits로는 128개의 수 표현 가능

1byte = 8bits

**워드(word)** : CPU가 한번에 처리할 수 있는 데이터의 크기

ex) 한번에 32비트를 처리할 수 있다면 1word = 32bits

절반은 하프 워드(half word)라고 한다. - 16bits

---

# 이진수

0과 1로만 이루어진 이진법, 컴퓨터에서 데이터를 처리하는데 중요한 역할

수학적 표기 : 아래첨자 <sub>(2)</sub> 사용     ex) 1101<sub>(2)</sub>

코드상 표기 : 앞에 0b를 사용     ex) 0b1110

## 이진수 → 십진수

ex) 

1   0   1   0   0

16  8  4   2   1

16+4=20

10100<sub>(2)</sub> → 20<sub>(10)</sub>

1     1     0     1     1     0   

32  16    8     4     2     1

32+16+4+2=54

110110<sub>(2)</sub> → 54<sub>(10)</sub>

1   .   1

1      0.5

1+0.5=1.5

1.1<sub>(2)</sub> → 1.5<sub>(10)</sub>

## 십진수 → 이진수

십진수를 2<sup>n</sup>의 덧셈으로 나눈다.

ex) 

85<sub>(10)</sub> = 2<sup>6</sup> + 2<sup>4</sup> + 2<sup>2</sup> + 2<sup>0</sup>

85<sub>(10)</sub> = 1010101<sub>(2)</sub>

37<sub>(10)</sub> = 2<sup>5</sup> + 2<sup>2</sup> +2<sup>0</sup>

37<sub>(10)</sub>  = 100101<sub>(2)</sub>

## 이진수의 음수 표현

1의 보수 - 1 → 0, 0 → 1

2의 보수 - 1의 보수 + 1

ex) 10101의 음수 표현 

10101<sub>(2)</sub> → 01010<sub>(2)</sub> → 01011<sub>(2)</sub>

             1의 보수     2의 보수

## 십육진수

수학적 표기 : 아래첨자 <sub>(16)</sub> 사용    ex) D5<sub>(16)</sub>

코드상 표기 : 0x를 앞에 사용    ex) 0xD5

0-9, A-F(10-15)

## 이진수 → 십육진수

4bits씩 끊어서 대응하는 십육진수로 바꿔줌.

ex)

11010101<sub>(2)</sub> → D5<sub>(16)</sub>

1101<sub>(2)</sub> → 13<sub>(10)</sub> → D<sub>(16)</sub>

0101<sub>(2)</sub> → 5<sub>(10)</sub> → 5<sub>(16)</sub>

## 십육진수 → 이진수

십육진수의 한글자를 4bits의 이진수로 바꿔줌.

ex)

2D<sub>(16)</sub> → 00101101<sub>(2)</sub>

2<sub>(16)</sub> → 2<sub>(10)</sub> → 0010<sub>(2)</sub>

D<sub>(16)</sub> → 13<sub>(10)</sub> → 1101<sub>(2)</sub>

---

# 문자 집합, 인코딩, 디코딩

**문자 집합** : 컴퓨터가 인식,표현 가능한 문자의 모음

**문자 인코딩** : 문자 집합에 속한 문자를 0,1로 변환하는 과정, 인코딩 과정을 거치면 ‘문자 코드’가 된다.

**문자 디코딩** : 0,1로 이루어진 문자 코드를 사람이 읽을 수 있는 문자로 변환하는 과정

문자 → 문자 코드

ex)

아스키코드(8bits 중 7bits로 표현, 1bit는 오류를 검출하기 위해 사용, 한글표현 불가)

EUC-KR(완성형 인코딩 방식: 초성, 중성, 종성의 조합으로 이루어진 완성된 하나의 글자에 고유한 코드를 부여하는 인코딩 방식)

유니코드(통일된 표준 문자 집합)
