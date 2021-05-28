# Overriding과 Overloading에 대해서 말해주세요

### 1. Overloading

    OverLoading은 함수의 다형성을 지원하기 위한 것입니다.

    같은 이름의 메소드에 매개 변수의 타입이나 개수를 다르게 설정하여 동일한 기능을 처리할 ()수 있습니다.

    예를 들면, Java의 System.out.println()의 메소드가 있습니다.

    매개 변수의 타입이 int여도, String이여도 모두 같은 메소드를 호출하고 동일한 기능을 수행합니다.

    이러한 다형성을 지원하는 것이 OverLoading 입니다.
<br>

### 2. Overriding

    Overriding은 부모 클래스로부터 상속받은 메소드를 자식 클래스에서 재정의 하는 것입니다.

    객체 지향 프로그래밍에서 다른 클래스를 상속받는 경우가 많이 있고, 상속 받은 메소드를 그대로 사용하지 않고 수정해야 하는 경우도 있습니다.

    이렇듯 상황에 맞게 메소드를 수정해야 할 때, Overriding를 사용합니다.
<br>

### 3. 비교

    Overloading와 Overriding 모두 다형성을 지원하기 위한 것입니다.

    따라서 둘 모두 같은 이름의 메소드를 활용합니다.

    그러나 Overloading은 기존 메소드와 다른 매개변수(개수, 타입)을 사용해야 하는 반면,

    Overriding은 같은 매개변수를 사용합니다.

    또한 리턴 타입에 대해서도, Overloading은 달라질 수 있으나 Overriding은 동일해야 합니다.
<br>

### 4. 사용 조건

    Overloading 

    - 메소드의 이름이 같아야 한다.
    - 매개변수의 개수나 타입이 달라야 한다.
    - 리턴 값만 다른 것은 Overloading 할 수 없다.

    Overriding  

    - 메소드의 이름, 매개변수, 리턴 값이 모두 같아야 한다.
    - @Override 어노테이션 표기
    - 부모의 접근자 이상의 범위를 가져야 한다.