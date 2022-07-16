# Operating System



## Program

실행파일로 파일 시스템에 존재하는 실행파일이다.

- .exe 파일이 프로그램이다.



## Process

프로그램을 실행하면 운영체제가 그 프로그램을 실행하게 된다.

실행 주체를 인스턴스라고 표현한다. 이 인스턴스가 프로세스이다.

- 한글 파일을 실행하면 프로세스이며 한글 파일에서 프린트 기능을 실행하면 프린트 프로세스가 실행된다.
- 프로세스는 process ID(PID)로 관리한다.
- 프로세스는 완벽히 독립적이기 때문에 메모리 영역(code, data, heap, stack)을 다른 프로세스와 공유하지 않는다. 프로세스는 최소 1개의 스레드(main thread)를 가진다.

[Process](https://jhnyang.tistory.com/6)



## Thread

스레드는 프로세스 내에서 실제로 작업을 수행하는 주체를 의미한다.

- 프로그램 내에서 실행되는 프로그램 제어 흐름(실행 단위)이다.
- 모든 프로세스에는 한 개 이상의 스레드가 존재하여 작업을 수행하낟.
- 두 개 이상의 스레드를 가지는 프로세스를 멀티스레드(multi-threaded process)라고 한다.
- 스레드는 프로세스 내에서 stack만 따로 할당 받고 그 이외의 메모리 영역(code, data, heap) 영역을 공유하기 때문에 다른 스레드의 실행 결과를 즉시 확인할 수 있다.
- 프로세스는 운영체제로부터 자원을 할당받는 작업의 단위이고 스레드는 프로세스가 할당받은 자원을 이용하는 실행단위이다.

[Thread](https://akdl911215.tistory.com/327)



## Multi Process & Multi Thread



### Multi Process

두 개 이상 다수의 프로세서(CPU)가 협력적으로 하나 이상의 작업(task)을 동시에 처리하는 것이다(병렬처리).

- 각 프로세스 간 메모리 구분이 필요하거나 독립된 주소 공간을 각져야 할 경우 사용한다.
- 장점
  - 독립된 구조로 안정성이 높다.
  - 프로세스 중 하나에 문제가 생겨도 다른 프로세스에 영향을 주지 않아, 작업속도가 느려지는 손해정도는 생기지만 정지되거나 하는 문제는 발생하지 않는다.
  - 여러개의 프로세스가 처리되어야 할 때 동일한 데이터를 사용하고, 이러한 데이터를 하나의 디스크에 두고 모든 프로세서(CPU)가 이를 공유하면 비용적으로 저렴하다.
- 문제점
  - 독립된 메모리 영역이기 때문에 작업량이 많을수록(context switching이 자주 일어나서 주소 공간의 공유가 잦을 경우) 오버헤드가 발생하여 성능 저하가 발생 할 수 있다.
  - context switching 과정에서 캐시 메모리 초기화 등 무거운 작업이 진행되고 시간이 소모되는 등 오버헤드가 발생한다.



### Multi Thread

하나의 프로세스에 여러 스레드로 자원을 공유하며 작업을 나누어 수행하는 것이다.

- 장점
  - 시스템 자원소모 감소(자원의 효율성 증대)
    - 프로세스를 생성하여 자원을 할당하는 시스템 콜이 줄어 자원을 효율적으로 관리할 수 있다.
  - 시스템 처리율 향상(처리비용 감소)
    - 스레드 간 데이터를 주고 받는 것이 간단해지고 시스템 자원 소모가 줄어든다.
    - 스레드 사이 작업량이 작아 context switching이 빠르다(캐시 메모리를 비울 필요가 없다)
  - 간단한 통신 방법으로 프로그램 응답시간 단축
    - 스레드는 프로세스 내 스택영역을 제외한 메모리 영역을 공유하기에 통신 비용이 적다.
    - 힙 영역을 공유하므로 데이터를 주고 받을 수 있다.
- 문제점
  - 자원을 공유하기에 동기화 문제가 발생할 수 있다(병목현상, 데드락 등).
  - 주의 깊은 설계가 필요하고 디버깅이 어렵다(불필요 부분까지 동기화하면, 대기시간으로 인해 성능 저하 발생)
  - 하나의 스레드에 문제가 생기면 전체 프로세스가 영향을 받는다.
  - 단일 프로세스 시스템의 경우 효과를 기대하기 어렵다.



### Multi Process vs Multi Thread

- 멀티 스레드는 멀티 프로세스보다 적은 메모리 공간을 차지하고 context switching이 빠른 장점이 있지만, 동기화 문제와 하나의 스레드 장애로 전체 스레드가 종료 될 위험이 있다.
- 멀티 프로세스는 하나의 프로세스가 죽더라도 다른 프로세스에 영향을 주지 않아 안정성이 높지만, 멀티 스레드보다 많은 메모리공간과 CPU 시간을 차지하는 단점이 있다.



#### Why Multi Thread?

- 운영체제가 시스템 자원을 효율적으로 관리하기 위해 스레드를 사용한다.
- 멀티 프로세스로 실행되는 작업을 멀티 스레드로 실행할 경우, 프로세스를 생성하여 자원을 할당하는 시스템 콜이 줄어들어 자원을 효율적으로 관리할 수 있다.
- 프로세스 간의 통신보다 스레드 간의 통신 비용이 적으므로 작업들 간 통신의 부담이 줄어든다(처리비용 감소. 프로세스는 독립구조이기 때문).
- 하지만 스레드를 활용하면 자원의 효율성이 증가하기도 하지만, 스레드 간의 자원 공유는 전역 변수를 이용하므로 동기화 문제가 발생할수 있으므로 프로그래머의 주의가 필요하다.

[Multi Process & Multi Thread](https://wooody92.github.io/os/%EB%A9%80%ED%8B%B0-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EB%A9%80%ED%8B%B0-%EC%8A%A4%EB%A0%88%EB%93%9C/)



## Context Switching



### Process Control Block

프로세스는 자신에 관한 정보를 하나의 데이터 구조에 저장하여 관리하고 이를 Process Control Block(PCB)라고 한다.

- 프로세스 상태 : 생성, 준비, 수행, 대기, 중지
- 프로그램 카운터 : 프로세스가 다음에 실행할 명령어 주소
- 레지스터 : 누산기, 스택, 색인 레지스터
- 프로세스 번호



### Thread Control Block

하나의 스레드를 관리하는데 필요한 정보를 담고 있는 구조체이다.

- 프로세스의 상태를 관리하는 PCB보다 적은 양의 정보가 담겨있다.
- 스레드 사이의 context switching과 프로세스 사이의 context switching을 할 때 CPU scheduling을 하는 최소단위이다.
- Thread Idendifier : 스레드를 구분하는 유일한 식별자
- Stack Pointer : 스레드 별로 고유한 stack의 pointer
- Program Counter : 현재 instruction의 주소
- Thread State : (running, ready, waiting, start, done)
- Thread's register values
- 스레드가 소속된 processor의 PCB 주소



### Context

프로그래밍에서 Context는 (동작, 작업들의 집합)을 (정의, 관리, 실행)하도록 하는 (최소한의 상태, 재료, 속성)을 포함하는 (객체, 구조체, 정보)이다.

- 프로세스의 경우 현재 프로세스가 중단 되었을 때, 중단된 시점부터 다시 프로세스를 실행하기 위한 정보를 Context라고 부른다.
- 프로세스의 Context정보는 PCB 구조체에 저장된다.



### Scheduling

"자원"에 "작업"을 할당하는 행위이다.

- "자원"은 프로세서(Processor), 네트워크 연결, 외부 장치 등을 의미하고, "작업"은 thread, process 혹은 data flows를 의미한다.
- 스케쥴링은 scheduler라는 프로세스에 의해 수행되며, 모든 자원이 골고루 사용될 수 있게 디자인 된다.



### Context Switching

작업의 주체가 현재 Context를 잠시 중단하고 다른 Context를 실행하는 것이다.

- CPU의 코어가 1개(자원이 1개)라면 동시에 단 하나의 프로세스만 실행이 가능하다. CPU scheduling을 통해 하나의 CPU를 여러 작업들이 공유할 수 있게 CPU 시간을 나누어 작업한다.
- 프로세서가 지금까지 실행되던 프로세스(A)를 중지하고 다른 프로세스(B)의 PCB정보를 바탕으로 프로세스(B)를 실행하는 것을 Process Context Switching이라고 한다.
- 동일한 프로세스 속에서 하나의 스레드(a)를 중지하고 다른 스레드(b)의 TCB정보를 바탕으로 스레드(b)를 실행하는 것을 Thread Context Switching이라고 한다.



### Process Context Switching vs Thread Context Switching

- 스레드들은 고유한 Stack영역의 메모리와 고유한 register를 할당 받으며 Heap영역의 메모리에서 선언된 데이터(전역 변수)는 서로 공유한다.
- 동일한 프로세스 속에서 thread context switching이 발생할 경우 processor는 stack영역의 주소와 registers 주소를 포함한 스레드의 context정보만 변경하면 된다. 여기서 register은 스레드의 저장된 상태를 의미한다.
- process context switching이 발생할 경우 processor는 thread의 context뿐만 아니라 process의 context까지 모두 변경해야 한다.



## CPU Scheduling



### Process State

프로세스가 실행하면서 변하는 상태정보이다. 보통은 Five-state라 하여 프로세스 상태를 설명한다.

- New : 프로세스가 만들어지는 과정의 상태이다.
- Terminated : 프로세스가 다 수행되어 종료할 때 저장되는 상태이다.
- Running : CPU에서 프로세스가 수행되고 있는 상태이다.
- Ready : CPU를 할당받기를 기다리는 상태이며 언제든지 수행될 수 있는 상태이다.
- Waiting : ready와 다르게 I/O나 다른 이벤트가 발생하기를 기다리는 상태이다.
- Running -> Waiting, Waiting -> Running
  - 로그인 시 입력해야 하는데 이때 프로세스는 running -> waiting이 수행된다.
  - 이러한 과정은 I/O나 이벤트를 기다릴 때 수행된다.
  - 수행이 끝나면 interrupt 신호를 발생한 후 waiting -> ready로 상태가 변한다.
- Ready -> Running
  - ready 상태의 프로세스 중 하나를 고르는 것을 scheduling이라고 하며 고른 프로세스를 CPU에 올리는 것을 dispatch라고 한다.
  - 물론 running 도중 interrupt가 발생하여 running -> ready로 상태가 변할 수 있다. Preemption이라고 하며 프로세서 스케쥴링 등으로, 프로세서를 잃고 다시 프로세서 할당을 대기하는 것이다.



### CPU Scheduling

CPU 자원을 최대한 활용할 수 있는가에 대한 프로세스이다.

보통 CPU를 짧은 시간 내에 최대한 활용하기에 이를 적절히 분배하기 위해 필요하다.

Ready Queue에 들어간 순서대로 실행을 하는데 이를 우선순위에 따라 다시 정렬하는 방식이다.



#### Short-Term Scheduler

- 4가지 경우 프로세스를 새로 선택해야 한다.
  1. Running -> Waiting
  2. Running -> Ready
  3. Waiting -> Ready
  4. Terminate
- 1, 4번은 nonpreemptive하다. 즉, 중간에 끊기지 않는 경우이다.
- 2, 3번은 preemptive하다. 즉, 중간에 끊기는 경우이다.



#### Dispatcher

- context switching이 일어나게 해준다. 하나의 프로그램으로 scheduling decision을 할 때도 호출된다.
- Dispatcher latency = context switching delay
  - 순수 overhead
- latency가 짧을 수록 시스템의 효율성은 빠르다.



#### Non-Multitaksing



##### First-Come, First-Served

- "FIFO" 라고 부른다.

- 가장 먼저 온 프로세스부터 수행한다.
- Convoy effect : short process가 long process 뒤에 있어서 시간 손해를 많이 본 경우이다.
- 하나의 CPU bound process, 많은 I/O bound process(비교적 짧은)인 경우를 생각한다.



##### Shortest Job First

- "SJF" 라고 부른다
- 평균 waiting time이 최소가 되는 것을 보장한다.
- 수행 시간을 알기 위해 예측을 한다.
  - 이전에 실행되었던 시간 정보를 이용하여 그 시간에 가깝게 task 수행시간을 정하고 예측한다.
  - 첫 수행은 default 값으로 예측한다.
- Burst time이 짧은 순으로 스케줄링한다(preemptive인지 nonpreemptive에 따라 다르다).
- Preemptive 경우 중간에 더 짧은 프로세스가 interrupt할 수 있으며 매 클락마다 짧은 것을 선택하게 된다.
- Nonpreemptive 경우 arrival time 순으로 수행되고 이 후에 수행시간이 짧은 순으로 한다. 수행시간 같다면 먼저 하던 것을 계속 진행한다.
- waiting time은 프로세스가 ready에서 기다리는 시간이다.



##### Priority Scheduling

- Priority Number를 할당한다(작은 숫자가 우선순위이다).
- Preemptive : interrupt 우선순위 높은 순으로 한다.
- Nonpreemptive : 하던 프로세스를 진행한다.
- OS가 user program인지 kernel program인지에 따라 우선순위를 정해주거나 scheduler가 priority를 정해준다.
- Starvation problem
  - Priority가 낮은 프로세스가 높은 우선순위 프로세스의 등장으로 cpu를 할당받지 못한다.
  - Aging solution으로 해결한다.
- Aging solution
  - 클락마다 running이 되지 못하면 우선순위를 천천히 높여준다.
- arrival time이 같을 경우
  - priority가 높은 순으로 한다(작은 숫자).



#### Multitasking



##### Round Robin

- "RR" 이라고 부른다
- RR자체가 preemptive, 단 interrupt는 quantum q가 지나고 1번 수행된다.
- 원형 큐를 만들어놓고 수행한다.
- Time quantum q를 정하고(특정 프로세스가 정함) process가 q만큼 수행하고 빠지면서 수행되는 방식이다.
- 전체 시간을 1/n로 분리하고 q만큼의 시간을 주고 interrupt, (n-1)q만큼 수행한다.
- q가 작으면 context switching이 자주 일어나서 주의가 필요하다.

[CPU Scheduling](https://velog.io/@doyuni/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9COS-5.-Scheduling)



#### Multi-programming

- 하나의 프로세서가 하나의 프로세스를 수행하는 동안 다른 프로세스에 접근할 수있도록 하는 방법이다.
- 즉, 입출력 대기 시간 동안 다른 프로세스를 실행하는 것이다.
- 대기가 풀리면 다시 프로세서를 돌려 받는다.
- 멀티 프로그래밍은 CPU가 쉬지 않게 해주는 방법이며 멀티 태스킹은 동시에 여러 프로그램이 돌아가는 것 처럼 보여주는 방법이다.



## Kernel

운영 체제 중 항상 필요한 부분만 메모리에 올려서 사용하게 된다.

메모리에 상주하는 운영체제의 부분을 커널이라고 한다.

- 컴퓨터에 속한 자원들에 대한 접근을 중재하는 역할을 한다.
- 운영체제에서 가장 중요한 구성요소로 입출력을 관리하고 소프트웨어로부터 요청(System Call)을 컴퓨터에 있는 하드웨어(CPU, 메모리, 저장장치, 모니터)가 처리할 수 있도록 요청을 변환하는 역할을 한다. Shell을 이용하여 접근하는 것이 가능하다.



## Heap & Stack



### Code

실행할 프로그램의 코드가 저장되는 텍스트 영역이다. CPU는 코드영역에서 저장된 명령어를 하나씩 가져가서 처리한다.

- 함수는 code 영역에 저장될 것이다.



### Data

전역벼수, 정적변수, 배열, 구조체가 해당된다. 프로개름의 시작과 함께 할당되며 프로그램이 종료되면 소멸된다.



### Stack

함수의 호출과 관계되는 지역변수와 매개변수가 저장되는 영역이다. 함수의 호출과 함께 할당되며, 함수의 호출이 종료될 때 해제된다.

- Stack Overflow : stack이 커져서 heap 영역을 침범하는 것이다.



### Heap

사용자가 직접 관리할 수 있는 메모리 영역이다. 사용자에 의해 메모리 공간이 동적으로 할당되고 해제된다.

- Heap Overflow : heap이 커져서 stack 영역을 침범하는 것이다.



## Paging

페이징은 프로세스가 차지하는 물리적 메모리 공간이 비연속적이 되도록 허용하는 메모리 관리 기법이다.

- 페이징은 외부 단편화가 발생하지 않으며 별도의 Compaction 과정도 필요 없다.
- 다양한 크기의 메모리 덩어리(chunk)들을 backing store에 맞춰야 하는 문제를 해결한다.



### Basic Method

물리적 메모리를 고정된 크기의 프레임(Frame)으로 나누고 논리적 메모리를 동일한 크기의 페이지(Page)로 나누는 것이다.

![img](https://blog.kakaocdn.net/dn/PWRxh/btqNnwEXDoR/AsKvismwtWVVgHrfUMvx2K/img.png)

- CPU에 의해 생성된 모든 주소는 페이지 번호(Page Number, p), 페이지 간격(Page Offset, d)로 나뉜다. 페이지 번호는 페이지 테이블의 인덱스로써 사용된다.

![img](https://blog.kakaocdn.net/dn/CjJly/btqNkd0BQ7x/2WPjfhSwXRoZnZd8jbqS61/img.png)

- 페이지 테이블(Page Table)은 물리적 메모리의 각 페이지의 Base 주소 (시작 주소)를 저장하고 있다. 즉, 페이지와 대응하는 물리적 메모리의 프레임 주소를 가리킨다. 이 시작 주소를 페이지 간격과 합해 메모리 단위의 물리적 메모리 주소를 정의할 수 있다.
- 페이징 기법은 외부 단편화가 발생하지 않는다. 모든 사용 가능한 프레임은 그것을 필요로하는 프로세스에게 할당될 수 있기 때문이다.
- 내부 단편화는 발생할 수 있다. 프레임은 일정한 크기로 할당되기 때문이다.
- 내부 단편화를 위해 페이지 크기를 작게 만들 수 있지만 페이지의 크기가 줄어들수록 총 페이지의 갯수가 그만큼 늘어나고 페이지들을 관리하는 오버헤드가 증가한다. 그래서 일반적으로 4KB, 8KB로 정해져 있다.
- 운영체제는 반드시 물리적 메모리가 어떻게 할당되는지에 대한 내용을 알고 있어야 한다. 즉, 어떤 프레임이 할당되었고 어떤 프레임이 사용 가능한지에 대한 것이다. 이러한 정보는 프레임 테이블(Frame Table) 자료구조에 저장된다.
- 운영체제는 모든 논리적 주소가 대응되는 물리적 주소를 알고 있어야 하므로 각 프로세스의 페이지 테이블 복사본을 가지고 있어야 한다.



### TLB

TLB는 Key(또는 tag), Value의 두 가지 값을 저장한다. 어떤 항목이 메모리에 제시된다면 그 항목은 모든 key들에 대해 동시에 비교된다.

- TLB에서 페이지 번호를 발견했다면 (TLB Hit) 해당하는 프레임 번호는 즉시 사용가능하며 메모리 접근 가능하다.
- 페이지 번호가 TLB에 발견되지 않았다면 (TLB Miss) 그 페이지 테이블에 대한 메모리 참조가 만들어지며 TLB에 업데이트 된다.







[면접 질문 1](https://hyonee.tistory.com/95)



Ipc

socket

Paging
