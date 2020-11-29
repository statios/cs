# Structure of CPU

## 메모리와 CPU

### Address

메모리 속에는 어드레스가 있다. 메모리 안에는 프로그램과 데이터가 저장되어 있다. 그리고 저장 장소에 따라 어드레스가 할당되어 있는 것이다.

CPU가 직접 관리하고 있는 공간을 **어드레스 공간(메모리 공간)** 이라고 한다.

Address를 통해서 원하는 데이터를 번호로 지정할 수 있다. 따라서 CPU가 메모리에서 데이터나 프로그램을 호출할 때 해당 어드레스 번호만으로 가져올 수 있게 된다.

### Bus

bus는 컴퓨터 내 데이터의 통로라고 할 수 있다.

**Address bus** : address를 지정하는 버스

**Data bus** : data를 주고받는 버스

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus.png)

**External bus** : CPU와 외부 장치를 연결하는 버스

**Internal bus** : CPU 내부를 연결하는 버스

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-3.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-3.png)

**Multiplexer(MUX)** : 내부 버스의 내부에서 경로를 전환 시키는 장치.

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-4.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-4.png)

### 버스 폭과 비트 수

버스는 데이터의 통로라고 했는데 구체적으로는 **신호선을 다발로 묶은 것**이라고 볼 수 있다. 신호선은 0이나 1이라는 전기 신호가 지나다니는 선이다. 또한 신호선은 가닥수에 따라 표현할 수 있는 숫자가 달라진다. 예를들어 4가닥의 신호선이 있으면 4자리(4비트)의 2진수를 나타낼 수 있다.

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-5.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-5.png)

결국 신호선의 가닥수=비트 수가 된다. 4가닥의 신호선이면, 0000부터 1111까지 16가지 수를 표현할 수 있는 것이다. 신호선의 가닥수(비트 수)를 **버스 폭** 이라고 부른다. 버스 폭이 넓을 수록(비트 수가 많을 수록) CPU의 처리 능력이 향상된다. 예를들어 한 번에 4비트의 연산을 처리하는 ALU의 모습을 보면, 데이터 버스 폭도 4비트라는 것을 알 수 있다.

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-6.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-6.png)

ALU의 처리 폭(예를 들어 64비트)에 따라 데이터 버스 폭을 맞추는 것이 합리적이라서 데이터 버스 폭도 결과적으로 64비트가 되는 경우가 많다. **64비트 CPU**라는 건 이런 의미를 담고 있다. CPU의 비트 수와 데이터 버스 폭이 반드시 일치하는 것은 아니다. 예를 들어 1982년경 16비트 CPU의 경우, ALU가 16비트인데 데이터 버스 폭이 8비트인 것도 있었다. 그렇기 때문에 CPU로 데이터를 불러들이려면 데이터 버스를 통해 메모리에서 2회 데이터를 거둬들여야 했다.

외부 버스 폭 → CPU와 메모리가 한 번에 데이터를 몇 비트 주고받을 수 있는지 결정

내부 버스 폭 → CPU 내부에서 한 번에 연산을 몇 비트 할 수 있는지 결정

어드레스 버스 폭 → 어드레스를 몇 비트로 지정할 수 있는지 결정

정리하면 CPU의 능력은 버스 폭으로 판단할 수 있으며 데이터 버스 폭은 넓을 수록 좋다.

어드레스 버스 폭은 어드레스를 몇 비트로 지정할 수 있는지 결정되는데 이에 따라 **어드레스 공간 크기**도 정해진다.  예를들어 어드레스 폭이 32비트라고 하면, 2^32인 약 40억개의 어드레스가 존재한다. 그리고 어드레스 버스 폭은 어느 정도의 메모리 용량을 다룰 수 있는가 하는 문제와도 연결된다. 간단하게 말하면 어드레스 버스 폭도 넓을 수록 좋다.

### 메모리 용량과 버스 폭

메모리의 용량과 버스 폭에 대하여 생각해보자.

다음 그림과 같이 하나의 어드레스에 1byte의 데이터가 할당되어 있다고 가정하자. 1바이트는 8비트로, 데이터의 크기를 나타내는 단위다.

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/Untitled.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/Untitled.png)

이 경우 어드레스 공간(어드레스 버스 폭)이 12비트이면 2의 12승으로, 어드레스의 수는 4096이 된다. 하나의 어드레스에 1바이트의 데이터이므로 취급할 수 있는 메모리 용량의 상한은 4096byte = 약 4kbyte가 된다.

### R/W 제어

**Read** : 저장되어 있는 데이터를 추출하는 것.

**Write** : 데이터를 기록해서 저장.

Load/Store라는 표현도 있는데, R/W는 하드웨어 측면에서, L/S는 소프트웨어 측면에서 바라본 표현이다. R/W는 메모리에 대한 읽기/쓰기 이고, 읽은 데이터를 어디로 가져갈 것인지, 어디에 있는 데이터를 쓸 것인지에 대해서는 관여하지 않는다. 한편 Load는 메모리에서 읽은 데이터를 레지스터로 이동시킨다. Store는 레지스터에서 데이터를 이동시켜 메모리에 쓴다. 이처럼 L/S는 데이터의 흐름을 의식하고 있다.

**제어 신호 :** control bus를 통해서 read/write 등의 신호를 보내는데 이것을 제어 신호라고 한다. 예를 들어 '83번 데이터가 필요하다'라는 명령을 할 때 실제로는 어드레스 버스로 '83번' 이라는 신호를, 제어 버스로 'read'라는 제어 신호를를 전달한다.

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-7.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-7.png)

### I/O (input/output)

**I/O 제어(I/O 신호) :** 입력 장치는 키보드와 마우스가 있고, 출력 장치는 모니터와 프린터가 있다. 이러한 외부 장치를 작동시키기 위한 제어 신호

**I/O 포트(입출력 포트)** : 외부와 데이터 주기받기를 하는 현관 역할을 한다. 이 포트를 경유하여 CPU와 외부 장치가 직접 연결되어 있다. (일반적으로 디스플레이는 CPU와 직접 연결되어 있지 않다.)

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-8.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-8.png)

### 명령의 구성요소

**operand** : 연산 등의 대상이 되는 것 (오퍼랜드, 피연산자). 실제 데이터가 아닌 Address로 지정하는 경우도 있다.

**opcode** : CPU가 수행해야하는 동작 (동작 코드, 명령코드)

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-9.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-9.png)

### 레지스터

CPU 속의 메모장같은 간단한 기억 장치인 **레지스터**는 명령을 실행할 때 반드시 필요하다. 레지스터는 용도에 따라 여러가지 종류가 있다.

**Accumulator(누산기)** : 계산 전용 메모장 같은 것이고 연산에 반드시 이용한다

**범용 레지스터** : 계산 외에도 여러가지 작업에 이용하는 레지스터

**명령 레지스터** : 메모리에서 읽은 명령(프로그램)을 일단 저장해두기 위한 레지스터

예를들어 1번 데이터와 2번 데이터를 더하라는 명령은 다음과 같은 절차를 거친다. 데이터는 일단 한 번은 레지스터에 저장한다고 생각해야 한다.

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-10.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/bus-10.png)

1. 1번 address의 데이터 2를 accumulator에 저장
2. 2번 address의 데이터 98을 범용 레지스터에 저장
3. ALU에서 덧셈 연산 실행
4. 연산 결과 데이터인 100은 자동적으로 accumulator에 저장

## CPU의 명령 처리 동작

### 고전적 CPU의 구조

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process.png)

### CPU의 명령 처리 동작

**Program counter** : 모든 CPU에 반드시 있는 매우 중요한 장치이며 항상 다음에 실행할 명령의 Address를 기억하고 있다.  

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process-3.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process-3.png)

1. 다음 명령의 address를 계산한다
2. address register에 저장한다
3. 메모리에 전달한다

**명령 디코더** : 메모리에서 호출된 명령 코드를 연산 처리를 할 수 있도록 하드웨어 내부에서 전환하는 동작을 수행한다.

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process-4.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process-4.png)

1. 메모리에서 address가 지정된 명령을 cpu로 전달한다
2. 전달받은 명령을 우선 명령 레지스터에 저장한다
3. 명령 디코더로 전달하여 해독한다
4. 해돌 결과 명령어인 operand와 opcode를 알 수 있다

이후에는 해당 명령어를 accumulator를 이용하여 ALU에서 연산한다. 그 결과를 메모리나 레지스터에 저장하는 것이다. 명령 처리 과정을 정리하면 다음과 같다.

1. 명령 읽기(페치)
2. 명령 해독(디코드)
3. 명령 실행
4. 결과 쓰기 (다음 명령을 수행하기 위해 1번으로)

### Program counter

다음 명령의 address를 count하는 역할을 한다. count가 수행되는 trigger timming은 명령이 명령 레지스터에 저장 되었을 때다. 주의할 점은 program counter는 다음에 실행해야 할 명령의 어드레스를 count하는건 맞지만 address가 7번 다음에 갑자기 15번이 되거나 3번이 될 가능성도 있다는 것이다. 

프로그램에는 조건 판단에 의한 분기와 반복이 있기 때문이다. 분기 또는 반복에 의해서 실행해야 할 명령의 address 번지수는 값이 점프하게 된다. 

![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process-7.png](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/cpu_process-7.png)

이러한 분기나 반복을 실현하기 위해서 program counter는 다음에 count하는 address를 분기나 반복에 따른  address로 바꿔 쓴다. 즉 처리할 명령을 address에 대하여 순차적으로 하는 것이 아니라 program counter에 의해 적절한 address로 변경되어 명령을 수행하게된다. 

또한 기본적으로 program counter의 비트 수(pc가 나타내는 address의 비트 수)는 address bus의 비트 수와 동일하고 address 공간의 비트 수와도 동일하다.

컴퓨터에서 사용되는 cpu의 경우, os에서 실행되는 응용 프로그램에서는 address counter의 비트 수를 프로그래머가 신경 쓸 필요가 없다. 실제로 이용하는 메모리를 어떻게 잃고 쓸 것인지(액세스)는 os에 따라 관리되는 가상 메모리라는 개념에 속한다. 이 가상 메모리와 실제 메모리를 대응시키고 있는 하드웨어를 MMU(memory mapping unit)라고 한다.

## 여러 가지 기억 장치

**Main memory(주 기억 장치) :** 메모리

**보조 기억 장치 :** 하드디스크, SSD

메모리는 책상, 하드디스크는 서랍이라고 생각하자. 책상이 넓으면(메모리 용량이 크면) 동시에 많은 작업을 할 수 있다. 서랍이 크면(하드디스크 용량이 크면) 많은 것을 저장할 수 있다. CPU는 이러한 책상에 앉아서 업무를 하는 사람이라고 생각하면 적절한 비유가 될것이다.

1. 전원을 끄면 메모리에 있는 데이터는 사라지지만 하드디스크에 있는 데이터는 유지된다
2. 메모리는 CPU에서 직접 읽고 쓸 수 있지만 하드디스크는 직접 읽고 쓸 수 없다.

    ![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/Untitled_Diagram.jpg](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/Untitled_Diagram.jpg)

    ![Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/Untitled_Diagram.svg](Structure%20of%20CPU%205d6cbcb1530041f787f9eab3f8f77f66/Untitled_Diagram.svg)