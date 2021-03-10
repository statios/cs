# Management of memory

## 메모리의 종류

### 특성에 따른 분류

- RAM — Random Access Memory 데이터의 읽기 쓰기 가능, 휘발성 메모리
    - DRAM (Dynamic RAM) — 메인 메모리로 사용됨. 소비 전력 적음. 대용량. 비교적 느림.
    - SRAM (Static RAM) — 캐시 메모리로 사용됨. 소비 전력 큼. 저용량. 비교적 빠름.
- ROM — Read Only Memory, 비휘발성 메모리
    - 마스크 ROM — 마이크로 프로그램 등을 기록하며 기록 내용은 변경 불가능.
    - PROM (Programmable ROM)
        - EPROM (Erasable Programmable Rom) — 자외선으로 다시 쓸 수 있는 ROM
        - EEPROM (Electrically Erasable ..) — 전기적으로 다시 쓸 수 있는 ROM. BIOS를 저장.
        - 플래시 메모리 — 전기적으로 다시 쓸 수 있는 ROM. 일괄 또는 부분적으로 삭제하거나 다시 쓰기가 가능. USB 메모리, SD카드, SSD 드라이브 등에 사용됨.

### 메모리 공간

메모리 공간은 주소라 불리는 번지를 붙여서 각 영역을 식별합니다.

CPU는 32 비트와 64 비트가 있는데, 

이 둘은 표현할 수 있는 주소의 크기가 다르므로 취급할 수 있는 메모리의 용량도 다르다.

- 32bit CPU — 최대 메모리 용량 4GB
- 64bit CPU — 최대 메모리 용량 16EB

### 메인 메모리 용도

메모리는 **책상**에 비유할 수 있다.

책상(메모리)이 크면 많은 서류(프로그램이나 데이터)를 동시에 펼쳐놓고 작업할 수 있다.

1. Heap

    파일로부터 읽어들인 데이터나 네트워크상에서 수신한 데이터를 저장할 때와 같이 

    필요한 만큼만 확보하여 사용하는 메모리 영역이다. 필요가 없어지면 해제한다.

2. Stack

    프로그램 실행 중에 이용하는 **변수의 내용을 일시적으로 저장**하는 메모리 영역이다.

    프로그램의 한 단위(C언어의 함수 등)가 시작될 때 자동적으로 확보되고 처리가 종료되면 자동으로 해제된다.

    사용할 수 있는 스택 영역의 용량은 정해져 있으므로 너무 많이 사용하면 오버플로가 발생한다.

## 가상 기억

메인 메모리보다 큰 기억 영역을 제공하는 장치

### 물리 메모리

컴퓨터에 실제로 장착되어 있는 메모리.

OS가 다룰 수 있는 메모리의 용량은 정해져 있는데, 

물리 메모리가 그 최대 용량을 모두 갖고 있다고 말할 수는 없다.

### 가상 메모리

최근의 OS는 하드디스크안에 **페이징 파일(스왑 파일)**이라는 파일을 작성한다.

이 파일과 물리 메모리를 합쳐서 **가상의 메모리 영역으로 간주**함으로써

물리 메모리의 용량을 초과한 메모리를 다룰 수 있다.

### 스왑

메모리 용량이 부족할 때 물리 메모리와 페이징 파일 사이에서 메모리상의 프로세스를 일시적으로 교환하는 것

스왑은 하드디스크에 자주 액세스하여 퍼포먼스 저하로 이어진다.

![https://raw.githubusercontent.com/statios/diagrams/671dd78a7b614e45817f891e103afc6a93df5096/os_swap.svg](https://raw.githubusercontent.com/statios/diagrams/671dd78a7b614e45817f891e103afc6a93df5096/os_swap.svg)

우선순위가 낮은 프로세스A를 페이지 파일로 저장해서 점유하고 있던 메인 메모리를 해제한다.

## 메모리 확보와 해제

OS가 프로세스나 데이터의 메모리 영역을 확보하는 것을 Allocation(할당)이라고 한다.

확보한 메모리 영역은 처리 종료 시 해제할 필요가 있다.

![https://raw.githubusercontent.com/statios/diagrams/267f43e8c1c27fcf6d6cf27b65016717ed352a3b/os_allocation.svg](https://raw.githubusercontent.com/statios/diagrams/267f43e8c1c27fcf6d6cf27b65016717ed352a3b/os_allocation.svg)

### 리로케이션 — Relocation

한번 확보한 메모리 영역의 위치를 변경하는 것

실행 중인 프로그램의 메모리 위치를 변경하는 것을 Dynamic Relocation(동적 재배치)이라고 한다.

가상 메모리상의 주소를 물리 메모리 주소로 반환할 때는 동적 재배치가 일어난다.

### 가비지 콜렉션

힙 영역이 가득 차서 액세스할 수 없을 때 불필요한 메모리 영역을 자동으로 해제하는 것.

### 컴팩션 — Compaction

단편화된 메모리의 미사용 영역을 모아서 연속으로 이용할 수 있는 메모리 영역을 만드는 것

![https://raw.githubusercontent.com/statios/diagrams/721b3cb41165249e65b3f0e7977de29174a27ad5/os_compaction.svg](https://raw.githubusercontent.com/statios/diagrams/721b3cb41165249e65b3f0e7977de29174a27ad5/os_compaction.svg)

## 데이터 저장 순서

### 메모리 추출 알고리즘

- LIFO(Last In First Out) — 메모리에 나중에 넣은 데이터를 먼저 꺼내는 방법. 스택 저장 방법.
    - push — 스택에 저장하는  것
    - pop — 스택에서 꺼내는 것
- FIFO(First In First Out) — 메모리에 먼저 넣은 데이터를 먼저 꺼내는 방법. 잡 관리의 저장 방법으로 사용된다. 데이터의 대기 행렬을 Queue라고 한다.
    - Enqueue — 큐에 저장하는 것
    - Dequeue — 큐에서 꺼내는 것

### 연결 리스트

하나의 데이터가 element와 pointer로 구성되어 

pointer가 다음 데이터의 메모리 주소를 가리킴으로써 연속한 데이터를 저장하는 방법

![https://raw.githubusercontent.com/statios/diagrams/cbba7b5598d0e168a2466320a56cb9908a47e296/os_linkedlist.svg](https://raw.githubusercontent.com/statios/diagrams/cbba7b5598d0e168a2466320a56cb9908a47e296/os_linkedlist.svg)

## 매핑 — Mapping

OS가 물리 메모리와 가상 메모리 사이에서 프로그램이나 데이터를 대응시키는 것

### 페이징 — Paging

고정 길이 페이지 단위(4KB)로 매핑을 수행하는 것.

페이징이 빈번히 일어난 것을 Thrashing(스래싱)이라고 한다.

스래싱은 CPU의 이용 효율 저하의 원인이 된다.

![https://raw.githubusercontent.com/statios/diagrams/4c058dcd961fe26c4c241770fe4182c2ef0ef019/os_mapping.svg](https://raw.githubusercontent.com/statios/diagrams/4c058dcd961fe26c4c241770fe4182c2ef0ef019/os_mapping.svg)

### 세그먼테이션 — Segmentation

가변 길이 세그먼트 단위로 매핑을 수행하는 것

세그먼트에는 프로세스에서 사용하는 메모리를 연속해서 할당한다.

![https://raw.githubusercontent.com/statios/diagrams/a77b978ef0dabcf2afd3f80a3f3494c61107559f/os_mapping_segmentation.svg](https://raw.githubusercontent.com/statios/diagrams/a77b978ef0dabcf2afd3f80a3f3494c61107559f/os_mapping_segmentation.svg)

세그먼테이션을 빈번히 수행하면 프레그먼테이션(fragmentation)이 발생하므로

컴팩션을 수행할 필요가 있다.

## 메모리 맵(I/O)

입출력 기기를 제어할 때 메인 메모리와 I/O 주소 공간을 공유하는 방식.

I/O주소 공간도 메모리의 일부로 취급한다.

### DMA(Direct Memory Access)

DMA는 CPU를 거치지 않고 입출력 장치와 메모리 사이에 직접 데이터를 주고받는 방법.

메모리와 입출력 기기 사이에 놓인 DMA 컨트롤러가 CPU를 대행하여 입출력 기기의 동작을 제어한다.

DMA 컨트롤러는 인터럽트 처리도 대행한다.

DMA는 CPU에 부담을 주지 않기 때문에 큰 데이터를 전송할 때 적합하다.