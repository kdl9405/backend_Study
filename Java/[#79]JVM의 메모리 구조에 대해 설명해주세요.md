#   JVM의 메모리 구조
JVM의 메모리는 Runtime Data Areas라고 불립니다.
JVM의 메모리는 공유 자원과 스레드 자원으로 구성되어 있습니다.

공유 자원 : Heap, Method
스레드 자원 : Stack, PC Registers, Native Method Stack

- `Memory`
  - `Stack`
    - 스레드마다 런타임 스택 생성
    - 메소드 호출을 스택 프레임으로 쌓음
    - 스레드가 종료되면 런타임 스택도 사라짐
  - `PC Registers`
    - 스레드마다 현재 실행할 명령어의 위치를 가리키는 포인터 생성
  - `Native Method Stack`
    - C, C++과 같은 라이브러리의 메소드가 머무릅니다.
  - `Heap`
    - 공유 자원
    - 객체 저장
  - `Method`
    - 공유 자원
    - 클래스 수준의 정보 저장
  
##  Heap Area

- JVM의 `Runtime Data Areas`에서 `Heap`은 객체를 저장합니다.
- 객체에 대한 참조 변수는 `Stack`에 있습니다.

###  Oracle의 HotSpot VM의 Heap 구조
- `Young Generation`
  - `Eden`
    - 객체가 최초로 할당되는 장소
    - Eden이 포화상태이면 참조중인 모든 객체를 Survior로 옮깁니다.
    - Survivor로 참조중인 객체가 모두 옮겨지면 Garbage Collection(`Minor GC`) 수행합니다.
  - `Survivor`
    - `Survivor 1`, `Survivor 2`로 이뤄져 있습니다.
    - 참조중인 객체들은 하나의 Survivor 영역만 사용합니다.
- `Old Generation`
  - `Survivor` 에서 오랫동안 참조되고 있는 객체는 `Tenured`로 이동합니다.
  - `Tenured`에 온 객체는 앞으로도 오랫동안 참조될 가능성이 높기 때문에 메모리 상에서 계속 머무릅니다.
  - `Tenured` 의 메모리가 포화상태에 이르면 참조하고 있지 않는 객체에 대한 Garbage Collection(`Major GC` == `Full GC`)이 이뤄집니다.
- `Metaspace` : 메타 정보가 저장됩니다.