# 개발 방법론



## TDD(테스트 주도 개발)

- 반복 테스트를 이용한 소프트웨어 방법론으로 작은 단위의 테스트 케이스를 작성하고 이를 통과하는 코드를 추가하는 단계를 반복하여 구현한다.
- 애지일 방법론 중 하나인 eXtream Programming기반 설계
  - XP - 미래에 대한 예측을 최대한 하지 않고, 지속적으로 프로토타입을 완성하는 애자일 방법론 중 하나이다. 추가 요구사항이 생기더라도 실시간 반영가능
- 실패하는 테스트코드 작성 -> 테스트 코드 성공을 위한 실제 코드 작성 -> 리펙토링 실행

- TDD 이용안하는 일반적인 개발방식은 오히려 나중에 발생하는 오류 해결로 테스트 비용이 증가하며 오히려 프로젝트의 완성시간이 단축된다. but 일반적으로 시간 10~30%느리며 납기일 준수가 목적인 SI프로젝트는 잘 이용안한다.
- 객체 지향적인 코드생산 - 모듈화, 재설계 시간을 단축시킬 수 있는 코드, 디버깅 시간이 단축되는 코드
- 테스트 코드 작성 -> 테스트 코드 실행(이때 테스트 성공하면 구현하지도 않은 부분의 코드의 성공이므로 버그 찾아야 한다) -> 실패한 테스트 코드를 위한 최소한 코드 구현 -> 코드 리펙토링



## BDD(행동 주도 개발)

- TDD와 비슷하지만 테스트 자체가 아닌 비즈니스 요구사항에 집중하여 테스트 케이스를 개발한다.
- 즉, 테스트 케이스 자체가 요구사항이 되도록 개발한다.
- TDD 결합으로 시나리오 테스트까지 한다(어디서부터 테스트, 어떤것을 테스트, 얼만큼 테스트 등).
- 시나리오는 어디서부터 테스트를 시작할지, 어떤 것을 테스트하고 어떤 것을 하지 않을지, 한 번에 얼마만큼을 테스트할지, 테스트에 어떤 이름을 붙일지, 테스트가 왜 실패했는지 등에 대한 고민을 해결해준다.
- "should do something"라는 식의 문장으로 작성해 "행위"를 위한 테스트에 집중
- TDD보다는 좀 더 큰 단위로 개발을 진행한다.
- 코드를 작성하기 전에 코드가 수행할 행위(Behavior)(시나리오)에 대한 명세를 먼저 작성해야 한다.



## DDD(도메인 주도 개발)

- 순수한 도메인의 모델과 로직에 집중하는 것이다.
- **즉, 일반적으로 많이 사용하는 데이터 중심의 접근법을 탈피하여 순수한 도메인의 모델과 로직에 집중한다.**
- 상호가 이해할 수 있도록 모든 문서와 코드가 동일한 표현과 단어로 구성되게 한다.
- **분석 작업과 설계 그리고 구현까지 통일된 방식으로 커뮤니케이션 가능하다.**
- 도메인 모델부터 코드까지 항상 함께 움직이는 구조의 모델을 지향한다.
- 도메인이란, SW로 해결하고자 하는 문제의 영역, 즉 만들고자 하는 서비스를 잘게 쪼개놓은 단위.



- 도메인은 "정보와 활용의 영역"을 말하며 어플리케이션 로직의 기준으로 활용될 수 있다. "회원"과 같은 사항이 도메인이다.
- DDD는 데이터가 아닌 도메인을 중심으로 설계하는 것이다.
  - 핵심 도메인과 그 기능에 집중한다.
  - 도메인의 모델을 정교하게 구축한다.
  - 어플리케이션 모델을 발전시키고 새롭게 생기는 도메인 관련 이슈를 해결하기 위해 도메인 전문가와 연락한다.
- Context란 특정 객체 혹은 상황이 벌어지는 주변 환경이다. 피자가 그릇에 있는지 바닥에 있는지에 따라 유료, 무료로 분류되는 것이라고 할 수 있다. Model에 관한 문장은 context 안에서만 이해될 수 있다.
- Strategic Design이란 같은 사물이나 행동 양상이 벌어지는 상황에 집중하여 디자인하는 것이다. 주택을 설계하는 과정이라고 생각하면 된다.
- Domain은 여기서 집 전체를 말한다.
- Subdomain은 domain의 부분 집합으로 헛간, 농장, 수영장 등을 말한다.
- Bounded Context는 subdomain의 문맥적 상황이며 위 context 예시와 유사하다. Context에 대한 구체적인 범위이다.
- Domain Model은 subdomain의 구체적인 형상을 나타낸 것이다. Domain의 특정 양상을 묘사하는 추상화 시스템으로 도메인과 관련된 문제를 해결하는데 사용한다.
- Ubiquitous Language는 domain model을 둘러싼 언어구조를 말하며 팀 전체각 각각의 업무 파트에서 공통적으로 사용될 수 있는 공통된 어휘이다.
- Context Map은 bounded context들 사이의 관계를 말한다.

[TDD BDD DDD](https://m.blog.naver.com/rkdudwl/221973507455)

[DDD2](https://steemit.com/kr/@frontalnh/domain-driven-design)



# 객체 지향 설계



## SOLID

### SRP

- 단일 책임 원칙으로 모든 클래스는 각각 하나의 책임을 가져야 한다. 클래스는 그 책임을 완전히 캡슐화 해야한다. 

### OCP

- 개방-폐쇄 원칙으로 확장에는 열려있고 수정에는 닫혀있는 기존의 코드를 변경하지 않으면서(closed) 기능을 추가할 수 있도록(open) 설계 되어야 한다는 원칙이다(인터페이스화 같다).

### LSP

- 리스코프 치환 원칙으로 자식 클래스는 언제나 자신의 부모 클래스를 대체할 수 있다는 원칙이다. 즉, 부모 클래스가 들어갈 자리에 자식 클래스를 넣어도 계획대로 잘 작동해야 한다(다형성 고려 인터페이스).

### ISP

- 인터페이스 분리 원칙으로 한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다. 하나의 일반적인 인터페이스보다 여러개의 구체적인 인터페이스가 낫다.

### DIP

- 의존 역전 원칙으로 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 것이다. 한마디로 구체적인 클래스보다 인터페이스나 추상 클래스와 관계를 맺으라는 것이다.

[SOLID1](https://hckcksrl.medium.com/solid-%EC%9B%90%EC%B9%99-182f04d0d2b)

[SOLID2](https://dev-momo.tistory.com/entry/SOLID-%EC%9B%90%EC%B9%99)



# Java 8, Java 11



## Java 8

- 람다 표현식의 탄생
  - 메소드를 하나의 식으로 표현한 것을 말한다. 익명함수라고도 불린다.
  - 가시성이 좋아진다.
- Stream API
  - 컬렉션의 저장 요소를 하나씩 참조해서 람다식으로 처리할 수 있도록 해주는 내부 반복자이다.
- Optional 지원
  - Optional을 통해 null에 대한 참조를 안전하게 할 수 있다.
  - Optional을 통해 NPE를 얻을 상황을 손 쉽게 처리할 수 있다.
- Interface Default Method 탄생
  - 구현을 넣을 수 있으며 굳이 오버라이딩 하지 않아도 된다.

- Garbage Collector
  - Parallel GC 사용한다.



## Java 11

- Javac를 통해 컴파일 하지 않고 바로 java파일 실행 가능하다.
- HTTP Client 기능 표준화로 전반적인 HTTP API 성능 향상했다.
- Garbage Collector
  - G1 GC 사용한다.

[Java 8, Java 11 1](https://livenow14.tistory.com/81)

[Java 8, Java 11 2](https://steady-coding.tistory.com/598)



# Sort

- Arrays.sort()
  - 듀얼 피봇 퀵정렬(Dual-Pivot QuickSort)를 이용한다.
  - 피봇을 2개를 두고 3개의 구간을 만들어 퀵정렬을 한다.
- Collections.sort()
  - Tim 정렬을 이용하며 삽입정렬, 병합 정렬을 결합한 형태이다.
  - Java 7 부터 사용한다.
- Arrays.sort() vs Collections.sort()
  - 참조 지역성 원리 - 동일한 값 또는 해당 값의 근처에 있는 스토리지 위치가 자주 엑세스 되는 특성이다. 캐싱 전략에 영향을 미친다.
  - Array는 연속적인 주소이므로 참조 지역성 원리에 좋다.
  - Collection의 arraylist는 메모리간 인접하지만 linkedlist는 참조 인접성이 좋지 않아서 tim 정렬을 사용한다.
- Heap sort는 최선의 경우 O(n), 최악의 경우 O(nlogn)이지만 참조 지역성이 좋지 않다. 즉 C * nlogn + a 에서 C 가 크게 나온다.
- Merge sort는 인접한 덩어리를 병합하기 때문에 참조 지역성의 원리를 만족한다. 하지만 입력 배열 크기만큼의 메모리를 추가로 사용한다는 단점이 있다.
- Quick sort는 pivot  주변에서 데이터의 위치 이동이 빈번하게 발생하기에 참조 지역성이 좋으며 메모리를 추가로 사용하지 않는다.
- Tim sort는 삽입 정렬로 참조 지역성 원리를 만족하고 병합 정렬로 빅오의 속도를 높이는 것이다.

[Sort1](https://sabarada.tistory.com/138)

[Sort2](https://d2.naver.com/helloworld/0315536)



# Design Pattern

소프트웨어 설계시 이후에 재사용하기 좋은 형태로 설계하는 방법이다.



## 생성

- 싱글톤 패턴
  - 전역 변수를 사용하지 않고 객체를 하나만 생성하도록 하며 생성된 객체를 어디서든 참조할 수 있도록 하는 패턴이다.
- 빌더 패턴
  - 객체를 생성하는 클래스와 표현하는 클래스를 분리하여 동일한 절차에서도 서로 다른 표현을 생성하는 방법을 제공한다.
  - 생성자만 사용할 때 발생할 수 있는 문제를 개선한다.
  - 필수 필드는 생성자로 주입하며 optional한 필드는 빌더 패턴으로 주입한다.



## 구조

- 프록시 패턴
  - 객체를 직접적으로 참조하는 것이 아닌 해당 객체를 대항하는 객체를 통해 대상 객체에 접근하는 방식이다.
  - 연관관계 시 Lazy 가 있다.



## 행위

- 옵저버 패턴
  - 객체들 사이에 1 : N 의 의존관계를 정의하여 어떤 객체의 상태가 변할 때, 의존 관계에 있는 모든 객체들이 통지받고 자동으로 갱신될 수 있게 만드는 패턴이다.

[Design Pattern](https://coding-factory.tistory.com/708)



# Agile

- 빠르게 취하고 낭비없게 만든는 다양한 방법론을 말한다.
- 앞을 예측하지 않고 일정한 주기를 가지고 계속 검토해 나가며 필요할 때마다 요구사항을 더하고 수정하는 방식을 한다.
- 경험 기반 프로세스이며 적시(just-in-time)설계
- 코드강조
- 팀워크 중시
- 장점
  - 프로젝트 계획에 걸리는 시간 최소화
  - 버그를 쉽고 빠르게 발견 가능
  - 수정과 변경에 유연
  - 즉각적인 피드백으로 프로토타입 모델 빠른 출시
- 단점
  - 확정되지 않은 계획 및 요구사항으로 인한 반복적인 유지보수 작업이 많다.
  - 개인이 아닌 팀이 중심이어서 공통으로 해야할 작업이 많다(회의).

## Scrum

- 스프린트 - 크지 않은 태스크를 적당한 기간동안 집중해서 전력질주하듯 업무를 수행하는 것이다. 스크럼 내부에 있으며 계획 회의 부터 제품 리뷰까지 기간이 1스프린트이다.
- 스프린트 백로그 - 스프린트 목표에 도달하기 위해 필요한 작업 목록
- 스크럼 회의 - 날마다 진행되는 미팅(어제한일, 오늘할일, 장애현상)
- 제품 책임자(product owner) - 제품 백 로그를 정의하여 우선순위를 정해 준다.
- 스크럼 마스터(Scrum Master) - 일반적인 관리를 수행하는 프로젝트 관리자들과는 달리 팀원을 코칭하고 프로젝트의 문제 상황을 해결하는 역할을 하며, 제품 책임자는 스프린트 목표와 백로그 등의 결정에 있어 중심이 되는 상위 관리자이다.



# Thread Safe

Multi Thread 프로그래밍에서 여러 Thread로부터 어떤 method나, variable, object에 동시에 접근이 이루어져도 프로그램의 실행에 문제가 없는 것을 말한다.

- HashMap 대신 ConcurrentHashMap 사용
- Long 대신 AtomicLong 사용
- StringBuilder 보다 StringBuffer이 Thread Safe 하다.
- 빈에 변할 수 있는 변수가 있다면 Thread Safe하지 않다. 이때 지역변수로 사용하거나 scope을 prototype으로 하여 singleton이 아닌 새로운 객체 생성되게 한다. 아니면 읽기 전용으로 만들어서 setter을 삭제해야 한다.

[Thread Safe](https://velog.io/@cateto/Java-Thread-Safe%EB%9E%80)



# AOP & Filter & Interceptor



## AOP

AOP는 관점 지향 프로그래밍으로 객체를 추상화하여 모듈화 하는 것이다.

- 주소가 아닌 파라미터, 어노테이션 등으로 대상 설정이 가능하다.
- 공통처리에 사용되며 로깅이나 실행시간 체크 시 이용한다.



## Filter

자바 표준을 활용하며 웹 컨테이너가 관리한다.

- Dispatcher Servlet 전에 호출된다.
- 보안, 인증, 인가, 압축, 인코딩 시 사용된다.



## Interceptor

스프링이 제공하는 기술이며 스프링 컨테이너가 관리한다.

- Dispatcher Servlet 이후에 호출된다.
- 클라이언트의 요청과 관련되어 전역적으로 처리해야 하는 작업들을 처리해야 한다.
- 컨트롤러로 넘겨주기 위한 정보를 가공한다.

[AOP & Filter & Interceptor](https://www.saichoiblog.com/springboot-filterling/)





# MSA

단일 프로그램을 각 컴포넌드 별로 나누어 작은 서비스의 조합으로 구축하는 방법이다. 서비스를 모듈화 한다고 생각하면 된다.



## Monolithic

전체 어플리케이션이 하나로 되어있는 구조이다.

![leh_3](http://clipsoft.co.kr/wp/wp-content/uploads/2020/06/leh_3.png)

- 하나의 덩어리로 된 구조이다.
- 각 컴포넌트들이 함수로 호출되기 때문에 성능에 제약이 덜하고 운영 관리가 용이하다.
- 작은 볼륨의 시스템을 개발할 때는 유용하지만 시스템이 커지기 시작하고 여러 컴포넌트들이 더해지면 문제가 발생한다.
- 단점
  - 빌드 / 테스트 시간이 길어진다.
    - 작은 수정에도 시스템 전체를 빌드해야 하며 테스트 시간도 길어진다.
    - CI / CD 시 오래 걸린다.
  - 선택적 확장이 불가능하다.
    - 이벤트로 인해 서비스 접속량이 폭증할 경우 프로젝트 전체를 확장해야 한다.
  - 하나의 서비스가 모든 서비스에 영향을 준다.
    - 이벤트 서비스에 트래픽이 몰려 해당 서버가 죽게 된다면 다른 모든 서비스 역시 마비된다.



## MSA

작은 서비스를 기준으로 구성되는 구조이다. 서비스 지향적 아키텍쳐 스타일이다.

![leh_4](http://clipsoft.co.kr/wp/wp-content/uploads/2020/06/leh_4.png)

- 장점

  - 각 컴포넌트는 서비스 형태로 구현되고 API를 이용하여 타 서비스와 통신한다.
  - 각 서비스는 독립된 서버이므로 독립된 배포를 한다.
  - 각 컴포넌트가 독립된 서비스로 개발되어 있기 때문에 부분적인 확장이 가능하다(이벤트 서버만 스케일링).

- 단점

  - 모놀리틱 아키텍처는 서비스간 호출이 하나의 프로세스 내에서 이루어지기 때문에 속도가 빠르지만 MSA 경우 서비스간 호출을 API 통신을 이용하기 때문에 속도가 느리며 통신에 사용하기 위해 값을 데이터 모델로 변환시켜주는 오버헫가 발생하기도 한다.

- 특징

  - 데이터분리

    - 데이터 저장 시 하나의 DB에 중앙 집중화를 하지 않고 서비스 별 별도의 데이터 베이스를 사용한다.
    - 같은 DB를 사용하더라도 나누어서 사용하게 된다.
    - 장점
      - 데이터가 분산되어있기 때문에 다른 서비스 컴포넌트에 대한 의존성이 없이 서비스를 독립적으로 개발 및 배포 / 운영 할 수 있다.
    - 단점
      - 다른 컴포넌트의 데이터를 API통신을 통해 가져와야 하기 때문에 성능상 문제가 발생할 수 있다.
      - 트랜잭션으로 쿼리를 묶을 수 없는 문제가 발생한다.

  - API Gateway

    - MSA의 문제점 중 하나는 각 서비스가 다른 서버에 분리 배포되어있기 때문에 서버 URL이 각기 다를 수 밖에 없다.
    - 이때 API Gateway는 API 서버 앞 단에서 모든 API 서버들의 End-Point를 단일화하여 묶어주는 역할을 한다.
    - 거미줄처럼 복잡한 서비스간의 API호출 구조도 단순화 시킨다.
    - 라우팅, 로드밸런싱, 인증 역할도 수행한다.

  - 팀의 변화

    - 기존 모놀리틱의 팀 모델은 역할 별로 나누어진 모델로 팀을 구분했다.
    - 이러한 팀 모델은 인력 관리와 운영에 유연성을 부여하지만 팀 간의 커뮤니케이션이 원활하지 않고 협업에 걸리는 시간이 지연되는 경우가 많다.
    - 기획, UX, 개발, 인프라 운영 팀이 존재하며 각각 독립적이다.

    ![leh_5](http://clipsoft.co.kr/wp/wp-content/uploads/2020/06/leh_5.png)

    - MSA에서는 서비스 별로 팀을 나누고 서비스 기획에서부터 설계 개발 운영이 팀 내에서 이루어지기 때문에 다른 팀에 대한 의존성이 사라진다.
    - 역할별 요청과 피드백이 빨라지고 유연하고 지속적인 운영과 개발이 함께된다.
    - 하지만 각 팀의 역할 담당자는 기본적인 업무 성숙도를 가지고 있어야 하며 개발팀은 운영팀의 인프라 핸들링까지 해야한다(AWS같은 클라우드 발달로 가능해졌다).

    ![leh_6](http://clipsoft.co.kr/wp/wp-content/uploads/2020/06/leh_6.png)



## Spring Cloud Eureka

Spring Cloud는 마이크로서비스 아키텍처를 지원하는 스프링부트를 기반으로 하는 프레임워크이다.

- Spring Cloud Config Server라는 외부 저장소에 환경설정을 설정한다. 이때 외부 저장소는 Git이 된다.
  - 이를 사용하면 각각의 마이크로서비스의 내용이 변경된다고 해도 다시 빌드하지 않아도 되고 외부저장소에 있는 환경설정만 바꿔준다면 연결되어 있는 마이크로 서비스들의 환결설정이 자동으로 변경되어 유지보수에 좋아진다.
  - 사용 이유
    - 첫째, 마이크로서비스의 어떠한 설정(환경변수값, Spring cloud 설정 등)이 변경되었을때 서버 재시작 없이 동적으로 적용하기 위해서이다.
    - 둘째, 마이크로서비스가 배포될때 제반 설정값들을 배포 대상 환경(개발계, 검증계, 운영계 등)에 맞게 적용하기 위함이다.
    - 셋째, 마이크로서비스를 Stateless하게 개발하기 위해서입니다. Stateless하게 만들어야 스케일링(마이크로서비스 인스턴스 서버 - 즉, 컨테이너의 증감)과 부담없는 재시작이 가능하기 때문이다.

![img](https://blog.kakaocdn.net/dn/tsc82/btq7ixD4f5U/x6JKAVXUWBxdYiw41Yrh30/img.png)

- Spring Cloud Gateway를 통해서 외부 또는 내부의 서비스에서 오는 요청이 원하는 서비스를 찾아갈 수 있다. Naming Server는 찾고자 하는 서비스의 위치를 저장한다.
  - Tomcat이 아닌 Netty를 사용하여 비동기 WAS이고 1Thread / Many Request 방식으로 기존 방식보다 더 많은 요청을 처리한다.
  - API Gateway는 클라이언트와 백엔드 서비스 사이에 위치하는 리버스 프록시 역할을 한다.
  - API Gateway는 서버 최앞단에 위치하여 모든 API 호출을 받고 인증 후 적절한 서비스들에 메시지를 전달한다.
  - 인증 및 권한, 모니터링, 로깅 등 기능도 한다.
- Spring Cloud Eureka(Netflix OSS)는 Naming Server로 단위 서비스들에 대해 동적으로 서비스 등록(Service Registry) 및 서비스 디스커버리(Service Discovery)를 수행하고 로드밸런싱을 통해 서비스간 통신의 부하 분산 기능을 한다.
  - Eureka는 각 서비스에서 보내는 하트비트(HeartBeat) 방식으로 상태 정보를 받아들이고 상태 점검(Health Check)를 한다.
  - 만약 하트비트가 수신되지 않은 경우 레지스트리에서 해당 서비스 정보가 제거된다.
  - Eureka의 부하 분산은 클라이언트-사이드 방식의 리본을 사용한다.



[MSA1](http://clipsoft.co.kr/wp/blog/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98msa-%EA%B0%9C%EB%85%90/)

[MSA2](https://www.samsungsds.com/kr/insights/1239180_4627.html)

[Spring Cloud Config Server](https://happycloud-lee.tistory.com/209)

[API Gateway](https://m.blog.naver.com/dktmrorl/222129517689)

[Spring Cloud Gateway](https://saramin.github.io/2022-01-20-spring-cloud-gateway-api-gateway/)



# Message Queue

메시지들을 큐라는 자료구조에 담아서 관리한다는 의미이다.



## MOM

"메시지 지향 미들웨어" 라고 부른다.

응용 소프트웨어 간의 데이터(비동기 메시지) 통신을 위한 소프트웨어이다.

![img](https://blog.kakaocdn.net/dn/bzojLH/btrcFV6Bj5V/cgVBm4FFu840FgA9b0Cd9k/img.png)

- 메시지 지향 미들웨어는 메시지를 전달하는 과정에서 보관하거나 라우팅 및 변환할 수 있다는 장점이 있다.
  - 보관 : 메시지의 백업을 유지함으로써 지속성을 제공, 덕분에 송수신 측은 동시에 네트워크 연결을 유지할 필요가 없다.
  - 라우팅 : 미들웨어 계층 자신이 직접 메시지 라우팅이 가능하기 때문에 하나의 메시지를 여러 수신자에게 배포가 가능해진다(멀티캐스트).
  - 변환 : 송수신 측의 요구에 따라 메시지를 변환할 수 있다.
- 단점
  - 아케텍처에 외부 구성 요소인 메시지 전송 에이전트가 필요, 일반적으로 새로운 요소를 추가할 경우 시스템 성능이 저하되고 신뢰성이 떨어진다.
  - 시스템이 복잡해지기 때문에 관리가 어렵고 비용이 발생한다.
  - 어플리케이션 간의 통신은 본질적으로 동기지만 메시지 기반 통신은 본질적으로 비동기이기 때문에 메커니즘 불일치가 발생한다.



## Message Queue

메시지 큐는 메시지 지향 미들웨어(MOM)를 구현한 시스템으로 프로그램(프로세스) 간의 데이터를 교환할 때 사용하는 기술이다.

![img](https://blog.kakaocdn.net/dn/Ngglq/btrcBzwwxTZ/q8QoaXArd36vlklhu85KT0/img.png)

- 장점
  - **비동기(Asynchronous)** : 데이터를 수신자에게 바로 보내지 않고 큐에 넣고 관리하기 때문에 나중에 처리 가능
  - **비동조(Decoupling)** : 애플리케이션과 분리할 수 있기 때문에 확장이 용이해짐
  - **탄력성(Resilience)** : 일부가 실패하더라도 전체에 영향을 주지 않음
  - **과잉(Redundancy)** : 실패할 경우 재실행 가능
  - **보증(Guarantees)** : 작업이 처리된 걸 확인할 수 있음
  - **확장성(Scalable)** : N:1:M 구조로 다수의 프로세스들이 큐에 메시지를 보낼 수 있음
- 메시지 큐는 대용량 데이터를 처리하기 위한 배치 작업, 채팅 서비스, 비동기 데이터 처리 시 사용한다.
- 다량의 요청을 바로 서버로 보내지 않고 메시지 큐에 보관하고 서버 측에서는 처리하는데 이상 없을 정도의 요청들만 메시지 큐에서 가져와서 처리하여 서버 부담을 줄인다.
- RabbitMQ, ActiveMQ는 신뢰성 있는 메시지 브로커가 필요한 경우 사용하며 Kafka는 처리량이 많은 분산 메시징 시스템에서 사용된다.

[Message Queue](https://sorjfkrh5078.tistory.com/291)



# Cloud



## Public Cloud

퍼블릭 클라우드는 리소스를 클라우드 서비스 공급자가 소유하고 인터넷을 통해 제공하는 클라우드이다.

- 하드웨어, 소프트웨어 지원 인프라를 공급자가 소유하고 관리한다.
- 여기서 공급자는 외부 기업 및 데이터 센터이다.
- Pay as you go 정책을 따른다.
- Ex) AWS, Azure, GCP
- 장점
  - 비용절감
    - 하드웨어 또는 소프트웨어를 구매할 필요가 없으며, 사용한 서비스의 요금만 지불하면 된다.
  - 유지관리 불필요
    - 서비스 공급자가 유지 관리를 제공한다.
  - 무제한에 가까운 스케일링 기능
    - 주문형 리소스를 사용하여 비즈니스 요구 사항을 충족할 수 있다.
- 단점
  - 업체 종속
    - 클라우드 업체가 제공하는 가상 머신, 스토리지, 애플리케이션, 기술 등의 서비스에 종속될 수 있다.



## Private Cloud

프라이빗 클라우드는 하나의 조직에 전용 클라우드 환경을 제공하는 모델이다.

- 프라이빗 클라우드에서는 서비스와 인프라가 항상 프라이빗 네트워크에서 유지 관리되며 하드웨어와 소프트웨어는 조직에서만 전용으로 사용된다.
- 인트라넷 클라우드라고도 불린다.

- Ex) VMware, Openstack
- 장점
  - 유연성 향상
    - 조직에서 특정 비즈니스 요구 사항을 충족하기 위해 클라우드 환경을 사용자 지정할 수 있다.
  - 제어 향상
    - 리소스가 다른 사용자와 공유되지 않으므로 더 높은 수준의 제어 및 개인 정보 보호가 가능하다(보안 우수).
  - 스케일링 성능 향상
    - 온프레미스보다 큰 스케일링 성능을 제공한다.
- 단점
  - 관리비용 및 책임
    - 조직이 관리 비용과 책임을 맡아야하며 인력, 관리, 유지비용이 증가한다.



## Hybrid Cloud

하이브리드 클라우드는 VPN 등의 보안 연결을 통해서 하나 이상의 퍼블릭 클라우드 + 프라이빗 클라우드 환경을 결합하는 방식이다.

- 활용 예
  - 이메일같은 자사의 독자성이 필요없는 서비스는 퍼블릭 클라우드를 이용하고 인사정보나 개인 인증 정보같은 보안성이 필요한 정보는 프라이빗 클라우드에 저장한다.
  - 외부 개발자와 함께 개발할 때는 퍼블릭 클라우드에서 작업하고 개발 결과물은 프라이빗 클라우드로 옮겨서 자사 전용으로 서비스한다.
- 장점
  - 제어
    - 조직이 짧은 대기 시간이 필요한 중요한 자산이나 워크로드를 위한 프라이빗 인프라를 유지 관리할 수 있다.
  - 유연성
    - 필요할 때 퍼블릭 클라우드에서 추가 리소스를 사용할 수 있다.
  - 비용 효율성
    - 퍼블릭 클라우드로 스케일링하는 기능을 통해 필요할 때만 추가 컴퓨팅 성능의 비용을 지불하면 된다.



[Public, Private, Hybrid Cloud1](https://azure.microsoft.com/ko-kr/resources/cloud-computing-dictionary/what-are-private-public-hybrid-clouds/#benefits)

[Public, Private, Hybrid Cloud2](https://owin2828.github.io/devlog/2020/01/10/aws-1.html)

[Public, Private, Hybrid Cloud3](https://ttend.tistory.com/691)



## As a Service

"서비스형(as-a-Service)"는 제 3사에서 클라우드 컴퓨팅 서비스를 제공한다는 의미이다.

- 사용자는 코드, 고객 관계 관리와 같은 더 중요한 업무에 집중할 수 있다.
- 비용이 절감된다.
- 관리가 쉬워진다.
- 스케일링이 가능하다.

![img](https://www.redhat.com/cms/managed-files/iaas-paas-saas-diagram5.1-1638x1046.png)



### IaaS

제 3사가 스토리지와 가상화와 같은 인프라 서비스를 인터넷을 통해 클라우드로 제공하는 것이다.

- 일반적으로 사용하는 클라우드이다.
- 사용자는 운영 체제 및 데이터, 애플리케이션, 미들웨어 및 런타임을 담당하고 제공업체는 사용자가 필요로 하는 네트워크, 서버, 가상화 및 스토리지의 관리와 액세스를 담당한다.
- 장점
  - 필요한 구성 요소만 구매하고 필요에 따라 확장 또는 축소할 수 있는 유연성을 제공한다. 사용자의 재량에 따라 과금되는 경제적인 옵션이다.
  - 개발 및 테스트 환경의 구축 및 제거가 빠르고 유연하다는 장점이 있다. 언제나 스케일링 및 중단 가능하다.
- 단점
  - 제공 업체의 보안 문제 가능성이 있다.
- Ex) AWS, Azure, GCP



### PaaS

제공 업체가 자체 인프라에서 하드웨어와 소프트웨어를 호스팅하고 이러한 플랫폼을 사용자에게 통합 솔루션, 솔루션 스택 또는 인터넷을 통한 서비스로 제공한다.

- 해당 프로세스와 관련된 인프라 또는 플랫폼을 구축하고 유지관리할 필요 없이 사용자가 자체 애플리케이션을 개발, 실행 및 관리할 수 있도록 한다.
- 사용자는 애플리케이션 코드를 작성, 빌드, 관리하지만 소프트웨어 업데이트 또는 하드웨어 유지관리와 같은 번거로움이 사라진다. 빌드 및 배포를 위한 환경이 사용자에게 제공된다.
- 개발자가 프레임워크를 개발하여 지속적으로 웹 기반 애플리케이션을 빌드 및 커스터마이징할 수 있는 방법이다. 개발자는 기본 소프트웨어 구성 요소를 활용하여 자체 애플리케이션을 개발할 수 있으므로 자체적으로 작성해야 하는 코드의 양을 줄일 수 있다.
- Ex) AWS Elastic Beanstalk, Heroku, Red Hat OpenShift



### SaaS

가장 포괄적인 형식의 클라우드 컴퓨팅 서비스로 모든 애플리케이션은 제공업체가 관리하며 웹 브라우저를 통해 제공된다.

- 제공업체가 소프트웨어 업데이트, 버그 수정 및 기타 일반 소프트웨어 유지관리 작업을 처리하며 사용자는 대시보드 또는 API를 통해 애플리케이션을 연결한다.

- 클라우드로 만든 서비스 자체를 제공하는 것으로 google 계정이 지원하는 서비스들을 말한다.
- 현재 개발중인 Fillkie도 SaaS다.
- Ex) Dropbox, Salesforce, Google Apps

[as-a-Service](https://www.redhat.com/ko/topics/cloud-computing/iaas-vs-paas-vs-saas)



# ETCD

**머신의 분산된 시스템 또는 클러스터의 설정 공유, 서비스 검색 및 스케줄러 조정을 위한 일관된 분산형 키-값 저장소이다.**

- 안전한 자동 업데이트 지원한다.
- 호스트에 스케줄링되는 작업을 조정한다.
- 컨테이너에 대한 오버레이 네트워킹 설정을 지원한다.
- **ETCD는 쿠버네티스의 기본 데이터 저장소이며 모든 쿠버네티스 클러스터 상태를 저장하고 복제한다.**
- **ETCD 오퍼레이터를 사용하여 ETCD를 관리한다. 단일 명령으로 설치하고 사용자가 ETCD 클러스터를 생성, 설정 및 관리하는 선언적 설정을 통해 관리한다.**
  - **생성/제거** - 각 etcd 멤버에 대해 설정 세팅을 반복적으로 지정하는 대신에 사용자는 클러스터의 크기를 지정하기만 하면 된다.
  - **크기 조정** - 사용자는 사양의 크기만 수정하면 되며, etcd 오퍼레이터가 클러스터 멤버 배포, 제거 및/또는 재설정 작업을 맡아 처리한다.
  - **백업** - etcd 오퍼레이터는 백업을 자동으로 투명하게 수행한다. 사용자는 백업 정책만 지정하면 된다. 예를 들면, *30분마다 백업하고 마지막 3번의 백업을 보관한다.*
  - **업그레이드** - 다운타임 없이 etcd를 업그레이드하는 것은 매우 중요하지만 까다로운 작업이다. etcd 오퍼레이터를 이용하면 운영이 간소화되고 일반적인 업그레이드 오류를 방지할 수 있다.
  - 즉, 사용자는 ETCD 클러스터 크기, 사양 크기 설정을 통해 생성/제거, 크기 조정을 해결하며 백업 정책을 통해 백업한다. 오퍼레이터를 통해 ETCD 업그레이드가 가능하다.

[ETCD](https://www.redhat.com/ko/topics/containers/what-is-etcd)



# Kubernetes



## Container

![img](https://image.samsungsds.com/kr/insights/__icsFiles/afieldfile/2022/02/21/1.jpg)

**앱이 구동되는 환경까지 패키징하여 실행할 수 있도록 격리하는 기술이다.**

- 컨테이너 런타임 : 컨테이너를 다루는 도구이다.
  - 컨테이너를 쉽게 내려받거나 공유하고 구동할 수 있도록 해주는 도구이다.
  - 도커가 사용하는 컨테이너 규격은 표준화 되어 있어서 도커가 아닌 다른 컨테이너 런타임으로도 도커로 만든 컨테이너를 이용할 수 있다.
- 도커 : 컨테이너를 다루는 도구 중 가장 유명한 것이다.
- 쿠버네티스 : 컨테너 런타임을 통해 컨테이너를 오케스트레이션 하는 도구이다.
  - **여러 서버(노드)에 컨테이너를 분산해서 배치하거나, 문제가 생긴 컨테이너를 교체하거나(상태 관리), 컨테이너가 사용할 비밀번호나 환경 설정을 관리하고 주입하는 일 등을 한다.**
  - 즉, 컨테이너 오케스트레이션을 한다.
  - 컨테이너를 다루기 위해 도커 이외에도 다양한 컨테이너 런타임 소프트웨어 이용 가능하다.
- 오케스트레이션 : 여러 서버에 걸친 컨테이너 및 사용하는 환경 설정을 관리하는 행위이다.

![img](https://image.samsungsds.com/kr/insights/__icsFiles/afieldfile/2022/02/21/2.jpg)

- Traditional Deployment(전통적 배포)는 물리적인 컴퓨터 한대에 하나의 OS를 설치하고 프로그램을 실행하는 방식이다.

- Virtualized Deployment(가상화 배포)는 가상머신을 기반으로 배포하는 방법이다.

  - **하이퍼바이저는 하나의 시스템 상에서 가상 컴퓨터를 여러 개 구동할 수 있도록 해주는 중간계층이다.**
  - App은 실행하고자 하는 프로그램, Bin/Library는 프로그램이 실행하는데 필요한 환경과 관련된 파일이다.
  - **가상머신은 CPU, 메모리, 저장 장치를 개별적으로 할당하며 OS도 별도로 할당한다.**

- Container Deployment(컨테이너 중심의 배포)는 가상화 배포와 달리 프로그램 구동을 위해서 OS를 매번 설치할 필요가 없이 OS를 1개만 사용한다.

  - 컨테이너는 하단이 어떻게 동작하는지 관심이 없어서 가상머신에서도 배포될 수 있다.
  - **2개의 컨테이너를 실행하면 프로그램 간에 간섭을 일으킬 수 없는 장벽을 치며 OS는 CPU, 메모리 등의 자원을 독립적으로 사용할 수 있도록 할당하고 관리한다.**
  - 컨테이너로 실행된 프로그램은 서로 다른 컴퓨터에서 실행되는 중이라고 생각하게 된다.
  - 컨테이너 동작 방식을 OS 커널을 공유하는 가상화라고 표현하기도 한다.
  - **컨테이너는 OS를 공유하는 방식이기 때문에, 어떤 프로그램의 문제가 다른 프로그램을 간섭할 수는 없다. 하지만 내 프로그램의 문제가 OS에 문제를 일으킬 경우에는 OS에서 구동 중인 전체 컨테이너의 문제가 될 가능성이 있다.**
  - **리눅스를 기준으로 내가 실행한 프로그램이 독립된 환경에서 실행되는 것처럼 격리시켜주고, CPU, 메모리 및 저장 장치와 같은 자원도 실행한 프로그램이 독립적으로 쓸 수 있도록 해주는 namespace 및 cgroup이라는 기술을 제공한다.**

  ![img](https://image.samsungsds.com/kr/insights/__icsFiles/afieldfile/2022/02/21/5.jpg)

[Container](https://www.samsungsds.com/kr/insights/220222_kubernetes1.html?referrer=https://www.google.com/)



# Kubernetes

**쿠버네티스는 여러 서버(노드)에 컨테이너를 분산해서 배치하거나, 문제가 생긴 컨테이너를 교체하거나(상태 관리), 컨테이너가 사용할 비밀번호나 환경 설정을 관리하고 주입하는 일 등을 한다.**

- 미니쿠브(Minikube)

  - 설치하기 쉽다.
  - **쿠버네이스가 제공하는 대부분의 기능을 활용할 수 있다.**
  - 개발 도구들과 연계 가능하다.
  - **미니쿠브는 로컬에 설치되며 단일 노드 형태로 동작하기 때문에 다중노드를 구성하여 수행해야 하는 작업을 하기는 좋지 않다.**
  - 또한, 노드를 가상화된 형태로 생성하기 때문에 도커, 버추얼박스 등 가상화 도구가 추가로 필요하다.
  - \- 용도 : 간단한 학습 및 개발 환경 구성
    \- 장점 : 설치가 쉽고 개발 도구와의 연계가 편리함
    \- 단점 : 단일 노드만 지원하며 추가적인 가상화 도구 필요함

- k3s

  - **단일 파일로 이루어진 k3s 실행 파일을 통해 서버와 에이전트만 구동하면 쿠버네티스의 각 구성 요소가 간편하게 설치되면서 쿠버네티스 클러스터를 쉽게 구성할 수 있다.**
  - **ETCD는 경량의 내장 데이터베이스인 SQLite로 대체되어 가볍다.**
  - 소규모의 운영 환경에도 적용가능하다.
  - **k3s는 대부분의 구성 요소가 매우 단순화되어 있어 높은 성능과 안정성을 요구하는 시스템에는 부적합할 수 있다.**
  - \- 용도 : 쿠버네티스와 완전히 호환되는 가벼운 배포판
    \- 장점 : 설치가 쉽고 시스템 리소스를 적게 사용하면서 높은 쿠버네티스 호환성을 보장함
    \- 단점 : 구조가 매우 단순하므로 높은 성능과 안정성을 요구하는 시스템에는 부적합할 수 있음

- 랜처(Rancher)

  ![img](https://image.samsungsds.com/kr/insights/__icsFiles/afieldfile/2022/04/01/2_a4.png)

  - **쿠버네티스 클러스터뿐 아니라 운영에 필요한 모니터링, 보안 관련 기능을 쉽게 설치할 수 있다.**
  - 랜처가 제공하는 마켓 플레이스에서 쿠버네티스 관련 도구를 설치하고 구성 가능하다.
  - 관리 도구를 사용해서 새로운 쿠버네티스 클러스터를 쉽게 생성하고 여러 클러스터를 한곳에서 관리할 수 있다.
  - **여러 클라우드를 동시에 활용하는 멀티 클라우드 환경을 구성할 수 있다.**
  - **랜처는 대규모 시스템 관리까지 염두한 플랫폼이므로 자체적인 구성 요소가 많이 포함되어 있으며 이로 인하여 다른 도구에 비해 조금 무거운 면이 있다. **그래서 모니터링이나 대시보드를 자동으로 구성해 주는 도구 정도로 접근하는 경우가 있다.
  - \- 용도 : 대규모 및 기업용 환경에서도 활용 가능한 다목적 쿠버네티스 관리 플랫폼
    \- 장점 : 기본적으로 포함되어 있는 기능이 많고 추가 도구 설치도 쉬움. 멀티 클라우드 관리 가능함
    \- 단점 : 다른 도구에 비해 무거우므로 시스템 환경에 따라 적절한 고려가 필요함

- 매니지드 쿠버네티스 서비스(Managed Kubernetes Service)

  - **퍼블릭 클라우드 서비스에서 제공하는 쿠버네티스 서비스를 사용하는 것이며  클러스터의 관리까지 퍼블릭 클라우드에서 해주기 때문에 사용자는 쿠버네티스 기능을 사용하는 데에만 집중할 수 있다.**
  - AWS(EKS), Azure(AKS), GCP(GKE)가 있다.
  - **삼성SDS 또한 CNCF의 Certified Kubernetes 인증을 받은 Samsung Cloud Platform(SCP) Kubernetes Engine 서비스를 제공한다.**

[Kubernetes](https://www.samsungsds.com/kr/insights/kubernetes-2.html?moreCnt=1&backTypeId=insight&category=all)



## Pod

**쿠버네티스 포드는 Linux 컨테이너를 하나 이상 모아 놓은 것으로 쿠버네티스 애플리케이션의 최소 단위이다. 리소스를 더 지능적으로 공유하기 위해 포드로 관리한다.**

- **쿠버네티스 시스템에서는 같은 포드에 속한 컨테이너끼리 동일한 컴퓨팅 리소스를 공유한다.**
- 이러한 컴퓨팅 리소스를 풀링하여 클러스터를 만들고, 이를 바탕으로 더 강력하고 지능적으로 분산된 애플리케이션 실행 시스템을 제공한다.

### 하드웨어 유닛

**노드: 쿠버네티스에서 최소 단위의 컴퓨팅 하드웨어이며, 하나의 개별 머신으로 생각하면 됩니다.**

**클러스터: 지능적인 리소스 공유와 균형 배분을 위해 여러 노드를 묶은 그룹입니다.**

### 소프트웨어 유닛

Linux 컨테이너: 하나 이상의 프로세스 모음이며, 실행에 필요한 파일도 모두 들어 있어 머신 간 이식이 가능합니다.

**쿠버네티스 포드: 하나 이상의 Linux 컨테이너 모음이며, 클러스터 관리를 통한 리소스 공유의 장점을 극대화하기 위해 패키지로 묶여 있습니다.**

![img](https://d33wubrfki0l68.cloudfront.net/5cb72d407cbe2755e581b6de757e0d81760d5b86/a9df9/docs/tutorials/kubernetes-basics/public/images/module_03_nodes.svg)

- 기본적으로 쿠버네티스에서는 개별 하드웨어를 노드라고 부른다.
- 노드가 여러 개 모여 클러스터를 이루며, 이로써 필요에 따라 컴퓨팅 성능을 분산시킬 수 있다.
- 이 클러스터에서 실행되는 것이 포드이다.
- 포드와 클러스터의 관계 때문에 쿠버네티스는 직접 컨테이너를 실행하지 않는다.
- **포드를 실행하면서 포드 속의 각 컨테이너가 동일한 리소스 및 로컬 네트워크를 공유한다.**
- 이런 식으로 컨테이너를 그룹화하면 실제로는 어느 정도 분리된 상태더라도 마치 동일한 물리 하드웨어를 공유하는 것처럼 컨테이너끼리 서로 통신할 수 있다.
- 컨테이너를 포드로 구성하는 것이 바로 쿠버네티스의 유명한 기능, 복제의 토대가 된다.
- **복제는 스케일 아웃을 말하며 포드를 기준으로 진행된다.**
- **쿠버네티스 포드는 과부하 상태에서의 정상 작동을 지원할 뿐만 아니라 지속적으로 복제되면서 시스템의 내장애성을 제공한다.**

[Kubernetes Pod](https://www.redhat.com/ko/topics/containers/what-is-kubernetes-pod)



# C & Java & Python



## C

- 절차지향형 언어이다.
  - 객체가 아닌 코드 들의 일련의 순서에 집중하는 것으로 유지 보수 하는 것이 어렵다.
- 컴퍼일러 언어이다.
  - 인터프리터 언어에 비해 실행속도가 빠르다.
- Low Level 언어이다.
  - 어셈블리어 수준으로 하드웨어를 제어할 수 있다.
  - 즉, 임베디드 시스템, 운영체제, 하드웨어 제어 시스템 개발 등에 사용된다.
- 개발자가 직접 GC를 작동해야 한다.
  - 일일이 free() 해줘야 한다.
  - GC 라이브러리의 제공으로 자동으로 하기도 한다.



## C++

- 객체지향형 언어이다.
  - C의 문법적 체계를 그대로 계승했다.
  - C언어에 객체 지향 개념을 도입한 것이다.
- 컴파일러 언어이다.



## Java

- 객체지향 언어이다.
  - C++과 마찬가지로 객체지향 언어이지만 설계 목표의 차이에 따른 차이가 존재한다.
  - Java는 보안, 이식성, 빠른 개발에 비중을 두고 C++는 속도와 C와 하위 호환성에 중점을 둔다.
- 인터프리터와 컴파일러를 모두 사용한다.
  - Javac(Java Compiler)를 이용해 소스코드를 .class 파일로 컴파일하고 이후 JVM의 인터프리터에서 바이트코드를 한 줄씩 읽어 실행한다.
- 웹 서비스 개발, 안드로이드 앱 개발에 사용한다.
- GC
  - 자동으로 주기적으로 검사하여 GC 실행한다.
  - C++는 메모리에 직접 접근하여 명시적으로 할당을 해제하여 메모리 누수를 방지하지만 Java는 직접 메모리 영역에 접근하지 않고 JVM 가상머신을 사용하여 간접적으로 접근한다.
  - Heap 영역은 처음 설계될 때 2가지 전제로 설계되었다.
    - 대부분의 객체는 금방 접근 불가능한 상태(Unreachable)가 된다.
    - 오래된 객체에서 새로운 객체로의 참조는 아주 적게 존재한다.
  - 객체 생존 기간에 따라 물리적인 Heap 영역을 나누게 되었다.
    - Young 영역
      - 새롭게 생성된 객체가 할당되는 영역이다.
      - 대부분의 객체가 금방 Unreachable 상태가 되기 때문에, 많은 객체가 Young 영역에 생성되었다가 사라진다.
      - Young 영역에 대한 GC를 Minor GC라고 부른다.
    - Old 영역
      - Young 영역에서 Reachable 상태를 유지하여 살아남은 객체가 복사되는 영역이다.
      - Young 영역보다 크게 할당되며, 영역의 크기가 큰 만큼 가비지는 적게 발생한다.
      - Old 영역에 대한 GC를 Major GC 또는 Full GC라고 부른다.
  - Old 영역이 Young 영역의 객체를 참조하는 경우 참조 정보가 512 bytes의 카드 테이블에 표시된다.
    - Young 영역에서 GC가 시행될 때 모든 Old 영역에 존재하는 객체를 검사하여 참조되지 않는 Young 영의 객체를 식별하는 것이 비효율 적이므로 카드 테이블만 조회한다.\
  - GC 작동 방식에는 2가지가 있다.
    - Stop The World
      - JVM이 애플리케이션의 실행을 멈추는 작업이다.
      - GC를 실행하는 스레드를 제외한 모든 스레드들의 작업이 중단된다.
      - GC의 성능 개선을 위해 튜닝을 한다고 하면 보통 stop-the-world의 시간을 줄이는 작업을 하는 것이다.
    - Mark and Sweep
      - Mark : 사용되는 메모리와 사용되지 않는 메모리를 식별하는 작업이다.
      - Sweep : Mark 단계에서 사용되지 않음으로 식별된 메모리를 해제하는 작업이다.
    - Stop The World를 통해 모든 작업을 중단시키면, GC는 스택의 모든 변수 또는 Reachable 객체를 스캔하면서 각각이 어떤 객체를 참조하고 있는지를 탐색하게 된다. 그리고 사용되고 있는 메모리를 식별하는데, 이러한 과정을 Mark라고 한다. 이후에 Mark가 되지 않은 객체들를 메모리에서 제거하는데, 이러한 과정을 Sweep이라고 한다.

[Java GC1](https://mangkyu.tistory.com/118)

[Java GC2](https://lemonlemon.tistory.com/175)



## Python

- 객체지향 언어, 스크립트 언어, 인터프리터 언어이다.
  - 스크립트 언어로 컴파일 과정 없이 인터프리터에 의하여 실행된다.
  - 즉, 컴파일 언어에 비해서는 속도가 느리다.
- 동적 타입 언어이다.
  - 변수의 자료형을 따로 지정하지 않고 선언하는 것만으로 값을 지정할 수 있다.
  - 따라서 변수의 자료형은 코드가 실행되는 시점에 결정된다.
- 플랫폼 독립적이다.
  - 인터프리터 언어의 특징 중 하나로, 운영체제에 따라 컴파일할 필요가 없기 때문에 플래폼 독립적이다.
  - 즉, 어느 OS에서도 바로 실행 가능하다.
- C로 이루어져 있다.
- 딥러닝, 빅데이터, AI에 사용한다.
- GC
  - 자동으로 주기적으로 검사하여 GC를 실행한다.
  - Reference Counting
    - 모든 객체는 참조 당할 때 이 레퍼런스 카운트를 증가시키고, 참조가 없어지면 이를 감소시킨다.
    - 이 값이 0이 되면 객체가 메모리에서 해제된다.
  - Generational Garbage Collection
    - GC는 내부적으로 세대와 임계값을 통해 GC 주기와 객체를 관리한다.
    - 0, 1, 2 세대가 있으며 생성된 객체는 0세대로 이동하고 오래된 객체는 2세대로 이동한다.
      - (700, 10, 10) 일때 0세대이면 700번 참조, 1세대이면 7000번 참조, 2세대는 70000번 참조가 일어나면 GC가 실행되는 것이다.
    - 순환 참조를 해결한다.
      - 순환 참조 탐지 알고리즘을 통해 특정 세대에서 도달할 수 있는 객체를 찾는데 도달할 수 있는 객체는 세대를 아전 시키고 도달할 ㅅ후 없는 객체는 메모리에서 해제된다.
      - 객체에 gc_refs 필드를 레퍼런스 카운트와 같게 설정한다.
      - 각 객체에서 참조하고 있는 다른 컨테이너 객체를 찾고, 참조되는 컨테이너의 gc_refs를 감소시킨다.
      - gc_refs가 0이면 그 객체는 컨테이너 집합 내부에서 자기들끼리 참조하고 있다는 뜻이다.
      - 그 객체를 Unreachable하다고 표시한 뒤 메모리에서 해제한다.

[Python GC](https://codediary21.tistory.com/77)

[C & Java & Python](https://code-lab1.tistory.com/240)



# gRPC

gRPC는 구글에서 개발한 어느 환경에서 실행할 수 있는 최신 오픈 소스 고성능 RPC 프레임워크이다.

- Protocol Buffer

  - gRPC는 IDL(Interface Definition Language)로 Protocol Buffer을 사용한다.

  - Protocol Buffer는 구조화된 데이터를 직렬화, 역직렬화 데이터 구조로 통신한다.

    ![img](https://miro.medium.com/max/1400/1*PTZ_ELRZlbCZKqOBbCJ2Jg.png)

    - 간단하다.
    - 파일 크기가 3~10배 정도 작다.
    - 속도가 20~100배 정도 빠르다.
    - XML보다 가독성이 좋고 명시적이다.
    - JSON은 직렬화보다 무겁고 느리다.
    - 이진 데이터로 직렬화 된다.

  - 하나의 프로그래밍 언어가 아닌 다양한 언어와 플랫폼에서 동작한다(11개 언어).

    - 다양한 지원으로 비즈니스 로직 구현에만 집중할 수 있다.

  - HTTP/2 기반

    - 양방향 스트리밍이 가능하여 서버, 클라이언트가 동시에 데이터를 주고 받을 수 있다.
    - HTTP/2의 헤더 압축과 protoBuf에 의한 메시지 정의에 의해 메시지 크기가 획기적으로 줄어든다.
    - 즉, 네트워크 트래픽이 줄어드는 것을 의미한다.

  - gRPC vs HTTP

    | 기능                 | gRPC                                                         | JSON을 사용하는 HTTP API        |
    | :------------------- | :----------------------------------------------------------- | :------------------------------ |
    | 계약                 | 필수(`.proto`)                                               | 선택 사항(OpenAPI)              |
    | 프로토콜             | HTTP/2                                                       | HTTP                            |
    | Payload              | [Protobuf](https://docs.microsoft.com/ko-kr/aspnet/core/grpc/comparison?view=aspnetcore-6.0#performance)(소형, 이진) | JSON(대형, 사람이 읽을 수 있음) |
    | 규범                 | [엄격한 사양](https://docs.microsoft.com/ko-kr/aspnet/core/grpc/comparison?view=aspnetcore-6.0#strict-specification) | 느슨함. 모든 HTTP가 유효합니다. |
    | 스트리밍             | [클라이언트, 서버, 양방향](https://docs.microsoft.com/ko-kr/aspnet/core/grpc/comparison?view=aspnetcore-6.0#streaming) | 클라이언트, 서버                |
    | 브라우저 지원        | [아니요(gRPC-웹 필요)](https://docs.microsoft.com/ko-kr/aspnet/core/grpc/comparison?view=aspnetcore-6.0#limited-browser-support) | 예                              |
    | 보안                 | 전송(TLS)                                                    | 전송(TLS)                       |
    | 클라이언트 코드 생성 | [예](https://docs.microsoft.com/ko-kr/aspnet/core/grpc/comparison?view=aspnetcore-6.0#code-generation) | OpenAPI + 타사 도구             |

- Stub
  - Stub는 RPC의 핵심 개념으로 Parameter 객체를 Message로 Marshalling/Unmarshalling하는 레이어이다.
  - 서버와 클라이언트는 서로 다른 주소 공간을 사용하므로 함수 호출에 사용된 매개 변수를 꼭 변환해줘야 한다. 그렇지 않으면 메모리 매개 변수에 대한 포인터가 다른 데이터를 가리키게 되기 때문이다.
    - Marshalling : 직렬화된 객체를 바이트 단위로 분해한다.
    - Unmarshalling : 전송받은 데이터를 원래대로 복구한다.
    - client의 stub은 함수 호출에 사용된 파라미터의 변환(marshalling) 및 함수 실행 후 서버에서 전달된 결과의 변환 담당한다.
    - server의 stub은 클라이언트가 전달한 매개 변수의 역변환(unmarshalling) 및 함수 실행 결과 변환을 담당한다.

- MSA
  - ProtoBuf가 지원하는 IDL 활용한 서비스 및 메시지 정의는 MSA의 다양한 기술 스택의 공존으로 인한 중복 발생의 단점을 보완하고, 수많은 서비스간의 API 호출로 인한 성능 저하를 개선한다.
  - ProtoBuf는 다양한 언어와 플랫폼을 지원하여 언어에 구애받지 않고, 원격에 있는 프로시저를 호출하여 고유 프로그램의 개발에 집중할 수 있게한다.
  - 내부 요청이 많은 MSA에서 ProtoBuf로 요청 처리 시간 감소는 매우 중요하다.

[gRPC1](https://chacha95.github.io/2020-06-15-gRPC1/)

[gRPC2](https://velog.io/@dojun527/gRPC%EB%9E%80)

[gRPC vs HTTP](https://docs.microsoft.com/ko-kr/aspnet/core/grpc/comparison?view=aspnetcore-6.0)

[gRPC MSA1](https://tech.buzzvil.com/blog/tech-blog-grpc%EB%A5%BC-%EC%93%B0%EB%A9%B4-rest%EA%B0%80-%EA%B3%B5%EC%A7%9C/)

[gRPC MSA2](https://medium.com/@goinhacker/microservices-with-grpc-d504133d191d)

[Data Serialization](https://hub1234.tistory.com/26)



# CRDT

여러 사용자가 동시에 사용할 수 있도록 하는 서비스이다.

- 동시편집에는 OT, CRDT가 있으며 공통적으로 다수의 사용자가 모두 같은 상태를 유지해야 한다는 조건이 있다.



## OT

Operational Transformation이다.

- 클래식한 동시 편집 방법으로 Google Docs에서 이용한다.

- 예

  ![img](https://s3.ap-northeast-2.amazonaws.com/zoyi-ghost/kr/2021/04/crdt_vs_ot_ot___________4-1617612847570.png)

  - !이 먼저 적용되면 그대로 l을 3번 인덱스에 넣으면 된다.
  - l이 먼저 적용된 경우 !는 4번 인덱스였지만 서버에서 조절하여 5번 인덱스에 넣는다. 즉, 다른 실시간 반영된 operation에 의해 삽입 위치를 바꿔야 하므로 Operation Transformation이라고 부른다.
  - 단점
    - 모든 요청은 하나의 서버를 통하게 되어있다.
      - 위에 설명한 서버에서 동시 요청에 대한 반영에 대한 알고리즘을 적용하여 반영해야 하기 때문이다.
      - 즉, 같은 와이파이를 사용해도 바로 반영하지 못하고 Google 서버와 통신해야 한다.
      - CRDT는 서버를 반드시 거쳐야되는 네트워크를 방지하여 모든 channel을 사용할 수 있다.



## CRDT

Conflict

- 기본 개념이 적용된 CRDT를 개발하는 것은 쉽지만 예상한 정확한 결과를 도출하는 CRDT를 개발하는 것은 어렵다.



### Interleaving Anomalies

![img](https://s3.ap-northeast-2.amazonaws.com/zoyi-ghost/kr/2021/04/crdt_vs_ot_crdt___________-1617612861067.png)

- OT의 서버 접근을 방지하기 위해 CRDT는 인덱스가 아닌 Unique Indentifier(식별자)을 사용한다. 간단한 예로 소수를 사용할 수 있다.
- 이 식별자는 각 문자마다 정적으로 할당되며 CRUD가 행해져도 그대로 유지된다.
- 배열의 2번째 인자인 'A'는 노드(사용자)를 의미하며 서로 다른 노드ID가 같은 번호를 선택 시 순서를 정해주는 용도로 사용한다.

![img](https://s3.ap-northeast-2.amazonaws.com/zoyi-ghost/kr/2021/04/crdt_vs_ot_crdt________1-1617612875238.png)

![img](https://s3.ap-northeast-2.amazonaws.com/zoyi-ghost/kr/2021/04/crdt_vs_ot_crdt________2-1617612881030.png)

- 하지만 식별자를 사용해도 동시에 같은 지점에 데이터 삽입 시 충돌이 일어나게 된다.
- 이러한 문제를 방지하기 위해 식별자로 범위 안의 랜덤 숫자를 사용하기도 한다.

![img](https://s3.ap-northeast-2.amazonaws.com/zoyi-ghost/kr/2021/04/crdt_vs_ot_crdt________-1617612888999.png)

- Treedoc, WOOT는 가장 안전한 알고리즘이지만 식별자로 인해 많은 메모리 공간을 차지하게(비효율적임) 되어 LSEQ 알고리즘이 나왔지만 좋은 결과는 도출하지 못했다.

- Logoot, LSEQ는 interleaving이 발생하여 text editing에 좋지 않다.

- Astrong도 마찬가지이다.

- RGA 적은 interleaving이며 Treedoc, WOOT보다 효율적이다.

- RGA

  ![스크린샷 2022-08-22 오후 5.22.53](/Users/mwkang/Desktop/스크린샷 2022-08-22 오후 5.22.53.png)

  ![image-20220822174632596](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822174632596.png)

  - 각각의 문자의 부모는 직전에 입력된 문자가 된다(LinkedList처럼 적용됨).
  - 커서가 움직이면 새로운 sub tree가 생성된다. 이 트리의 순서는 깊이 우선이다.
    - 서브 트리를 접근하는 순서는 모든 노드에 저장된 타임스탬프로 판별한다.
  - 타임스탬프는 동시편집에서 판별이 어렵기 때문에 좌측 아래의 3가지 결과가 도출될 수 있다.
  - 즉, 위의 글자 하나하나 식별하던 방법보다는 더 정확한 동시편집이 된다.
  - 하지만 글자 하나하나 식별하던 문제가 발생할 수 있긴 하다.
    - 즉, 사용자가 단어를 가장 뒷글자부터 하나하나 작성하면서 커서를 바꾸면 발생한다.

  - 단어에 식별자를 부여하는 방법이다. 즉, 글자가 섞이지는 않는다.
  - 물론 3가지 결과가 도출되지만 RGA에서 이 3가지 중 요구했던 결과를 도출하는 알고리즘이 2019년에 생성되었다.



### Moving (reordering) List Items

단어를 생성, 삭제하는 것이 아닌 위치(순서)를 바꾸는 것이다.

![image-20220822174943176](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822174943176.png)

- "삭제 후 다시 삽입"을 이용하면 3번의 단어는 사라지지만 모두 1번자리에 삽입하여 중복이 발생한다.

![image-20220822175804581](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822175804581.png)

![image-20220822175932728](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822175932728.png)

- 두 사용자가 같은 문자를 다른 위치로 이동 시 문제가 발생한다.
  - 이때 둘다 적용하면 이전과 같이 중복이 발생하는 것이다.
- 두 명령 중 하나의 명령만 반영하는 방법을 선택한다.
- 즉, 마지막에 명령한 사용자의 명령이 반영된다.
- 이때에도 이전의 알고리즘을 사용하여 단어를 옮긴다.
- Set에 옮기려는 단어들의 순서를 저장한 후 CRDT로 옮긴다.
  - Set에는 Last Writer Win Resgister로 마지막 사람이 옮기려는 위치가 저장된다.
- 즉, RGA 알고리즘, AtWin Set, Last Writer Win Register를 적용하여 현재의 문제를 해결한다.

![image-20220822181219106](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822181219106.png)

![image-20220822181234157](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822181234157.png)

- 한 사용자는 한 부분을 옮기며 다른 사용자는 그 부분을 수정할 때 문제가 발생한다.
- 이 문제는 아직 해결되지 못했다.



### Moving Subtrees of a Tree

리스트가 아닌 트리의 위치를 변경하는 것이다.

![image-20220822182755950](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822182755950.png)

- A 트리를 각 사용자가 B, C로 옮기는 과정이다.
- (a)는 중복이며 (b)는 트리구조가 파괴되므로 사용하지 않는다.
- (c), (d)가 합리적이며 이전의 Last Writer Win을 적용한다.

![image-20220822183129169](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822183129169.png)

- 트리를 옮기는 예이며 파일 시스템이 관련된 것이다.
- a디렉토리 내부에 b디렉토리가 있는데 a디렉토리를 b디렉토리로 옮기려는 시도로 Mac OS 등 이러한 것은 사이클이 생기며 오류를 발생한다.

![image-20220822183929584](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822183929584.png)

- 서로를 부모 노드라고 변경하여 사이클이 발생하는 경우이다.
- 이때에도 (c)나 (d)를 선택하는 것이 좋다.
- 구글 드라이브도 이 사항은 해결하지 못하여 에러 메시지를 출력한다.

![image-20220822184448448](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822184448448.png)

- Lamport 타임스탬프와 같은 것으로 각 요청을 안전하게 수행할 수 있다고 가정한 후 요청을 병합하는 과정이다.
- 이때 A B는 safe하지만 이미 변한 트리구조로 인해 B A는 unsafe하다.
- 이때 B A 요청은 무시하고 undo 하는 것이 맞다.

![image-20220822184728923](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822184728923.png)

- 위의 상황을 해결하기 위해 요청들을 모아서 타임스탬프 순서로 적용해야 한다.
- 이때 Replica 1은 t1, t3, t4, t5를 실행했는데 t2가 t3, t4, t5보다 선행되어야 하므로 undo 과정을 거쳐야 한다. 그 후 병합을 수행한다.

![image-20220822230253403](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822230253403.png)

- 3개의 replica가 서로 멀리 위치해도 초당 600개의 트리 위치 변경을 해결한다.

![image-20220822230916194](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822230916194.png)

- LogEntry 구조체를 생성하여 위치 변경 이전의 parent Node, metadata를 저장하여 undo 가 가능하도록 한다.

![image-20220822232351284](/Users/mwkang/Library/Application Support/typora-user-images/image-20220822232351284.png)

- 현재 적용한 알고리즘에 대한 전제이다.
- 모든 트리는 부모 식별자가 있으며 이것으로 사이클 발생을 방지한다.
- CRDT로 서로 같은 결과를 공유한다.



### Reducing Metadata Overhead of CRDTs

![image-20220823003156949](/Users/mwkang/Library/Application Support/typora-user-images/image-20220823003156949.png)

- 다양한 metadata가 생성되어 데이터로 전송된다.

![image-20220823003235838](/Users/mwkang/Library/Application Support/typora-user-images/image-20220823003235838.png)

- 옛 버전은 JSON을 사용하여 인코딩하고 네트워크를 통해 디스크에 저장하지만 JSON은 매우 장황하다.
- 모든 add, delete 등 기록을 binary 인코딩으로 변경하여 200배 정도 사이즈를 줄였다. protobuf의 경우 3배정도만 빨라질 것이다. 200배 사이즈 감소를 위해서는 CRDT에 맞는 포맷의 binary로 인코딩해야 한다.
- 커서 위치는 저장하지 않아도 되므로 없애면 22% 사이즈 감소한다. 여기까지 사용하자.
- 변경 히스토리마저 지우면 150% 사이즈 감소한다.
- TombStone을 삭제하면 이전의 기록과 merge를 할 수 없지만 추가로 48% 사이즈 감소한다.
- 마지막은 그냥 raw data로 아무 메타데이터가 없는 것이다.

![image-20220823005006826](/Users/mwkang/Library/Application Support/typora-user-images/image-20220823005006826.png)

- 모든 입력은 Set으로 저장한다.
- 유니크 식별자는 Lamport Timestamp를 이용한다.
- 각 입력은 이전의 ID(Lamport TimeStamp)를 참조한 후 입력된다.
- 모든 입력 요청은 문자 순서(문서 정렬)로 저장된다.

![image-20220823005537619](/Users/mwkang/Library/Application Support/typora-user-images/image-20220823005537619.png)

- Lamport TimeStamp를 인코딩하는 것으로 1씩 증가하였으므로 Run-Length Encoding으로 111111이 (6,1)로 압축된다.

![image-20220823005711608](/Users/mwkang/Library/Application Support/typora-user-images/image-20220823005711608.png)

- Actor은 원래 UUID로 16바이트이며 lookup table을 통해 작게 매핑한다.
- 그 후 동일하게 Run-Length Encoding 방법을 적용한다.

![image-20220823010550923](/Users/mwkang/Library/Application Support/typora-user-images/image-20220823010550923.png)

- 길이, 문자를 인코딩 후 concat만 하여 추가한다.
- 길이는 분리할 때도 사용한다.

![image-20220823011304055](/Users/mwkang/Library/Application Support/typora-user-images/image-20220823011304055.png)

- TimeStamp, ID(UUID) 범위 metadata를 추가하여 히스토리를 정확하게 기록할 수 있다.

[CRDT](https://www.youtube.com/watch?v=x7drE24geUw&t=3s)



# Lamport Timestamp

Locgical clock에서 중요하게 생각하는 것은 각 이벤트 간의 인과관계다. 즉 사건 A가 사건 B보다 먼저 발생했다는 것이 중요하지, 사건 A가 B보다 얼마나 빨리 발생 했느냐 같은 것은 고려 대상이 아니다.

Lamport Timestamp는 논리 시간으로 각 프로세스의 이벤트 발생 시간을 동기화하는 것이다.

![img](https://blog.kakaocdn.net/dn/bgvrnf/btrexekPSCx/cZpbkv2DrI92UAxxMouwyk/img.jpg)

- Lamport Timestamp Rule

  - **clock counter는 각 이벤트가 발생하기 전에 증가한다.**

  - 프로세스가 메시지를 보낼 때, 메시지에 clock counter 값을 같이 보낸다.

  - **메시지가 도착하면 받은 clock counter와 자신이 가지고 있던 clock counter를 비교하여 자신이 가진 것이 크다면 그대로 유지하고, 새로 도착한 것이 더 크다면 새로운 clock counter에 1을 증가시킨 것을 자신의 clock couter로 셋팅한다.**

- Lamport Timestamp 주의사항

  - 하나의 프로세스에서 두 개의 사건이 발생하는 간격이 tick이 터지는 간격보다 더 빠르다면, 시간 구분을 할 수 없고 인과관계가 엉망이 된다. **Tick의 발생 주기는 이벤트의 발생 주기보다 짧아야 한다.**
- 두개의 프로세스에서 동일한 시간에 이벤트를 발생 시켜버린다면 역시 시간 구분을 할 수 없고 인과관계가 엉망이 되어버린다. 그래서 모든 시간의 소수점 이하로 프로세스의 번호를 붙여 다른 프로세스에서 같은 시간을 발생 시킬 수 없도록 한다. **즉, 동일 시간 이벤트 발생 시 프로세스의 번호에 따라 우선순위를 두는 것이다.**


[Lamport Timestamp](https://kukuta.tistory.com/105)





# Yorkie vs Yjs



## Basic Aspects

- Yjs
  - Yjs는 P2P 모델로 설계되어 있음
  - Yjs는 `Array`, `Map`, `Text`, `XmlElement` 등의 다양한 Shared Types를 지원함
  - Yjs는 다양한 Editor들에 대한 Binding들을 제공하면서, 다양한 형태로 통신할 수 있도록 Providers 들을 제공하고 있음
  - Yjs는 추상화가 잘 되어 있으면서 다양한 모듈들을 제공해서, 코드 몇줄로 쉽게 CRDT 기술을 적용할 수 있었음
- Yorkie
  - Yorkie는 전통적인 Client-Server 모델로 설계되어 있음
  - Yorkie는 `PlanText`, `RichText`, `JSONArray` 등의 text 기반의 Shared Types를 지원하는 것 같음
  - CRDT 기술의 핵심에 가까운 API들을 제공하고 있음 (쉽게 사용할 수 있도록 추상화가 덜 되어 있는 것 같음)



## Flow (Diagram)

- High-Level Flow
  - Yorkie
    - Clients (Changes) → gRPC → Server → gRPC → Clients (Propagates)
  - Yjs
    - WebRTC (P2P)
      - Clients (Changes, Propagates) ↔ Clients (Changes, Propagates)
    - WebSocket (Client-Server)
      - Clients (Changes) → WebSocket → Server → WebSocket → Clients (Propagates)



## Front-End



### Usability

- Yjs는 `Y.Map` 이라는 Shared Types를 지원함. 이는 key-value 형태의 Map 자료구조를 기반으로 하고 있어, `ymap.set(key, value)`, `ymap.get(key)`, `ymap.delete(key)` 등의 API들을 제공해줌
  - tldraw + Yjs로 실시간 화이트보드를 빌드할 때는 Map 자료구조로 쉽게 화이트보드 위의 shape들을 set하고 delete 할 수 있었음
- Yorkie의 canvas 예제를 빌드할 때는 `JSONArray`가 이용되어 root → shapes → points → point 의 중첩된 형태로 캔버스 위의 shape들을 저장하는 형태로 진행되었음
  - `JSONArray` 의 `deleteByID(ID: TimeTicket)`로 shape들을 삭제할 수 있을 것 같았음



## Back-End

- Yorkie에서 docker-compose 파일을 제공해줘서 쉽게 Docker Container로 올릴 수 있음
- Yorkie Docs 에서 Server for Web, Auth Webhook, Monitoring Server, Cluster Mode 등 백엔드 단의 여러 tasks 들을 설명해주고 있어서 쉽게 백엔드를 빌드 할 수 있었음



## Docs

- 사용성
  - 전체적으로 reference, 자료가 부족함
- 건의사항
  - Search: 자료 검색 기능
  - API: API 문서를 Documentation의 목차에서 바로 볼 수 있으면 API를 더욱 쉽게 찾을 수 있을 것 같음

[Yorkie vs Yjs](https://www.notion.so/Yorkie-vs-yjs-e26221241d934c44a1f16800a96650b7)
