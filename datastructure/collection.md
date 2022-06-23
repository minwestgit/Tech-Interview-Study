## 컬렉션 인터페이스의 상속 구조와 각각의 특징

![image](https://user-images.githubusercontent.com/70561950/175332297-2a9cb378-dcbc-488d-b73b-9d61fe268e29.png)

### Collection
데이터의 집합, 그룹을 나타내며, 하위 인터페이스로 List, Set이 있다. Map은 컬렉션 처럼 키와 값들을 검색하는 메서드들을 갖지만 “엘리먼트들의 그룹”이라는 컬렉션 인터페이스의 기본 개념과 맞지 않아 별도로 정의. 자료구조 + 메소드 묶어 놓은 것
- **List**: 순서가 있는 데이터의 집합으로 데이터의 중복을 허용.
    - **ArrayList** - 배열 기반. 동기화X. 검색 빠르고 삽입, 삭제 느림
    - **LinkedList** - ArrayList의 단점인 추가, 삭제 기능을 노드를 이용하여(양방향 포인터 구조) 향상시킴. Queue 인터페이스와 List 인터페이스를 모두 구현함
    - **Vector**: ArrayList와 비슷한데 동기화 처리가 되어 성능때문에 잘 사용하지 않음
- **Set**: 순서가 없는 데이터 집합으로 중복을 허용하지 않음(저장 순서 유지 X).
    - **HashSet**: Set 인터페이스를 구현한 대표적인 컬렉션 클래스. Tree보다 빠름(Tree는 정렬 유지하므로)
    - **TreeSet**: 이진 탐색 트리(binary search tree)로 구현된 클래스로 범위 탐색과 정렬에 유리. 저장시 정렬되므로 오래 걸림.
    - **LinkedHashSet**: HashSet에 순서 기능 향상(저장 순서 유지)
- **Map**: 키(Key), 값(Value)의 쌍으로 이루어진 데이터의 집합으로 순서는 유지되지 않으며 키(Key)의 중복을 허용하지 않으나 값(Value)의 중복은 허용. 검색속도 빠름
    - **HashMap**: ArrayList와 LinkedList의 장점을 합쳐서 만든 클래스이며, 해싱 기법을 사용하여 검색이 빠름. Tree보다 빠름(Tree는 정렬 유지하므로). null 허용
    - **TreeMap**: TreeSet와 비슷한 개념으로 정렬된 순서대로 엔트리를 저장하여 범위 검색과 정렬에 유리함. key값 기준 빠른 검색 가능. 이진탐색트리로 구현. 저장 시 정렬되므로 오래 걸림.
    - **LinkedHashMap**: HashMap에 순서 기능 향상(저장 순서 유지)
- **HashTable**: Hashtable은 예전에 나온 것으로 동기화O&null허용X, HashMap은 동기화X&null허용O
- **Queue**: 클래스로 구현된 스택과는 달리 자바에서 큐 메모리 구조는 별도의 인터페이스 형태로 제공한다. 선입선출(FIFO) 형태이며, 하위 인터페이스로 Deque 등이 있고 구현한 클래스로 LinkedList 등이 있다.
- **Stack**: List 컬렉션 클래스의 Vector 클래스를 상속받아, 전형적인 스택 메모리 구조의 클래스를 제공한다. 후입선출(LIFO) 형태
