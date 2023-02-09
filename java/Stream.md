## Stream
Stream은 JDK 8부터 추가된 기능으로 컬렉션, 배열등의 저장 요소를 하나씩 참조하며 함수형 인터페이스(람다식)를 적용해 반복적으로 처리할 수 있도록 해준다. Stream을 사용하면 불필요한 for, if문 대신 한 줄로 처리할 수 있어 가독성이 좋아진다.

Stream은 다음과 같은 특징을 가진다.
- 원본의 데이터를 변경하지 않는다.
- 일회용이다.
- 내부 반복으로 작업을 처리한다.

Stream은 `객체 집합.스트림생성().중간연산().최종연산();` 의 형태로 사용된다.

### 스트림 생성
Collection 인터페이스에는 stream()이 정의되어 있기 때문에, Collection 인터페이스를 구현한 객체들(List, Set 등)은 모두 이 메소드를 이용해 Stream을 생성할 수 있다.
stream()을 사용하면 해당 Collection의 객체를 소스로 하는 Stream을 반환한다.
```java
List<String> list = Arrays.asList("a", "b", "c");
Stream<String> listStream = list.stream();
```
<br>

### 중간 연산
Stream 객체 요소들을 가공하기 위한 연산이다. 
파라미터로는 앞서 설명하였던 함수형 인터페이스들이 사용되며, 여러 개의 중간연산이 연결되도록 Stream을 반환한다.

- filter
조건에 맞는 값만 반환한다. boolean 값을 리턴하는 람다식을 넘겨 true인 데이터만 반환한다.
  ```java
  list.stream().of(1,2,3,4,5,6)
               .filter(s -> s > 3)
               .collect(toList());
  ```

- map
요소를 1:1로 다룬다. 각 요소에 람다식을 적용해 새로운 Stream 객체를 반환한다.
  ```java
  list.stream().filter(v -> ((v % 2) == 0))
               .map(v -> v * 10)
               .forEach(System.out::println);
  ```

- sorted
요소들을 정렬한다.
  ```java
  list.stream()
      .sorted();

  list.stream()
      .sorted(Comparator.reverseOrder()) //역정렬
  ```

- distinct
중복을 제거한다.

- peek
스트림 요소에 영향을 주지 않고 특정 작업을 수행한다. 결과에는 영향을 주지 않는다.
특정 Stream 요소들을 중간에 출력하기 원할 때 사용할 수 있다.

- skip
처음 n개 요소를 제외한다.
<br>

### 최종 연산
- count, min, max, sum, average

- collect
스트림 연산 값을 List, Set 등의 컬렉션으로 바꿔준다.
ex) toMap, toSet, toList, joining 등

- match
스트림 요소들이 특정 조건을 충족하는지 검사하고 싶을 때 사용한다. match 함수는 함수형 인터페이스 Predicate를 받아서 해당 조건을 만족하는지 검사를 하게 되고, 검사 결과를 boolean으로 반환한다.
  - anyMatch: 1개의 요소라도 해당 조건을 만족하는가
  - allMatch: 모든 요소가 해당 조건을 만족하는가
  - nonMatch: 모든 요소가 해당 조건을 만족하지 않는가

- foreach
스트림 연산 값에 대해 어떤 작업을 하고 싶을 때 사용한다. 다른 메서드처럼 어떤 값을 리턴하지는 않는다.
  ```java
  names.stream()
       .forEach(System.out::println);
  ```

<br>

#### Ref.
https://mangkyu.tistory.com/114 <br>
https://jeong-pro.tistory.com/165 <br>
https://hbase.tistory.com/171
