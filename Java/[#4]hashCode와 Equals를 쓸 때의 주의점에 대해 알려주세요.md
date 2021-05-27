이 질문을 답변하기 위해서는 우선 Hashcode와 Equals를 이해해야 한다.

먼저, Hashcode는 대상 객체의 해시값을 리턴해준다. 이 때 해싱을 진행하는 방법이 여러 가지가 있는데, 보통은 자리수마다 소수를 곱해서 더하는 형식의 계산으로 해싱을 한다. 소수를 곱하는 이유는 해시 충돌을 방지하는 방법 중 알려진 가장 좋은 방법 중 하나가 소수를 이용하는 것이기 때문이다.
```java
public int hashCode() {
    int h = hash;
    if (h == 0 && value.length > 0) {
        char val[] = value;

        for (int i = 0; i < value.length; i++) {
            h = 31 * h + val[i];
        }
        hash = h;
    }
    return h;
}
```

다음으로 Equals는 비교대상들이 논리적으로 같은지를 리턴해준다. 이 때, Object는 단순히 ==으로 비교를 하고, Object를 extend한 클래스 들에서 적적하게 오버라이드해서 Equals를 정의하고 있다.
```java
public boolean equals(Object anObject) {
    if (this == anObject) {
        return true;
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
}
```
### 주의점

hashCode를 쓸 때의 주의점은 다음과 같다. 

1. 논리적으로 같은 객체들의 hashCode은 같아야 한다. 그래야 해시맵에 같은 키로 들어간다.

2. 해시코드를 구하는 내부로직을 외부에 가급적이면 공개하지 말아야 한다. 알 필요도 없거니와 해시코드를 만드는 법이 바뀔 수도 있고 해시코드를 구하는 로직에 의존성을 가지게 할 필요가 없다. 

Equals를 쓸 때의 주의점은 다음과 같다. 지키지 않고 막 쓰게되면 랜덤박스마냥 어떨 때는 true이고 어떨때는 false가 나오는 대환장 파티를 마주할 수 있다.

1. 재정의하지 않아도 되면 안하는게 제일 좋다. 
    * 각 인스턴스가 본질적으로 고유한 경우
    * 인스턴스의 논리적 동치성을 검사할 필요가 없는 경우
    * 상위 클래스에서 구현한거 써도 문제 없는 경우    
2. 재정의해야 한다면 다음 사항을 만족해야 한다
    * null이 아니면 스스로 비교했을 때 true가 나와야 한다
    * null이 아닌 x,y객체의 경우 x.equals(y)와 y.equals(x)가 같아야 한다
    * x,y,z가 있을 때 x.equals(y)와 y.equals(z)가 같으면 x.equals(z)도 같은 값이 나와야 한다
    * null이 아닌 경우 몇번을 호출하든 일관성있는 경과가 나와야 한다
    * null이랑 비교하면 false가 나와야 한다

이까지 읽고 나면 위에 구현한 equals가 꽤 잘 구현한 코드임을 알 수 있다
```java
public boolean equals(Object anObject) {
    if (this == anObject) {
        return true; //스스로 비교했을 때 true 만족
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) { 
            //x,y비교 만족, x,y,z비교 만족, 일관성 만족
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false; //null이랑 비교했을 때 false 만족
}
```