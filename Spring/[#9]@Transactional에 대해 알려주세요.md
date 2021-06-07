많은 어노테이션들이 그렇듯이, Transactional 또한 프록시 패턴을 사용하여 객체를 감쌉니다.

이를 통해서 사용자들이 커넥션을 열고 닫는 행위보다는 핵심 비즈니스 로직에 더 집중할 수 있게 되는데, Transactional의 대략적인 형태는 다음과 같습니다

```java
try{
    open connection
    business logic
} catch(Exception e){
    rollback
} finally{
    close connection
}
```

비즈니스 로직 상에서 예외가 터졌을 때 롤백을 하는 구조를 취하고 있다고 볼 수 있어요. 

데이터베이스 트랜잭션의 성질은 ACID라고 해서 Atomicity, Consistency, Isolation, Durability를 의미하는데요, @Transactional의 기본 구조를 통해 Atomicity를 보장하게 되는 것이죠.

Isolation의 정도를 정해줄 수도 있습니다. 병렬성이 낮은 순서대로 Read UnCommitted, Read Committed, Repeatable Read, Serializable이 있는데, 각각의 격리정도가 무엇을 의미하는 지는 별도의 자료로 학습하는 것을 권장합니다.

이 외에 Propagation의 정도 또한 정해줄 수 있습니다. 트랜잭션 도중에 다른 트랜잭션을 수행해야 하는 상황일 때 어떻게 할지를 정해주는 것으로, 새로운 트랜잭션을 만들지, 잠시 보류할지, 아니면 아예 트랜잭션을 만들지 않을 지를 정해줄 수 있습니다. 기존 트랜잭션을 잠시 보류하고 새로운 트랜잭션을 우선적으로 수행하는 등의 작업 또한 가능하기 때문에 비즈니스 로직에 따라 옵션을 조절해야 될 때가 있습니다.

그 외에도 쿼리의 타임아웃시간을 정해주거나 데이터를 읽기 전용으로 가져오거나 롤백하거나 롤백하지 않는 예외 상황을 지정해줄 수 있습니다. 