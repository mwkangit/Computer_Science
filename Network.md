# Network



## TCP

TCP(Transmission Control Protocol)

- Connection Oriented : 클라이언트와 서버가 pkt을 전송하기 전 패키지를 보내서 서로의 연결 상황을 확인한다.(handshaking)
  - Reliable data transfer : 모든 데이터가 에러 없이 올바른 순서로 전송된다.(ack를 통해 신뢰 가능)
  - Flow Control : 속도를 제어하여 넘치는 것을 방지한다. Receiver Buffer와 관련있다. Transport Layer에서 다룬다.
  - Congestion Control : 라우터 버퍼가 넘치는 것을 막기 위해 송신자가 transmission rate을 control한다. 진행해야 하는 라우터가 다른 루트로 일을 진행하고 있을 때 이전 라우터의 output buffer에 잠시 pkt를 보관한다. 이때 delay가 발생하며 버퍼의 크기는 유한하여 버퍼가 가득 차있으면 나중에 온 pkt는 버린다. 이러한 상황에 라우터의 버퍼가 넘치지 않게 조절하는 것이다. Router Buffer와 관련있다. Transport Layer에서 다룬다.
  - Ex) `HTTP, FTP, SMTP`
- CRC를 통해 에러 발생 여부를 알 수 있다. 하지만 에러의 개수와 에러 발생 위치는 알 수 없다. CRC를 비트에 더한 후 짝수인지 홀수인지 판별한다.

- 3-Way Handshaking : 클라이언트가 SYN을 서버에 전송하고 기다린다(SYN_SENT). SYN을 받은 서버는 클라이언트에 SYN(통신 허용 flag) + ACK를 전송하고 기다린다(SYN_RECIEVED). 클라이언트는 서버에게 SYN + ACK를 잘 받았다는 ACK를 전송한다(ESTABLISHED). 이후 데이터 전송한다.
- 4-Way Handshaking : 세션을 종료하기 위해 수행되는 절차이다. 클라이언트가 연결을 종료하겠다는 FIN 플래그를 전송한다. 서버는 ACK를 보내고 통신이 끝날때까지 기다린다(TIME_WAIT). 서버가 통신이 끝났으면 연결이 종료되었다고 클라이언트에게 FIN 플래그를 전송한다. 클라이언트는 ACK를 전송한다.
  - 이때 서버의 ACK보다 FIN이 먼저 도착하면 ACK는 유실된다. 이러한 현상을 대비하기 위해 클라이언트는 서버로부터 FIN을 수신하더라도 일정시간(default = 240초) 동안 세션을 남겨놓고 잉여 패킷을 기다리는 과정을 거치며 이 과정을 TIME_WAIT라고 한다.



## UDP

UDP(User Datagram Protocol)

- Connectionless Service : 클라이언트가 받을 것이라고 바라며 서버는 pkt를 그냥 전송한다. Delay가 적지만 그만큼 신뢰도도 적다.
  - Ex) `Video / Audio`



## Sharing the Links

다수의 클라이언트가 같은 link/router 사용시 pkt는 나누어져야 한다.



### Circuit Switching

- 어떤 링크를 여러 클라이언트가 배타적으로 독점적으로 구간을 나눠서 사용하는 것이다.



#### FDM

Frequency-Division Multiplexing

- 하나의 자원을 주파수를 나눠서 이용하는 방법이다.
- 전체 시간을 다 사용하지만 자신이 사용할 수 있는 주파수가 한정되어 있다.



#### TDM

Time-Division Multiplexing

- 하나의 자원을 시간에 따라 공유하는 방법이다.
- 한정된 시간에 모든 주파수를 사용할 수 있다.
- 단점 : 처리할 일이 없다고 해서 다음 사용자로 빠르게 넘어가는 것이 아니다. 즉, 사용자가 처리할 일이 없으면 자원 낭비가 발생한다.



### Packet Switching

- 자원이 남을 때까지 기다린 후 자원이 생기면 사용한다.
- 이때 메시지는 pkt로 나누어지며 full transmission rate로 pkt을 전송한다.
- 장점 : 자원이 낭비될 확률이 적다.
- 단점 : delay가 발생할 수 있다.
- Circuit Switching 보다 Packet Switching을 사용한다.



## Delay

pkt 전송 시 delay를 다룬다.

- Transmission Delay : 링크로 pkt를 넣는데 걸리는 시간이다. L/R (R : Bandwidth, L : Packet Length)
- Queuing Delay : output link에서 전송을 위해 기다리는 시간이다.
- Propagation Delay : 첫 번째 비트가 출발해서 도달하는데 걸리는 시간이다. 물리적인 매체를 통과하는데 걸리는 시간이다. d/s (d : length of physical link, s : propagation speed in medium)(거리/속력)
- Processing Delay : pkt를 검사하고 retrasmission 하는 시간이다. 비트 에러를 체크하는 시간이다. 어느 링크로 전송할지 결정하기도 하며 헤더를 디코딩 하는데 걸리는 시간이다. 즉, 목적지가 어디인지 라우터가 디코딩하는 시간으로 호스트의 컴퓨터 성능에 좌우한다.
- D = dtrans + dqueue + dprop + dproc (D : 전체 delay)

- 보통 Transmission Delay, Propagation Delay만 다룬다.
- HostA -> Router -> HostB 일때
  - 1개 pkt 전송할 때
    - D =  tp1 + tp2 + 2td (HostA에서 Router로 갈 때 발생하는 td는 포함하지 않는다)
  - n개 pkt 전송할 때
    - D = 2td + (n-1)td + tp1 + tp2 (처음 후의 pkt는 이미 라우터로 전송되었으므로 td만큼 시간이 걸린다)



## OSI 7 Layer

1~7 Layer로 구성되어 있으며 Physical Layer, DataLink Layer, Network Layer, Transport Layer, Session Layer, Presentation Layer, Application Layer로 구성되어 있다.

통신이 일어나는 과정을 단계별로 파악하기 위함과 통신 과정 중에 특정한 곳에 이상이 생길 경우에 다른 단계의 장비 및 소프트웨어 등을 건드리지 않고 통신 장애를 일으킨 단계에서 해결할 수 있기 때문에 나눈 것이다. 즉, 독립적으로 관리하기 위함이다.

송신 시 7~1순서로 헤더가 붙으며 수신 시 1~7 순서로 헤더를 읽는다.

Cross-Layer Optimization : 연상의 최적화를 위해 Layer 벽을 허무는 것이다.

[OSI 7 Layer](https://onecoin-life.com/19)



### Physical Layer

- 실제 장치를 연결하기 위한 전기적 및 물리적 세부 사항을 정의한 계층이다.
- 데이터를 전달만 할 뿐 전송하려는(또는 받으려는) 데이터가 무엇인지, 어떤 에러가 있는지 등은 전혀 신경 쓰지 않고 단지 데이터 전기적인 신호로 변환해서 주고받는 기능만 한다.
- Ex) `케이블 종류, 무선 주파수 링크, 전압`



### Datalink Layer

- 장치 간 신호를 전달하는 물리계층을 이용하여 네트워크 상의 주변 장치들 간의 데이터를 전송하는 역할을 한다.
- 물리계층을 통해 송수신되는 정보의 오류와 흐름을 관리하여 안전한 정보의 전달을 수행할 수 있도록 한다.
- 통신에서의 오류도 찾아주고 재전송도 하는 기능을 가지고 있으며 맥 주소(Mac Address)를 가지고 통신한다. 맥 주소는 네트워크에 접속하는 모든 장비가 통신을 위해 사용하는 물리적인 주소이다.
- 포인트 투 포인트(Point to Point)간 신뢰성 있는 전송을 보장하기 위해 CRC 기반의 오류 제어와 흐름 제어가 필요하다.
- 이 계층에서 전송되는 단위를 프레임이라고 한다.
- 주소 할당 : 물리계층으로부터 받은 신호들이 네트워크 상의 장치에 올바르게 안착할 수 있게 한다.
- 오류 감지 : 신호가 전달되는 동안 오류가 포함되는지 감지 오류가 있다면 해당 데이터를 폐기한다.
- Ex) `브리지, 스위치`



### Network Layer

- 경로를. 선택하고 주소를 정하고 경로에 따라 pkt를 전달해주는 것이 이 계층의 역할이다.
- 라우팅, 흐름 제어, 세그멘테이션, 오류 제어, 인터 네트워킹 등을 수행한다.
- IP를 네트워크 관리자가 직접 할당하는 구조이며 계층적이다.



### Transport Layer

- TCP, UDP, Port를 부여하는 계층이다.
- 양 끝단의 사용자가 신뢰성 있는 데이터를 주고받게 하여 상위 계층이 데이터 전달의 유효성이나 효율성을 신경 쓰지 않게 해주는 계층이며 시퀀스 넘버 기반의 오류 제어 방식을 사용한다.
- 특정 연결의 유효성을 제어하고 일부 프로토콜은 상태 개념이 있고(stateful), 연결 기반(connection oriented)이다.
- 전송 계층은 패킷들의 전송이 유효한지 확인하고 전송 실패한 패킷들을 다시 전송한다는 것이다.



### Session Layer

- 양 끝단의 응용 프로세스가 통신을 관리하는 방법을 제공하는 계층이다.
- 통신 연결이 손실되는 경우 연결 복구 시도가 가능하며 연결 시도 중 장시간 연결이 되지 않았다면 세션 계층의 프로토콜이 연결을 닫고 다시 연결을 시도한다.
- 세션 계층은 TCP/IP 세션을 만들고 없애는 책임을 가진다.
- 세션 계층은 동기화를 진행한다.
  - 전이중 통신(Full Duplex)
    - 두 대의 단말기가 데이터를 송수신하기 위해 동시에 각각 독립된 회선을 사용하는 통신 방식이다.
      - Ex) `전화망, 고속 데이터 통신`
  - 반이중 통신(Half Duplex)
    - 한 쪽이 송신하는 동안 다른 쪽에서 수신하는 통신 방식으로 전송 방향을 교쳬한다.
    - Ex) `마스터 슬레이브 방식의 센서 네트워크`



### Presentation Layer

- 코드 간 번역을 담당하는 계층이다.
- 데이터 형식상 차이를 다루는 부담을 덜고 MIME(전자 우편을 위한 인터넷 표준 포맷) 인코딩이나 암호화 등의 동작이 이 계층에서 이루어진다.
- 즉, 데이터를 알맞은 형식으로 변환하는 작업을 하는 계층이다. 이 계층은 응용프로그램이나 네트워크를 위해 데이터를 "표현" 하는 것이다.
- Ex) `EBCDIC -> ASCII, Text인지 GIF인지 JPG인지`



### Application Layer

- 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행하는 계층이다.
- 사용자에게 직접적으로 보이는 부분이다.
- 응용 프로세스 간의 정보 교환을 담당한다.
- 최종 목적지로서 `HTTP, FTP, SMTP, POP3, IMAP, TELNET`등 프로토콜이 있다.
- 프로토콜을 준수하여 응용 프로그램에 응용 서비스를 출력하는 것이다.
- Ex) `Chrome, Firefox, Skype, Outlook, Office`



## Application

### HTTP

Text를 전송하는 프로토콜이다.

HTML은 객체의 주소를 담고 있다.

TCP를 사용하며 Stateless로 과거의 클라이언트의 요청과 정보를 저장하지 않는다.



#### Non-Persistent HTTP (1.0)

- Index File : 각 object들의 address만을 담고 있다.
- to : trasmission time for index file(html).
- ti : transmission time for object i.
- D = 2RTT + to + sig(2RTT + ti) (모든 객체마다 TCP Request, HTTP Request를 별도로 해야한다)



#### Persistent HTTP (1.1)

- 하나의 TCP 연결로 다수의 객체를 송수신 할 수 있다.
- D = 2RTT + to + sig(RTT + ti)



##### With Piplining

- 클라이언트는 객체를 마주하면 바로 전송한다.

- D = 2RTT + to + RTT + sig(ti)

##### Without Piplining

- 이전 응답이 정상적으로 수신 되었을 때 새 요청을 수행한다.
- D = 2RTT + to + sig(RTT + ti)



### DNS

- Hostname을 IP 주소로 변환하는 작업을 한다.

- DNS는 UDP로 작동하며 53 포트를 이용한다.
- 하나의 DNS 서버로 수행하면 문제점이 있다.
  - 트래픽이 너무 몰린다.
  - DB가 멀리있다.
  - 문제가 생겼을 때 유지보수가 힘들다.
- 분산 계층 DB로 해결한다.
  - Root DNS Server : 전 세계에 13개 서버가 존재하며 최상위 계층이다.
  - Top Level Domain(TLD) : 상위 도메인으로 `com, org, net, edu, gov, uk, fr, ca, kr` 등이 있다.
  - Authoritative DNS Server(책임 DNS Server) :  Hostname을 관리한다.
- 순서는 8단계로 이루진다.
  - Host -> Local DNS Server -> Root DNS Server -> Local DNS Server -> TLD DNS Server -> Local DNS Server -> Authoritative DNS Server - > Local DNS Server -> Message
- Recursive Query : 즉각적인 응답을 얻을 수 없는 query로 Host -> Local DNS Server에 해당된다.
- Iterative Query : 즉각적인 응답을 얻을 수 있는 query로 대부분에 해당된다.
- 캐싱을 통해 Local DNS Server에서 Root, TLD 서버에 가지 않고 생략될 수 있다.



## Transport

전송계층은 데이터 전송 보장을 위해 다양한 방식의 프로토콜을 사용한다.



### Stop-And-Wait

- ARQ프로토콜의 일종이다.

- PKT, ACK에 번호를 붙여서 어떤 번호를 붙여서 메시지를 식별할 수 있게 한다.

  PKT0 -> ACK0(RN1) -> PKT1 -> ACK1(RN0)

- Timeout이 발생하면 다시 PKT를 전송하며 ACK Timeout 시 ACK도 재전송하며 중복 된 PKT는 무시한다.

- RN이 소실되면 클라이언트가 PKT를 재전송한다(Lost PKT).

- 클라이언트가 받고자 하는 RN이 아닐 경우 무시한다(Premature Timeout).

- 단점 : ACK 혹은 NAK을 받을 때까지 다음 프레임을 받을 수 없으므로 전송 효율이 좋지 않다.



### Go-Back-N

- 슬라이딩 윈도 프로토콜이다. 즉, 윈도를 옮기면서 앞부터 채워나가는 것이다.
- 파이프라이닝 방법이다.
- 윈도의 크기(N) 만큼 한번에 PKT를 전송하는 프로토콜이다.
- mod란 PKT에 SN을(Sequence Number)을 부여하는 범위이다.
- mod m >= n+1
- PKT2만 수신단에 도착하지 않았을 때 수신단은 RN3 이후의 ACK를 전송하지 않으며 송신단은 ACK가 없어서 PKT2부터 다시 보낸다.
- 송신단이 RN1, RN2를 받지 못하고 RN3를 받으면 앞은 무시하고 PKT3부터 정상 전송한다(Cumulative Acknowledge).
- 단점 : 패킷 하나의 오류 때문에 많은 패킷들을 재전송 하므로 많은 패킷을 불필요하게 재전송하는 경우가 발생한다.
- 가장 많이 사용한다.



### Selective Repeat

- ARQ프로토콜 일종이다.
- mod m >= 2n
- Go-Back-N과 다르게 ACK를 받지 못한 PKT만 재전송한다.
- Cumulative Acknowledge 아니다.
- 버퍼의 크기는 윈도 크기이다.
- ACK를 모두 버퍼에 담은 후 이전에 오류가 발생한 PKT에 대한 ACK가 도착하면 상위 Layer로 보낸다.
- TCP는 Go-Back-N, Selective Repeat의 결합 형태이다.



### Fast Transmission

- 오류 이후 3개의 ACK가 도착하면 Timeout 되기 전에 loss로 판단하여 다시 PKT를 전송한다.



### Flow Control

- Receiver Buffer와 관련있다.
- 윈도 사이즈를 적절하게 설정하여 loss 없이 PKT를 받을 수 있게 한다.



### Congestion Control

- 버퍼 사이즈를 잘 조절하지 않으면 buffer overflow로 loss가 발생하며 여유로운 라우터를 찾다가 너무 돌아서 전송되어 delay가 발생한다.



#### Fairress

- Congestion Window를 1씩 늘리면서 데이터를 받다가 loss 되면 윈도 크기를 1/2한다.
- 즉, 한쪽은 점점 더 많은 데이터를 전송하다가 수신쪽에서 loss가 발생한는 것이다.
- 반복 수행하면 최종 수렴 지점인 중간으로 수렴한다.



### Slow Start

- Congestion Control, Slow Start 중 골라서 사용한다.

- Threshold를 설정하여 threshold까지는 지수적으로 con.win이 증가한다.
- Threshold부터는 선형으로 con.win이 증가하며 loss 발생 시 threshold = con.win / 2, con.win = con.win / 2 이다.
- Timeout 발생 시 threshold = con.win / 2, con.win = 1이다.



## Network

네트워크 계층은 라우터와 밀접한 관계를 가지고 있다.

어떤 라우터를 거쳐서 목적지까지 도달할 것인지 결정한다.

- 두 가지 타입의 서비스를 제공한다.

  - Connectionless : 목적지만 지정되어 있고 라우터에서 알아서 찾아간다. Forwarding Table이 IP Address에 의해 결정된다(즉, 목적지로 결정된다).

  - Connection-Oriented : 중간에 거치는 노드까지 모두 헤더에 지정되어 있다. Virtual Circuit Number을 사용하여 표현한다.

- Forwarding : 라우터 Input에서 알맞은 PKT를 알맞은 라우터 Output으로 옮긴다.

- Routing : 목적지까지의 경로를 지정하는 것이다.

- Forwarding Table : 헤더의 비트를 분석하여 알맞은 서브넷에 포워딩한다. 모든 라우터는 Forwarding Table을 가진다. Incoming Interface, Incoming VC #, Outgoing Interface, Outgoing VC #로 이루어져 있다. 라우터에서 헤더의 VC를 바꿔서 다음 목적지로 전송한다.

- VC Network는 각각 connection마다 update 된다. 즉, 시작 ~ 목적지 설정되면 update 된다. 하지만 Datagram Network는 5 ~ 10분에 한번 update된다.

- VC Network는 IP가 아닌 ATM()에 사용한다. VC는 모든 것을 준비하기 때문에 전반적인 효율성이 떨어져서 IP에는 안쓰인다. 루트가 정해져서 최적의 루트로 높은 신뢰와 낮은 delay를 자랑한다. ATM은 비동기 통신을 하여 매우 빠르다(경로가 정해져 있어서 가능하다). 또한, ATM은 53바이트의 고정 셀 크기를 가져서 처리하기 편하며 속도도 빠르다.

- Datagram Network는 목적지만 있으며 IP에 사용한다. 몇 분마다 한번씩 Forwarding Table을 update한다(Load Balancing Network). PKT 내부에 timer을 둬서 일정시간 내에 목적지에 도달하지 못하면 PKT를 자폭시킨다. 목적지까지 도달하지 못하면 misrouting이라고 한다.

- 즉, 결론적으로 TCP/IP는 신뢰도가 높은 프로토콜일 뿐이다. 통신은 Datagram Network로 통신한다.

[ATM](https://m.cafe.daum.net/kjdhwtl/H32e/3)



### IP Addressing

- Host와 router interface가 판별 가능한 32 비트이다.
- 앞의 24bit는 서브넷 구분을 위한 bit이며 뒤의 8bit는 host를 구분하기 위한 bit이다.
- Subnet : 라우터를 통과하지 않고 서로 연결 가능한 host들이다.
- Classful Addressing
  - A : 0.0.0.0 ~ 127.0.0.0, 00000000.x.x.x ~ 01111111.x.x.x(2진수)로 24bit은 host 구분한다. 128개 네트워크, 16777216개 컴퓨터를 가진다. 10.0.0.0 ~ 10.255.255.255(사설)
  - B : 128.0.0.0 ~ 191.255.0.0, 10000000.x.x.x ~ 10111111.x.x.x(2진수)로 16bit은 host를 구분한다. 16384개 네트워크, 65532개 컴퓨터를 가진다. 172.16.0.0 ~ 172.31.255.255(사설)
  - C : 192.0.0.0 ~ 223.255.255.0, 11000000.x.x.x ~ 11011111.x.x.x(2진수)로 8bit은 host를 구분한다. 2097152개 네트워크, 256개 컴퓨터를 가진다. 192.168.0.0 ~ 192.168.255.255(사설)
  - D : Multicast Address로 224.0.0.0 ~ 239.255.255.255이다.
  - E : Reserved로 240.0.0.0 ~ 247.255.255.255이다.
- CDIR(Classless Inter-Domain Routing)
  - "IP주소/24"이면 앞의 24bit 이후에 오는 4번째 옥텟을 전부 사용할 수 있다는 표현이다.
  - Subnet Part : High Order Bits (MSB)
  - Host Part : Low Order Bits (LSB)
  - CIDR는 급격히 부족해지는 IPv4 주소를 보다 효율적으로 사용하게 해준다.
  - 접두어를 이용한 주소 지정 방식을 가지는 계층적 구조를 사용함으로써 인터넷 광역 라우팅의 부담을 줄여준다.

[CDIR](https://velog.io/@ragnarok_code/CIDR%EC%9D%B4%EB%9E%80)



### NAT

- 공유기에 public IP를 부여하고 공유기에 연결된 기기에 private IP를 부여하여 IP의 사용량을 늘리는 것이다.
- 즉, 비공인(사설, local) 네트워크 주소를 사용하는 망에서 외부의 공인망(public, 인터넷)과 통신을 위해서 네트워크 주소를 변환하는 것이다.

[IP Addressing ~ NAT](https://ws-pace.tistory.com/139)











SMTP,FTP 원리

