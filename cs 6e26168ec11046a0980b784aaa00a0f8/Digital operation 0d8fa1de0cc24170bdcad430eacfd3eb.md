# Digital operation

## 2진수

### 0과 1은 상반되는 2가지 상태

컴퓨터 안에서는 **전앞이 높다(H) 또는 낮다(L)** 두가지 상태만을 구별한다.

이러한 0과 1(L과 H)이라는 두가지 값을 이용해서 연산을 하는 것이다.

### 10진수와 2진수

사람 → 0부터 9까지 10개의 숫자를 사용하는 10진수를 사용

컴퓨터 → 0과 1만으로 수를 나타내는 2진수를 사용

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled.png)

- **bit** : 2진수의 1자리(0또는 1)를 1비트 라고한다.

    → 2진수 1001의 경우 4bit 이며 바꿔 말하면 10진수 9를 나타내려면 4비트가 필요하다

### 2진수 기본

10진수에서 356을 다르게 표현하면?

$$356 = (3*10^2)+(5*10^1)+(6*10^0)$$

2진수에서 1011을 다르게 표현하면?

$$1011 = (1*2^3)+(0*2^2)+(1*2^1)+(1*2^0)$$

이처럼 2진수이든 10진수이든 각 자리에 따라 수를 조합하여 하나의 수가 되며, 각 자리는 그 가치가 다르다.

### 2진법 변환

부동소수점은 컴퓨터에서 실수를 표현할 때 쓰는 방법이다. 실수, 그러니까 소수점이 붙어있는 수는 어떻게 2진수로 변환할까?

- 정수부

    10진수를 1이 될 때까지 계속 2로 나눠가면서 나머지를 구하고, 밑에서부터 거꾸로 읽으면 된다.

    예를 들어 10진수 35는 2진수로 바꾸면 100011이다.

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%201.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%201.png)

- 소수부

    정수부 변환의 정반대로 하면 된다. 즉 정수부에선 10진수를 2로 나눠가면서 1이나 0을 뽑았다면 소수부는 10진수에 2를 곱해가면서 1이나 0을 뽑아낸다. 그리고 정수부 변환할 때는 1이 나오면 종료했다면 여기서는 0이 나오면 종료하고, 결과를 뒤에서부터가 아니라 앞에서부터 읽어준다.

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%202.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%202.png)

### 고정 소수점(Fixed Point) 표현 방식

고정 소수점 표현 방식이라는 것은 쉽게 말해 위에서 설명한 방법대로 10진수를 2진수로 바꿨으면, 그걸 그대로 박아넣는 방식이다.

예를 들면 7.625라는 실수가 있을때, 2진수로 변환하면 111.101이 될 것이다. 이걸 이렇게 저장한다.

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%203.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%203.png)

16비트 체계를 쓴다고 가정하자. 맨 앞 1자리는 부호 비트 (Sign Bit) 라고 해서 0이면 양수, 1이면 음수라는 뜻이다. 나머지 비트들은 소수점을 기준으로 정수부랑 소수부를 표현하는 비트로 각각 나누게 되는데, 소수점의 위치는 미리 정해둔다. 소수부의 경우 앞에서부터 채우며 남는 뒷자리는 다 0으로 채운다.

이러한 고정 소수점 방식은 구현하기 편리하지만 사용하는 비트 수 대비 표현 가능한 수의 범위 또는 정밀도가 낮기 때문에 실수를 다룰 필요가 있는 범용 시스템에서는 거의 안 쓰이고, 높은 정밀도가 필요없는 소규모 시스템에서 간혹 쓰인다.

### 부동 소수점(Floating Point) 표현 방식

부동 소수점 표현 방식에서는 2진수로 변환한 결과를 대로 박아넣지 않고 몇 가지 과정을 추가로 거친다.

1. **정규화 :** 2진수를 1.xxxx... * 2^n 꼴로 변환하는 것을 말한다.

    정수부에 1만 남을 때까지 소수점을 왼쪽으로 이동시키고 이동한 칸 수만큼 n자리에 집어넣으면 된다. 예를 들어서 111.101을 정규화하면 1.11101 * 2^2가 된다.

2. **IEEE 754 부동소수점 표현**

    IEEE 표준에 따르면 부동소수점 방식으로 실수를 저장하는 데는 32비트 또는 64비트가 사용되며 32비트 기준으로 아래 그림과 같은 구조를 가진다.

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%204.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%204.png)

    - 부호 비트 : 0이면 양수 1이면 음수
    - 가수부 : 23자리로, 정규화 결과 소수점 오른쪽에 있는 숫자들을 왼쪽부터 그대로 넣으면 된다. 남는 자리는 0 으로 채운다
    - 지수부 : 정규화 한 결과에서 지수인 n을 넣는데 그대로 넣는 것이 아니라 bias 라고 하는 지정된 숫자를 더한 다음에 넣는다. IEEE 표준에서 32비트의 경우 bias는 127이다. 따라서 n + 127을 2진수로 바꾸어 넣는다.

결론적으로 7.625는 컴퓨터에서 아래와 같이 저장된다

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%205.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%205.png)

bias라는 값을 쓰는 이유는, 지수가 음수가 될 수도 있기 때문이다. 예를들면 0.000101이라는 이진수가 있을때, 정규화를 진행하면 1.0.1 * 2^-4가 된다. 

만약 bias가 없어서 지수 2를 그냥 00000010으로 저장한다면, -4는 저장할 방법이 없다. 지수부에 따로 부호 비트가 없기 때문이다. 따라서 지수 n에 127을 더하여 0~127일때는 지수 n이 음수, 128~255 구간은 양수를 표현하도록 만든 것이다. (8비트는 십진법의 0~255를 표현할 수 있음)

프로그래밍 언어의 자료형에서 float, double이라고 하는 것은 실수를 32비트 체계로 저장하냐, 64비트 체계로 저장하냐의 차이이다. 

double 그러니까 64비트 체계에서는 지수부가 11비트, 가수부가 52비트이다. 지수부가 2^11 즉 2048개의 수를 표현할 수 있으므로 0~1023 구간은 지수가 음수, 1024~2047 구간은 양수 지수를 의미하며 bias는 1023이 된다.

## 산술 연산

### 2진수의 덧셈

하위 자리부터 순서대로 자리 올림을 고려해서 계산해 나가면 된다.

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%206.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%206.png)

### 2진수의 뺄셈

뺄셈에서는 **보수**라는 개념을 사용해서 덧셈을 한다. 보수와 덧셈을 하면 뺄셈을 한 것과 같기 때문이다.

뺄셈을 하기 위해서 보수를 구하는 방법은

1. 원래 수의 각 자리를 모두 뒤바꾼다 (0은 1로, 1은 0으로)
2. 그 뒤바꾼 수에 1을 더한다

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/IMG_5938.heic](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/IMG_5938.heic)

ALU는 이러한 원리에 따라 산술 연산을 수행하며 뺄셈을 할 때는 실제로는 보수를 구하고 그 보수와 덧셈을 한다.

## 논리 연산

### IC 구조

**IC** : 

집적 회로라고 하며 여러가지 전자 부품 속에 들어가 있으며 CPU는 하나의 매우 복잡한 고도의 IC이다.

다리 같이 생긴 애를 **핀**이라고한다. 핀 하나하나는 전기의 통로이다. 여기서 0이나 1(L or H)이라는 디지털 신호를 입출력 하고있다. 

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%207.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%207.png)

**논리 회로** : 

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%208.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%208.png)

IC 속에는 아래 그림과 같은 논리 회로 라는 것이 들어 있다.

각각의 숫자는 핀을 의미한다. 핀에 연결된 반달 모양 기호에 앞으로 하나, 뒤로 둘이 연결되어 있다.

뒤로 연결된 두 핀은 입력을 나타내고, 앞으로 연결된 핀은 출력을 나타낸다.

핀과 기호를 연결하는 선을 **신호선**이라고 한다.

### 3가지 기본 회로 AND, OR, NOT

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%209.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%209.png)

1. AND 회로 

    두개의 입력으로 부터 모두 1을 전달 받았을 때만 1을 출력한다

2. OR 회로

    두개의 입력으로 부터 적어도 하나는 1을 전달 받았을 때 1을 출력한다

3. NOT 회로

    NOT회로는 입력을 하나만 받으며 전달받은 입력의 반대를 출력한다

### NAND, NOR, EXOR

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2010.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2010.png)

1. NAND (부정 논리적 회로)

    NOT+AND로 and의 결과를 not 한것

2. NOR (부정 논리화 회로)

    NOT+OR로 or의 결과를 not 한것

3. EXOR (배타적 논리화 회로)

    두개의 입력이 서로 다를 때 1을 출력한다

### 진리값 표, 벤다이어그램

진리값 표는 입출력의 모든 패턴을 표로 나타낸 것이다.

논리 회로를 벤다이어그램으로 표현할 수도 있는데 벤다이어그램의 색깔이 채워져있는지 여부로 2가지 상태를 표현한다.

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2011.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2011.png)

### 드모르간의 정리

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2012.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2012.png)

드모르간의 정리를 이용하여 AND와 OR을 치환할 수 있다.

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2013.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2013.png)

## 연산하는 회로

### 반가산기 - 덧셈을 하는 회로

AND회로와 EXOR회로를 사용하여 1비트 이진수끼리의 덧셈을 하는 회로를 만든다

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2014.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2014.png)

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/IMG_5939.heic](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/IMG_5939.heic)

하위 자리는 출력 S(sum) 상위 자리는 출력 C(carry)가 담당하여 1비트 덧셈의 논리회로를 구현할 수 있다.

이와 같이 2가지 입력으로 2가지 출력이 가능한 회로를 **반가산기(half adder)** 라고한다

### 전가산기와 순차 자리 올림 가산기

반가산기 2개를 이용하면 전가산기를 만들 수 있다. 이렇게 하면 하위자리에서의 자리 올림을 입력할 수 있기 때문에 2비트 덧셈이 가능하다.

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2015.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2015.png)

그림 처럼 3가지 입력에서 2가지 출력이 생기는 회로를 **전가산기(full adder)**라고 한다. Cin은 자리올림수 입력이고, Cout은 자리올림수 출력이다. 이러한 전가산기를 계속 연결해 나가면 여러 자릿수 덧셈이 가능한 가산 회로가 완성된다. 이를 **순차 자리 올림 가산기(Ripple carry adder)** 라고한다. 아래 그림은 전가산기 4개를 연결하여 4자릿수 덧셈이 가능한 순차 자리 올림 가산기를 표현한 회로이다.

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2016.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2016.png)

한 자리의 자리 올림 출력이 다음 자리의 자리 올림 입력으로 전달 되고 있다. 이렇게 순서대로 자리 올림이 전해져 계산이 되는 것이다. ripple carry adder는 자릿수가 큰 계산이 될수록 **전파 지연 시간**이 길어져서 계산 속도가 떨어진다. 이를 보완하는 **자리 올림 선견 가산기(carry look ahead adder)** 회로가 있다.

### Carry look ahead adder - 자리 올림 선견 가산기

자리 올림 선견 가산기는 자리 올림 부분은 따로 준비된 논리 회로로 계산하고 그 결과를 각 자리의 가산기로 전달하는 구조이다. 따라서 Ripple carry adder와 달리 상위 자리도 기다림 없이 신속하게 계산할 수 있다. (뺄셈의 경우에는 자리 내림(borrow)을 계산한다)

즉, 자리 올림이 있는지 없는지 판단하는 전용 회로가 따로 설치되어 있기 때문에 덧셈(뺄셈)의 실행과 동시에 자리 올림(자리 내림)이 있는지 여부를 판단할 수 있다. 회로 전체의 규모가 커지는 단점이 있지만, 연산 속도를 개선할 수 있다.

## 기억하는 회로

### 레지스터

메모리가 아닌 CPU에도 **레지스터** 라고하는 기억 장치가 있다. 레지스터는 연산할 때 숫자를 메모하는 등 일회용 메모장 같은 역할을 한다. 메모리보다 간편하지만 일시적인 기억이다. 레지스터를 이용하여 과거의 기억(상태)도 연산의 대상이 될 수 있다. 

예를들어 자판기에 100원과 50원을 순차적으로 투입했다고 하자. 50원을 투입하면 투입 금액이 150원으로 표시될 것이다. 이것은 과거의 **기억**인 100원과 현재 입력된 50원이 더해졌기 때문이다. 이렇게 현재의 입력에 대한 상태 변경을 위해 과거의 상태를 알아야 하는 경우에 CPU는 레지스터 라는 기억 장치를 이용하게 된다.

### 래치(latch) 와 플립플롭

컴퓨터는 0과 1의 세계이다. 즉 컴퓨터에게 기억이란 0이나 1, 어느 한쪽의 상태를 유지하는 것이다. 예를 들어 1을 기억하고 싶을 때는 시간이 지나도 계속 1의 상태를 유지하면 된다. 이것을 latch라고 한다.

0이나 1의 데이터를 유지하면서 임의의 타이밍에 0과 1일 반전시켜야 한다. 그것이 가능해야 기억 회로라고 할 수 있는 것이다. 이러한 요구를 실현시키는 것이 **플립플롭** 회로이다. 플립플롭은 기억 회로의 기본이다. 따라서 메모리나 CPU의ㅣ 레지스터 등도 플립플롭을 기본으로 구성되어 있다.

### RS 플립플롭(RS 래치)

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2017.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2017.png)

- R은 Reset, S는 Set
- S(set)에 1이 입력되면 Q는 1이 되어 유지(래치)된다
- R(reset)에 1이 입력되면 Q는 0이 되어 유지(래치)된다
- 출력 Q의 상태가 정해진 후엔 입력을 0으로 변경해도 출력은 변하지 않고 유지된다.
- S 또는 R 이라는 별도의 입력을 하면 보유하고 있는 데이터가 반전한다.
- 즉, 마지막에 입력한것이 S면 1이 기억(유지)되고 R이면 0으로 기억(유지)된다
- RS 플립플롭의 논리 구성

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2018.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2018.png)

    2가지 회로가 서로 출력을 다른 쪽 회로의 입력에 연결하고 있는 형태이다.

- 진리값 표

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2019.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2019.png)

    이전상태 유지는 Q=0 또는 Q=1이라는 출력을 계속 유지한다는 뜻이다.

    L은 Low라는 뜻으로 1과 0 중에서 0을 뜻한다

### D 플립플롭, 클록(Clock)

![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2020.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2020.png)

- 입력부의 D는 Data의 D
- 삼각 마크는 상승 에지의 마크
- 입력부의 C는 Clock의 C
- Clock - 회로의  동작 상태를 맞추는 데 필요한 일정 주기의 디지털 신호로 시계처럼 일정한 주기에 규칙적으로 L과 H(0과 1)를 반복한다. 클럭은 회로의 입력이나 출력과는 관계가 없는 별도의 존재.

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2021.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2021.png)

- 회로가 어떤 동작을 개시할 때 이 클록이 trigger가 되기도 한다.
- 클록 중에서도 0에서 1로 변하는 상태가 신호가 되는 것이 **상승 에지** (그 반대는 하강 에지)

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2022.png](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/Untitled%2022.png)

- D 플립플롭은 CLK의 상승 엣지 시점마다 D 입력을 출력Q로 전달한다.

### T 플립플롭

- 입력이 T 하나뿐인 단순한 회로
- T 입력의 신호 레벨이 0에서 1로 변화할 때마다 출력 Q가 반전한다

    ![Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/IMG_5940.heic](Digital%20operation%200d8fa1de0cc24170bdcad430eacfd3eb/IMG_5940.heic)

- 0과 1의 반전을 toggle이라고 한다.
- T 플핍플롭의 T는 toggle

### Counter 회로

todo

---

[[Digital design] 보수와 2진수의 덧셈과 뺄셈](https://issac-rok.tistory.com/4)

[컴퓨터에서의 실수 표현: 고정소수점 vs 부동소수점](https://gsmesie692.tistory.com/94)