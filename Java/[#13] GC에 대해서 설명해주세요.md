## Java의 Garbage Collection

## 개요
- 자바의 메모리 관리 방법입니다.
- 자바의 객체는 `Runtime Data Areas`의 `Heap`에 할당됩니다.
  - [JVM의 Heap Area](https://joojeongyong.tistory.com/106)
- 자바는 개발자가 메모리를 관리하지 않습니다.
- `Garbage Collector`가 객체의 메모리를 해제합니다.
- GC가 수행될 때, GC를 위한 스레드를 제외하고 모든 스레드의 작업이 중지됩니다(`Stop the World`).
- GC 튜닝은 `Stop the World`의 시간을 줄이는 것입니다.

## 가설 : Weak Generational Hypothesis
- 대부분의 객체는 금방 `접근 불가능 상태(unreachable)`가 됩니다.
- 오래된 객체에서 젊은 객체로의 참조는 아주 적게 존재합니다.

## GC
- 대부분의 객체는 Young 영역에서 GC(Minor GC)됩니다.
- Young 영역의 GC 대상을 판별할 때, Old 영역의 객체가 참조하는지 식별하기 위해서 카드 테이블이라는 청크를 확인합니다.
- Old 영역의 메모리가 포화상태에 이르면 GC(`Major GC` == `Full GC`)가 이뤄집니다.

##  Old 영역에 대한 GC
- `Serial GC`
  - 싱글스레드를 활용하여 GC를 수행합니다.
  - 멀티 프로세서를 활용할 수 없습니다.
  - `Serial GC는 가능한 한 절대로 사용하지 않아야 합니다.`
- `Parallel GC`
  - 병렬로 Major GC를 수행합니다.
- `Concurrent Mark & Sweep GC`
  - 일시 정지 시간이 짧습니다.
  - GC 작업과 프로세스 리소스를 공유할 수 있습니다.
  - `JDK 9부터 사용하지 않습니다.`
- `G1(Garbage First) GC`
  - 멀티 프로세스 프로그램을 위한 GC입니다.
  - 높은 처리량을 보여줍니다.
- `Z GC`
  - `JDK 11`에서부터 실험적으로 도입되었습니다.
  - `scalable low latency` GC입니다.
  - 모든 종류의 비싼 작업을 동시에 수행하며, 스레드를 중지하지 않는다는 특징이 있습니다.

##  참고자료
[기계인간 위키](https://johngrib.github.io/wiki/garbage-collection/)
[Java Garbage Collection, 네이버 D2](https://d2.naver.com/helloworld/1329)