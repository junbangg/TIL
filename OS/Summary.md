

* 프로세스란?
  > 프로세스는 메모리에 올라와있는 프로그램의 인스턴스를 말합니다. 
  > 즉, 컴퓨터에 연속적으로 실행이 진행중인 프로그램.
  > 운영체제로부터 할당받은 작업의 단위
  > ex) icon을 클릭할때 메모리에 올리고 CPU가 실행하는 상태
* 프로세스의 구조
   	- Stack: - 함수가 호출될때 생성되는 지역변수와 매개변수들이 저장이 됨. 함수 호출이 완료되면 LIFO로 제거됨
   		- 스택은 메모리가 한정되어 있기 때문에 너무 큰 메모리는 할당 할 수 없음(stack overflow).
		- 힙은 데이터 크기를 모를때 스택과 힙은 같은 메모리 공간을 사용함.
	- Heap: - 사용자가 직접 관리하는 메모리 영역. 동적으로 메모리를 할당하고 해제
		- 메모리 해제 반드시 해줘야하는데 ARC 덕분에 안해도 됨.
		- 클래스, 클로져와 같은 Reference Type이 힙에 자동으로 저장됨
		
	- Data: - 전역 변수들, 상수들이 저장되는 영역 
		- read-write
		- 프로그램 시작과 동시에 할당되고 프로그램이 종료되면 해제
	- Text / Code: 실행할 코드(기계어) 가 저장되는 영역..read-only
* 프로세스의 상태
	> New: 프로세스 생성중
	> Running: 실행
	> Waiting: 이벤트(I/O완료) 가 일어나기를 기다림
	> Ready: CPU 할당을 기다림
	> Terminated: 종료
* 스레드란?
	> 스레드는 프로세스의 실행 흐름을 나타내는 단위입니다. 경량화된 프로세스
	> 프로세스 내의 자원을 서로 공유 할 수 있습니다.
	> 스레드는 프로세스 내에서 각각 Stack/Register/Counter 만 따로 할당받고 Code, Data, Heap 영역은 공유한다.
	> 일부의 프로세스가 효율적으로 실행이 되기 위해 여러개의 스레드를 사용 할 수 있습니다
* 스택을 스레드마다 독립적으로 할당하는 이유?
	> 각각의 스레드가 독립적인 작업을 수행해야되기 때문에 각각 고유의 스택을 갖고있는것으로 알고있습니다. 스레드마다 함수호출을 하기 때문에
* 멀티스레딩과 멀티프로세싱의 차이
* CPU의 역할
* 커널이란?
  > 메모리에 상주하는 운영체제의 부분. 운영체제의 모든 부분들이 동시에 메모리에 올라가있다면 메모리가 너무 차지됨. 그래서 중요한 부분들만 메모리에 올려놓는것.
* 인터럽트란?
  > CPU에게 하고있는 일을 중단하고 다른 일을 하도록 시키는 신호입니다.
  > 예를 들면 CPU 가 어떠한 작업을 수행하고 있는 도중에 인터럽트 신호가 오면, 하고있던 일을 멈추고 인터럽트 신호를 먼저 처리합니다.
  > 인터럽트가 한 번에 여러개가 오는 경우가 있을 수 밖에 없기 때문에, 인터럽트에 우선순위를 매겨서, 우선순위가 높은 인터럽트부터 차례대로 처리를 해줍니다.
* DMA란
  > 디바이스를 이용할때 메모리에 자주 접근을 하는데, 이걸 CPU가 중간에서 중재를 해줍니다. 디바이스가 CPU 한테 데이터를 요청하면, CPU는 메모리에 가서 해당 데이터를 가져오고 그걸 디바이스한테 전달하는, 그런 방식으로 데이터가 이동이되는데, CPU가 여러 가지 일을 한번에 많이 처리 하다보니까 매번 그렇게 데이터를 메모리에서 꺼내오는게 오래걸릴 수 있습니다. 그래서 Direct Memory Access 를 통해, 디바이스가 CPU를 거치지않고 바로 메모리에 가서 데이터를 가져오는걸 말합니다.
* 프로세스 제어 블럭이란(PCB)?
	> 프로세스가 인터럽트에 의해서 중간에 끊기는 상황이 있을 수 있는데, 그럴때 프로세스의 진행상황을 어딘가에 저장해야되는데 그걸 저장하는 곳이 프로세스 제어 블럭입니다.
	> 프로세스가 생성될때 함께 생성이되고, 프로세스마다 각자 고유의 process control block을 갖고있다고 볼 수 있습니다.
	> 프로세스 상태, CPU 스케쥴링 정보 등을 저장

* 스레드를 사용해본 경험?
* 프로세스 스케쥴링이란?
	> CPU가 다음에 어느 프로세스를 실행할지 결정하는 것
	> 프로세스 큐로 스케쥴링을 진행
		> Job Queue: 현재 시스템에서 돌고있는 프로세스들의 집합 
		> Ready queue : Ready 상태의 프로세스들이 CPU의 선택을 받기위해 줄을 서있는 것 (연결리스트 형태)
		> Device queue:  하드디스크의 접근을 위해 프로세스들이 기다리는 줄

* 스케쥴러의 종류
	> Short-term(단기): 다음 프로세스를 선택
	> Long-term(장기): 다음 ready queue에 넣을 프로세스를 선택
	> Mid-term(중기): 여유 공간 부족시, 디스크로 옮김. .멀티프로그래밍의 수를 줄일때
* 스케쥴링 알고리즘
	> CPU의 이용률을 높이는 방법
	> 선점형 방식과 비선점형 방식으로 나눌 수 있는데, 선점형 방식은 우선순위가 높은 프로세스가 도달하면 그 즉시 그 프로세스에게 CPU를 할당. 빼앗아오는것
	> 비선점형 방식은 Ready Queue의 맨 앞에 그 프로세스를 등록. Starvation과 CPU를 사용못하는 프로세스를 CPU가 무한 대기하는 상태가 있을 수 있음. 오래 기다렸을 경우 우선순위를 높이는 Aging을 통해 해결 가능. 다른 프로세스 영향 못끼침 
* 스케쥴링 알고리즘 종류
	> - 선입선처리 (First Come First Served) : 먼저 온 녀석이 먼저 스케줄링을 받음. 중간에 반환하지 않는 비선점형이며, 시간이 긴 프로세스가 먼저 오면 효율성이 떨어짐.. 문제점은 먼저 들어온 애가 CPU를 오래잡고있으면 뒤에 애들이 대기 시간이 길어진다 
	> - 최단작업우선 (Short Job First) : 실행시간이 짧은 프로세스 부터 먼저 할당 해주는 것. 문제는 다음 CPU버스트 시간을 알기 힘들다. 늦게 오더라도 수행시간이 짧은 프로세스에 먼저 할당. 이렇게 되면 수행시간이 긴 프로세스는 영원히 할당받지 못할 수도 있음(Starvation)
	> - 최소 잔여 시간 우선 (Short Remaining Time) : 현재 프로세스의 수행시간이 끝나는 시간보다 나중에 오는 프로세스의 수행시간 완료 시간이 더 짧다면, 그 즉시 그 프로세스에게 CPU를 할당. 선점형 스케줄링. Starvation과 CPU 수행 시간을 측정할 수 없다는 문제가 있음 
	> - Round Robin : 현대적인 CPU 스케줄링으로, 선입선처리의 문제점을 개선한 방법. 각 프로세스에게 CPU 할당 시간을 지정해준다. 할당량만큼 실행하고 다시 Ready 큐 맨 뒤로 들어감.
각 프로세스는 동일한 CPU 할당 시간을 갖게 됨. 할당시간 만료시 ready queue 맨 뒤에 가서 줄섬. CPU의 사용시간이 제각각일 때 효율적. 반응 속도가 빨라지며, 공정한 스케줄링. 주의할 점은 할당하는 시간(time quantum)이 너무 길다면 FCFS와 다를게 없음. 너무 작다면 잦은 컨텍스트 스위칭이 발생.

* Context Switching(문맥 교환) 이란?
	> - 프로세스의 전환을 의미함. 전환이 일어날때 기존 프로세스의 상태를 저장하고 새 프로세스의 상태를 읽어오는것
	> - 순수 Overhead: 프로세스의 진행은 전혀 안이루어짐. (바뀌기만 함) 
	> - PCB가 복잡해질수록 context switch도 복잡해진다
	> - HW 지원이 있으면 개선 될 수 있다(CPU내 레지스터가 다수 세트 있을때)
	- 자주 일어날수록 좋을까??
		> 장단점이 있다. 자주 일어나면 프로세스들이 마치 동시에 실행되는것 처럼 자연스럽다. 하지만 단점으로는, overhead가 높다. CPU의 성능을 계속 거기에만 사용해야함. 즉, 프로세스가 느려짐(진행이 안됨)

* 멀티프로세싱
	> 하나의 CPU가 여러개의 프로세스를 마치 동시에 일어나는것 처럼 처리하는 것
	- 장단점?
		> 프로세스는 각각의 독립된 메모리 영역을 할당받았기 때문에 프로세스 사이에서 공유하는 메모리가 없습니다.
		- 장점: 여러개의 프로세스 중에 하나가 죽어도, 딱히 영향이 없습니다
		- 단점: - 프로그램이 프로세스 사이를 왔다갔다하는게 문맥 전환(Context Switching)인데, -> 오버헤드가 높다
		       
* 멀티스레딩
	> 하나의 프로세스 안에서 여러개의 스레드를 사용하여 작업을 처리하는것
	> 하나의 프로세스가 다수의 작업을 동시에 수행
	- 장점: - 시스템의 성능을 최대로 활용 할 수 있다
		- 스레드들은 프로세스의 자원을 공유하기 때문에 프로세스 간의 통신(IPC) 보다 훨씬 효율적이고 빠르다
		- 프로세스를 이용하여 동시에 처리하던 일을 스레드로 구현할 경우 메모리 공간과 시스템 자원 소모가 줄어들게 된다.
		- 응답성, 자원 공유, 
		- 경제성: 프로세스에 비해 생성이 가볍고 문맥교환도 쉽다
		- Scalablilty: 멀티프로세서 시스템에서 더 좋은 성능을 보인다
	- 단점: - 같은 자원을 공유하기 때문에 하나의 쓰레드가 오류를 만들면 자칫하면 나머지 쓰레들도 죽을 수 있다.
	       - 같은 자원을 공유하기 때문에 관리하기 힘들다
	       - 동기화 작업을 주의 깊게해야된다(작업 처리 순서 컨트롤)
	       - 디버깅이 어렵다
* 멀티프로세스와 멀티스레드의 차이
	>멀티스레딩은 멀티 프로세스보다 적은 메모리 공간을 차지하고 문맥 전환이 빠르다는 장점이 있지만, 오류로 인해 하나의 스레드가 종료되면 전체 스레드가 종료될 수 있다는 점과 동기화 문제를 안고 있다. 반면 멀티 프로세스 방식은 하나의 프로세스가 죽더라도 다른 프로세스에는 영향을 끼치지 않고 정상적으로 수행된다는 장점이 있지만, 멀티 스레드보다 많은 메모리 공간과 CPU 시간을 차지한다는 단점이 존재한다
* 동기와 비동기의 차이
	> 함수를 호출 했을때 작업 완료의 여부를 신경쓰는지 신경을 안쓰는지로 나뉩니다.
	> 동기식 일처리는 요청에 대한 응답을 기다린 후, 응답이 오면 다음 요청을 하는 방식. 
	> 비동기식 일처리는 요청에 대한 응답을 기다리지 않고, 다음 동작을 진행함
	
	

* 동기와 비동기의 장단점?
	> 동기식은 구성이 단순하고, 순서대로 실행 가능함.. 하지만 여러 일을 동시에 수행하는 멀티태스킹은 불가하다..
	> 비동기식은 동시에 여러 일을 수행 할 수 있지만, 일정 시간당 요청량이 많아질 경우, 부하가 발생할 수 있으며, 이를 위한 추가적인 처리가 필요할 수 있음 (코드의 복잡도가 올라갈 수 있다)

* 임계영역
	> 임계영역은 멀티스레딩을 할 때 발생하는 문제에 대한 이야기인데요. 하나의 프로세스 안에 있는 여러 스레드들은 그 프로세스의 자원을 함께 쓰게 되는데 그런 작업의 영역을 임계영역이라고 부릅니다.
* 임계영역의 해결조건
	> 상호 배제: 한 프로세스가 임계구역에서 실행되면 다른 프로세스는 그들의 임계 구역을 실행 할 수 없다
	> 진행: 임계구역에 있는 프로세스가 없으면 나머지 프로세스들이 다른 동작이 없다면 임계영역에 진입 할 수 있는 후보에 오른다.
	< 한정된 대기: 프로세스가 임계구역 진입 요청을 한 후 요청이 허용될 때 까지 다른 프로세스들이 Critical Section 에 진입하는 횟수는 제한이 있어야 한다.
* 임계영역의 문제: 어떻게 하면 멀트스레딩에서 스레드들이 오류 없이 프로세스의 자원들을 잘 쓸 수 있게 프로토콜을 제공하는지에 대한 문제
* 임계영역의 해결책:
	> - Peterson의 해결안: 두개의 공용 변수 turn, 과 flag를 통해 임계영역 진입을 제어
	> - Mutex: - 상호배제(Mutual Exclusion)로 동작하는 Lock
		- 프로세스는 임계구역에 진입할때 Lock를 획득. 나갈때 release().. lock를 갖고있는 프로세스만 임계구역 진입 가능.
		- 바쁜 대기가 단점
	> - Lock
		- 뮤택스는 lock이 가능한 객체고, lock은 그걸 유지하는 객체. 하드웨어 기반
		- 한계: Multiprocessor 에서는 Lock을 사용하면 시간 효율성이 낮아서 좋지 않다
	> - 세마포어
		- 소프트웨어 측면에서 임계구역 문제를 해결을 하려고하는 동기화 도구. 뮤텍스보다 조금 더 정교함.
		- 뮤텍스와는 다르게 프로세스들간의 signal이 가능해서 프로세스 실행 순서를 조금 더 효율적으로 제어를 할 수 있다. 뮤텍스는 너무 대기가 많음.
		- Counting 세마포어 : 자원에 접근 할 수 있는 쓰레드의 limit을 정해두고 count를 통해 관리 하는 방법
		- 이진 세마포어: 는 말그대로 0 과 1 두가지 값만 가능해서 .. 어떻게 보면 boolean으로 생각해도 될것 같습니다. 1이면 임계영역을 접근하고 있는 스레드가 있는거고 0이면 임계영역을 접근하고 있는 스레드가 없으니까 접근이 가능한 상태
		- 왜 sleep()를 사용할까?
			-안그러면 계속 while문으로 임계구역에 진입해도되는지 확인해야할텐데 그러면 너무 cpu 낭비가 심함.
	> - Monitor
		- 잘못된 세마포 사용을 처리하는 동기화 도구
		- 특정 공유 자원을 프로세스에게 할당하는데 필요한 절차
	- 이진 세마포어 와 Mutex의 차이?
		> 비슷한 개념이지만. Mutex를 소유하고있는 쓰레드가 직접 release해야하고, 즉 lock을 사용 해야되는거고, 이진 세마포는 그냥 어떤 쓰레드던 signal 을 통해 할 수 있다.
		> 세마포어는 뮤택스로 사용 될 수 있는데, 반대로 뮤택스는 세마포어로 사용 될 수 없다
* Deadlock
	> 둘 이상의 프로세스가 무한히 대기하고있는 상태.
	> 임계영역을 대기하고있는 프로세스가 2개 이상 있고 임계영역에서 실행되고있는 프로세스가 빠져나오려면 대기하고있는 프로세스가 실행되어야하는 상황
	- 예방을 위해 데드락의 4가지 조건 중에 하나를 제거
	- 데드락의 발생 조건 4가지(모두 만족해야 함) :
		- 상호 배제 : 한 자원은 한 프로세스에 의해서만 사용됨, 두 개 이상 사용 불가
		- 점유 대기 : 프로세스는 자원을 가진 채 다른 자원을 기다릴 수 있음
		- 비선점 : 다른 프로세스가 사용 중인 자원을 강제로 가져올 수 없음
		- 순환 대기 : 프로세스의 집합에서, 각 프로세스는 순환적으로 다음 프로세스가 필요로 하는 자원을 가지고있다.
	- 데드락 해결법 :
		-예방 : 4가지 조건 중 하나라도 만족되지 못하게 함
		-회피 : 알고리즘을 데드락이 발생하지 않도록 적용
		-회복 : 교착상태가 발생하면 그때 해결함
		-무시 : 회복과정의 성능저하가 더 심하다면 그냥 무시함
* Starvation(기아) 현상
	> 프로세스 / 스레드가 세마포 큐에서 무한히 대기하는 상황
* 메모리 구조의 순서가 어떻게 되는가?
	> CPU에서 가까운 순으로 말해보시오.
* First Fit, Best Fit, Worst Fit에 대해서 설명해 보시오.
	> 동적 할당 정책
	> - First Fit: 첫 번째 사용 가능 공간
	> - Best Fit: 사용 가능한 곳 중 가장 작은 공간
	> - Worst Fit: 가장 큰 가용공간 선택
* 외부 단편화란? 내부 단편화란?
	> - 외부 단편화: 안쓰는 공간이 너무 작고 분산 되어 낭비 되는 현상
	> - 내부 단편화: 필요한 최소 공간 보다 조금 더 여유롭게 할당이 되면서 낭비되는 공간
	> - 해결책: 페이징(할당 된 공간 안에서 낭비)
* 페이징이란?
	> 연속되지 않은 물리 주소 공간 관리 방법..
	> 곳곳에 잉여 메모리를 합해서 사용 가능한 메모리로 만들어주는 것
	- 방법: 
	> - 물리 메모리를 frame 단위로 나눈다 (512바이트~16메가바이트)
	> - 논리 메모리를 페이지라는 같은 크기의 블록으로 분할
	> - N개의 페이지를 필요로 하면 N 프레임을 할당
	> - 페이지 테이블(논리 주소를 물리 주소로 변환) MMU
* Segmenation: 페이징에서처럼 논리 메모리와 물리 메모리를 같은 크기의 블록이 아닌, 서로 다른 크기의 논리적 단위인 세그먼트(Segment)로 분할. 사용자가 두 개의 주소로 지정(세그먼트 번호 + 변위) 세그먼트 테이블에는 각 세그먼트의 기준(세그먼트의 시작 물리 주소)과 한계(세그먼트의 길이)를 저장
* 가상 메모리란?
 > 다중 프로그래밍을 실현하기 위해서는 많은 프로세스들을 동시에 메모리에 올려두어야 한다. 가상메모리는 프로세스 전체가 메모리 내에 올라오지 않더라도 실행이 가능하도록 하는 기법 이며, 프로그램이 물리 메모리보다 커도 된다는 주요 장점이 있다
* 가상 메모리가 하는 일
	> 가상 메모리는 실제의 물리 메모리 개념과 사용자의 논리 메모리 개념을 분리한 것으로 정리할 수 있다. 이로써 작은 메모리를 가지고도 얼마든지 큰 가상 주소 공간을 프로그래머에게 제공할 수 있다.
</br>
