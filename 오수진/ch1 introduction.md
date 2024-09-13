ch1 Introduction
=

## 운영체제
- computer system(hw)를 운영하는 software
### computer
- 정보를 처리하는 머신
### Information
- 불확실성 측정을 수치화한 것

![image](https://github.com/user-attachments/assets/5f794540-c5f7-4c47-b006-68a692942b84)
- 정보의 단위 : bit

## 운영체제가 하는 일
- 사용자와 hw의 중간매개 역할
- 사이의 추상적 layer로써 응용 프로그램이 hw를 직접 제어하기 힘들 때, 대신 제어해주는 sw
- "컴퓨터에서 항상 실행되고 있는 프로그램"
- 운영체제의 핵심은 kernel이다. 운영체제를 kernel로 정의하기도 함
  - kernel 이 중간 다리 역할을 하는 것. 

## Computer-System Organization
- 전통적 computer system 구조
  - CPU & bus로 연결된 여러개의 장치 controller
    ![image](https://github.com/user-attachments/assets/46ef7f8d-f550-4bd5-ae9b-d96ab292980f)

### Bootstrap
- 컴퓨터 전원이 켜지면 처음으로 실행되어야 하는 프로그램
- RAM은 휘발성 메모리이므로 부트스트랩 프로그램은 비휘발성 메모리인 ROM에 로드되어 있다. 
- 부트스트랩은 OS를 메모리에 로딩하는 것. 이후에는 OS가 제어

[참고] https://yonghwankim-dev.tistory.com/188
- Bootstrap : BIOS(펌웨어)가 디스크의 MBR 영역에 존재하는 bootloader를 메모리에 적재하는 과정

### Interrupt
![image](https://github.com/user-attachments/assets/051097fa-0286-4b34-b56f-5ca0ac305c06)
- 하드웨어가 작동 중에 CPU에게 보내는 신호
- 보통 시스템 버스를 통해 신호를 보낸다. 
- 언제든지 interrupt를 보낼 수 있다. 

#### 왜 필요?
- 디바이스의 작동이 CPU의 명령 수행속도보다 현저히 느리기 때문
- CPU는 interrupt 가 오지 않으면 다른 명령을 수행하고 있다가 interrupt 가 오면 해당 연산을 처리

### 폰 노이만 아키텍처
![image](https://github.com/user-attachments/assets/b858c098-c6e5-4bda-b3e4-a292a581d6cd)
1. 명령어 실행 사이클(Instruction-execution cycle)은 첫번째로 메모리에서 명령어를 인출(fetches)하고 명령어 레지스터(Instruction Register)에 명령어를 저장함
2. 명령어는 그런다음 디코딩되어 메모리에서 피연산자(처리될 데이터 그자체)를 가져올 수 있습니다. 그리고 내부 레지스터(Internal Register)에 저장됩니다.
3. 피연산자들에게서 명령어가 실행(execute)된 이후에 결과는 다시 메모리에 저장됩니다.

### 저장장치 계층
![image](https://github.com/user-attachments/assets/156472ed-0a7d-4d6a-b10f-8bca9fdeb420)
- 위로 올라갈수록 속도는 빠르지만 저장용량이 적고 아래로 내려갈수록 속도는 느리지만 저장용량이 많음
- hard disk, solid-state disk는 우리가 흔히 아는 HDD, SSD이고 main memory는 하드웨어 부품인 RAM
- cache와 registers는 CPU 내에 존재하는 작은 용량의 기억장치
  - 캐시는 자주 사용하는 데이터를 저장하여 빠르게 접근할 수 있도록 함. 
  - register 에는 명령어나 연산에 사용될 피연산자를 저장

### I/O Structure
- 운영체제 코드의 많은 부분이 I/O를 관리하는데 사용됨

#### 현대 컴퓨터 시스템의 동작과정
![image](https://github.com/user-attachments/assets/70f97832-4a0c-4c62-aec5-65e042977627)
- device와 CPU가 통신
- 주로 OS가 Data를 memory에 적재함
- DMA(Directed-Memory Access) 
  - 단, CPU가 많이 개입되지 않는 device 작업 (ex 동영상 실행) 등 에서는 Memory와 device가 직접 통신

## 1.3 컴퓨터 시스템 아키텍처

### 컴퓨터 시스템 부품들의 정의
![image](https://github.com/user-attachments/assets/568f68ea-b7cd-4754-9036-cedc2ba16ca5)
CPU : 명령어들을 실행시키는 하드웨어, 프로세서의 종류 중 하나
Processor : 프로세서는 CPU의 일부분으로서 CPU의 핵심 기능을 수행하는 실제 칩(chip)을 가리킴
Core : 코어는 CPU 내부의 실행 엔진으로 실제로 명령어를 처리하고 연산을 수행함. 코어들은 CPU 내부에 위치하여 독립적으로 작동하거나 병렬적으로 수행할 수 있음


### 대칭형 다중 처리 (Symmetric Multiprocessing, SMP)
- 여러개의 프로세서 또는 코어가 동일한 메모리와 시스템 버스에 접근하여 작동하는 아키텍처
- SMP 시스템에서는 각 프로세서가 독립적으로 작동하지만 모든 프로세서가 공유된 메모리에 접근 가능


- SMP는 멀티 CPU와 멀티 코어 모두 구현 가능하다.
#### 멀티 CPU 설계
![image](https://github.com/user-attachments/assets/18636dbe-f835-490e-9d8b-5452982c3182)
#### 멀티 코어 설계 (Multi-core design)
![image](https://github.com/user-attachments/assets/1e18b64f-22e3-4b84-bbe3-614ff40381ae)
- 현대의 컴퓨터에는 단일 CPU 칩 안에 여러 개의 처리 코어를 가지는 멀티 코어 CPU를 사용하는 SMP 구조가 일반적이라고 함
  - 제조 비용의 감소, 전력 효율성, 통신 속도 등의 이유

## 1.4 운영체제 연산들 (Operating System Operations)
### 멀티 프로그래밍 (Multiprogramming)
- 메모리에 여러 개의 응용 프로그램을 적재하는 것
- CPU 가 쉬지않고 일을 하게 만들기 위함
- 하나의 프로그램이 대기 중일 때 다른 프로그램을 수행시켜 효율을 극대화

### 프로그램 (Program)
- 명령어의 집합(SOI, Set of Instruction)

### 멀티 태스킹(Multitasking) = 멀티프로세싱 (Multiprocessing)
- 멀티프로그래밍의 논리적 확장
- 프로그램들을 동시에 사용할 수 있게 하는 기술
- 하지만 CPU는 한번에 하나의 작업만 수행할 수 있다, 멀티태스킹을 어떻게 구현할 수 있을까?


- 정확히는 사용자가 동시에 여러 프로그램을 사용하는 것처럼 느낄 수 있도록 CPU가 빠르게 프로그램을 교체하는 것
- CPU가 프로그램을 빠르게 교체하기 위해서 CPU 스케줄링 작업이 필요

### CPU 스케줄링 
- 운영체제가 CPU에 의해 실행될 다음 프로그램을 고르는 것

#### 시분할 시스템 (time-sharing)
- 대표적인 CPU 스케줄링 방식
- 컴퓨터 자원을 일정 시간동안 분할하고 CPU는 해당 프로그램을 배분받은 시간동안만 수행시키고 다른 프로그램으로 교체

### 운영체제 연산의 2가지 모드 (유저, 커널)
- 커널에서 중요한 자원을 관리하기 때문에 사용자가 해당 자원에 쉽게 접근하지 못하도록 보호하기 위해 구분
- 시스템에 중요한 영향을 미치는 연산은 커널 모드에서만 실행되도록 함으로써 하드웨어 보안 유지
- 프로세스가 실행되는 동안 유저모드와 커널 모드를 반복적으로 변경됨
- 유저 어플리케이션은 시스템 서비스를 호출할 때 유저 모드에서 커널 모드로 전환

![image](https://github.com/user-attachments/assets/ae9bb60c-0071-4bd9-8dc0-b4b42f2854a5)

#### 1. 유저 모드 (user mode)
- 사용자가 접근할 수 있는 영역을 제한적으로 두고, 프로그램의 자원에 함부로 침범하지 못하는 모드
- 하드웨어 직접 접근 불가
- 유저 모드에서 코드를 작성하고, 프로세스를 실행하는 등의 행동을 할 수 있음
- 유저 애플리케이션 코드가 실행됨

#### 2. 커널 모드 (kernel mode)
- 잘못된 프로그램으로 인해 다른 프로그램이 잘못 실행되지 않도록 하기 위해 사용되는 모드입니다.
- 커널 모드는 모든 자원(드라이버, 메모리, CPU 등)에 접근가능
- 모든 CPU 명령을 실행할 수 있음

## 1.7 가상화 (Visualization)
- 가상화 기술은 하나의 컴퓨터 하드웨어 위에서 여러개의 다른 운영체제를 실행하는 기술
- 가상화 기술을 사용하면 하드웨어 VMM를 올리게 됩니다.
- VMware, XEN, WSL 등이 존재

![image](https://github.com/user-attachments/assets/3f942ae0-fdf9-418d-b2dc-3ef50af752cc)
