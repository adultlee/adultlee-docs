물리적 컴퓨터 시스템에서 "프로세스(Process)"와 "프로세서(Processor)"는 컴퓨터의 중요한 개념입니다. 이 두 용어는 컴퓨터의 작동과 관련하여 서로 다른 역할을 수행합니다.

## 프로세서(Processor)

**_프로세서는 중앙 처리 장치(Central Processing Unit, CPU)_**로도 알려져 있으며, 컴퓨터의 실제 연산과 데이터 처리를 담당하는 핵심 하드웨어입니다. 프로세서는 기본적으로 프로그램 명령을 실행하고 데이터를 처리하여 컴퓨터가 원하는 작업을 수행합니다. 주로 산술 논리 연산(ALU, Arithmetic Logic Unit)과 제어 장치(Control Unit)로 구성되어 있습니다.
프로세서는 명령어 세트(Instruction Set)를 사용하여 컴퓨터 메모리에 저장된 프로그램 명령어들을 순차적으로 해석하고 실행합니다. 프로세서는 매우 빠르게 연산을 수행하여 프로그램의 실행 속도와 컴퓨터의 성능에 직접적인 영향을 미칩니다. 최근에는 다중 코어 프로세서가 일반적으로 사용되며, 하나의 프로세서 칩에 여러 개의 코어가 내장되어 병렬 처리를 지원하여 더 높은 성능을 제공합니다.

## 프로세스(Process)

프로세스는 컴퓨터에서 실행되는 프로그램의 인스턴스(instance)입니다. 즉, 메모리에 올라와 실행 중인 프로그램을 의미합니다. 컴퓨터에서 여러 프로세스가 동시에 실행될 수 있으며, 각 프로세스는 자신만의 실행 공간과 자원을 가집니다.
프로세스는 **_운영체제에 의해 관리_**되며, 실행을 위해 필요한 자원(메모리, 파일, 입출력 장치 등)을 할당받습니다. 프로세스는 독립적으로 실행되어 다른 프로세스의 영향을 받지 않으며, 각각의 프로세스는 자신의 주소 공간과 자원에 접근할 수 있습니다. 또한, 운영체제는 여러 프로세스를 동시에 실행하고, 프로세스 간의 우선순위를 관리하여 시스템 자원의 효율적인 사용을 도모합니다.

프로세스는 생성, 실행, 일시 중지, 종료 등의 상태를 갖고 있으며, 이러한 상태 변화는 프로세서의 스케줄링과 관련하여 이루어집니다. 운영체제는 프로세스 스케줄링을 통해 프로세서에게 어떤 프로세스를 언제 실행시킬지를 결정하여 시스템의 성능과 응답 시간을 최적화합니다.

요약하면, 프로세서는 컴퓨터의 중앙 처리 장치로써 연산과 데이터 처리를 담당하고, 프로세스는 컴퓨터에서 실행 중인 프로그램의 인스턴스로써 운영체제에 의해 관리되며 독립적으로 실행됩니다.

## 요약

- 프로세서는 연산을 행하는 주체 (cpu등)
- 프로세스는 연산이 되는 대상 (프로그램)
