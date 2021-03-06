# OS 운영체제

## 운영체제의 구조
* 커널
  > 프로세스관리, 메모리 관리, 저장장치 관리, 파일 시스템 관리, 입출력 관리, IPC 관리와 같은 운영체제의 핵심적인 기능을 모아놓은 것
  * 커널의 구성
    > 커널이 하는 일
      - 프로세스 관리: 프로세스에 CPU를 배분하고 작업에 필요한 제반 환경 제공
      - 메모리 관리: 프로세스에 작업 공간을 배치하고 실제 메모리보다 큰 가상공간을 제공
      - 파일 시스템 관리: 데이터를 저장하고 접근할 수 있는 인터페이스를 제공
      - 입출력 관리: 필요한 입력과 출력 서비스를 제공
      - IPC 관리: 공동 작업을 위한 각 프로세스 간 통신 환경을 지원
 * 커널의 종류
   > 단일형 구조 커널
      - 커널의 핵심 기능을 모듈로 구분 하지 않고, 한 곳에 다 때려박은 구조
      - 장점
        - 모듈 간의 통신 비용이 줄어들어 효율적인 운영이 가능하다
      - 단점
        - 버그나 오류 처리가 힘들다
        - 기능들이 분리 되어 있지 않기 때문에 서로 의존성이 강하다. 문제가 번질 수도 있다는 뜻
        - 다양한 시스템에 적용하기 어렵다
   > 계층형 구조 커널
     - 단일형 구조 커널의 단점을 보완하기 위해 만들어진 구조
     - 비슷한 기능들을 묶어서 계층 간의 통신으로 운영
     - 장점
       - 모듈화를 시켰기 때문에, 버그나 오류를 쉽게 처리 할 수 있다
       - 문제가 발생하면 해당 계층만 고치면 된다
       - 디버깅이 쉽다
    - 단점
       - 커널이 점점 커지면서 오류 잡기가 힘들어진다 
   > 마이크로 구조 커널
      - 커널이 커지면서 오류를 해결하기 힘들어져서 생긴 커널 구조
      - 꼭 필요한 프로세스 관리, 메모리 관리, IPC 관리 등, 가장 기본적인것만 커널에 두고, 나머지 기능들은 사용자 영역에 구현
      - 메모리관리와 프로세스 동기화 서비스를 제공하며, IPC 를 통해 정보 교환을 한다
      - 장점
        - 각 모듈이 독립적으로 작동하기 때문에, 하나가 고장나더라도 운영체제는 멈추지 않는다
        - 커널이 가벼워져서 CPU 용량이 낮더라도 작동 가능
      - 예) MacOS, iOS 에 사용되는 "MACH" 라는 커널도 마이크로 구조 커널의 한 종류이다.
* 인터페이스
  > 커널에 사용자의 명령을 전달하고 실행 결과를 사용자에게 알려주는 역할
  - 커널과 인터페이스 2개를 분리하여 같은 커널을 이용하더라도, 다른 인터페이스를 사용 할 수 있게 허용
     - UNIX는 셸이라는 인터페이스를 사용 하지만
     - MACOS 도 알고보면 UNIX 계열
* 시스템 호출(System Call)
   > 커널은 컴퓨터 자원을 보호하기 위해 사용자와 외부 응용프로그램을 차단한다. 대신에 시스템 호출로 자원에 접근 할 수 있다
   - 직접 자원에 접근하면, 다른 데이터가 실수로 지워질 수 있다
   - 시스템 호출을 이용하면, 데이터를 쓰고 가져오는 것은 전적으로 커널의 책임이 된다. 그래서 커널이 제공하는 write() / read() 함수로 데이터를 조작 할 수 있다. 이렇게되면 응용프로그램은 정확한 저장 위치는 알 수 없는 것이다.
   - 시스템 호출은 커널이 제공하는 시스템 관련 시비스를 모아놓은 것으로, 함수 형태로 제공됨.
* 드라이버
   > 응용 프로그램과 커널의 인터페이스였다면, 하드웨어와 커널의 인터페이스는 드라이버이다.
   - 커널이 제공하는 드라이버 + 하드웨어 제작자가 제공하는 드라이버, 두 종류가 있다

