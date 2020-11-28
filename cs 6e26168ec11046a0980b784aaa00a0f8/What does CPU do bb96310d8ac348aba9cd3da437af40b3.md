# What does CPU do?

## 컴퓨터의 중심은 CPU(중앙 연산 처리 장치)

- Centeral Processing Unit
- 주로 연산을 한다
- 연산의 종류 : 산술 연산, 논리 연산
- 산술 연산 : 덧셈, 뺄셈
- 논리 연산 : and, or, not

## 컴퓨터 5대 장치

![What%20does%20CPU%20do%20bb96310d8ac348aba9cd3da437af40b3/_5_.png](What%20does%20CPU%20do%20bb96310d8ac348aba9cd3da437af40b3/_5_.png)

- 입력 장치 : 외부에서 컴퓨터에 데이터나 지시를 입력하는 장치. 키보드, 마우스.
- 출력 장치 : 컴퓨터에서 외부로 데이터를 출력하는 장치. 모니터, 프린터.
- 연산 장치 : 연산을 하는 장치. 연산 장치는 기억 장치 및 제어 장치와의 연대가 필요.
- 기억 장치 : 데이터를 기억하는 장치.
    - 주 기억 장치(메모리)

        CPU의 연산 장치가 연산을 할 때는 반드시 메모리와 데이터를 주고받는다. 메모리에서 연산의 대상이 되는 데이터나 프로그램을 소유한다. 연산을 할 때 이러한 것을 불러오기도 하고 연산의 결과를 메모리에 주입하기도 한다.

    - 보조 기억 장치
- 제어 장치 : 메모리에서 프로그램을 읽어오고 해석하여 각 장치에 지시를 내림.

## ALU(Arithemetic Logic Unit) 산술 논리 장치

CPU의 연산 장치에 해당한다. 산술 연산과 논리 연산을 수행한다.

![What%20does%20CPU%20do%20bb96310d8ac348aba9cd3da437af40b3/Untitled.png](What%20does%20CPU%20do%20bb96310d8ac348aba9cd3da437af40b3/Untitled.png)

입력 받은 A와 B에 대해 Opcode(operation code)에 해당하는 연산을 한 후 결과(Y)를 출력한다. Status는 연산의 결과에 대한 정보를 제공한다. 예를 들어 A: 5, B: 3, opcode: 마이너스 일 때 status는 플러스 이다.