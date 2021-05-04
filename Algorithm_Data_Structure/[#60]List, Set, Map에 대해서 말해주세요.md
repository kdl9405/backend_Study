## 1. List, Set, Map에 대해서 말해주세요

    Java Collection의 주요 인터페이스로 Java에서 데이터를 저장하는데 사용되는 기본적인 자료구조입니다.
    List는 순서가 있는 데이터 집합으로 데이터의 중복을 허용하는 자료구조입니다.
    반면, Set는 순서가 없는 데이터 집합이며 데이터의 중복을 허용하지 않습니다.
    Map은 Key와 Value로 이루어지고 순서를 유지하지 않는 데이터 집합입니다.
    Key에 대해서는 중복을 허용하지 않으나, Value의 중복은 허용합니다.

## 2. List에 속한 자료구조에 대해서 간단히 설명해주세요

    대표적으로 ArrayList와 LinkedList가 있습니다.
    ArrayList는 기존 배열과는 다르게 메모리가 자동으로 늘어나는 자료구조입니다.
    배열처럼 Index를 갖고 있어 데이터의 조회와 순차적인 데이터 삽입,삭제에 대해서 빠른 속도를 보이며, 단방향 포인터 구조입니다.
    반면 LinkedList는 양방향 포인터 구조로, 데이터의 탐색에서는 ArrayList보다 느린 속도를 보이지만 중간 데이터의 삽입, 삭제에 대해서는 빠른 속도를 보입니다.
    이외에 Stack과 Vector가 있습니다.


## 3. Set에 속한 자료구조에 대해서 간단히 설명해주세요.

    Set에는 HashSet, LinkedHashSet, TreeSet이 있습니다.
    HashSet은 데이터의 중복을 막고, 순서를 보장하지 않는 자료구조입니다.
    LinkedHashSet과 TreeSet보다 성능이 더 빠르고, 더 적은 메모리를 사용합니다.
    LinkedHashSet은 HashSet을 상속받아 구현됩니다.
    HashSet과는 다르게 저장된 순서를 보장하여, 삽입된 순서대로 데이터를 관리합니다.
    반면 TreeSet은 정렬을 지원하는 자료구조입니다.
    이진 탐색 트리(Red-Black Tree) 형태로 데이터를 저장하여, 데이터의 삽입되 동시에 정렬합니다.
    따라서 데이터의 삽입과 삭제에는 더 많은 시간을 필요로 합니다.


## 4. Map에 속한 자료구조에 대해서 간단히 설명해주세요.

    Map에는 HashMap, LinkedHashMap, HashTable, TreeMap이 있습니다.
    HashMap은 대표적인 Map Collection으로 데이터를 Array형태로 저장합니다.
    Key와 Value에 null값을 허용하며 저장되는 순서를 보장하지 않습니다. 중복된 Key에 대해서는 중복저장을 허용하지 않지만 마지막 값이 저장됩니다.
    LinkedHashMap은 HashMap에 저장된 순서를 보장하는 자료구조입니다.
    HashTable은 null값을 허용하지 않고 동기화를 지원하는 자료구조입니다.
    그러나 동기화 지원에 따라 느린 속도를 보입니다.
    TreeMap은 이진탐색트리 구조이며, 정렬된 순서로 Key/Value값을 저장합니다.




