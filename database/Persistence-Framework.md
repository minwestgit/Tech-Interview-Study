## Persistence Framework

JDBC 프로그래밍의 복잡함이나 번거로움 없이 간단한 작업만으로 **데이터베이스와 연동되는 시스템을 빠르게 개발할 수 있으며 안정적인 구동을 보장**한다. Persistence Framework는 SQL Mapper와 ORM으로 나눌 수 있다.

- SQL Mapper : SQL 문장으로 직접 데이터베이스 데이터를 다룬다.즉, SQL Mapper는 SQL을 명시해줘야 한다.<br>
  ex) Mybatis 등

- ORM(Object-Relational Mapping) : 객체와 관계형 데이터베이스의 데이터를 자동으로 매핑(연결)해주는 것을 말한다. 
ORM을 이용하면 SQL Query가 아닌 직관적인 코드(메서드)로 데이터를 조작할 수 있다.객체 간의 관계를 바탕으로 SQL을 자동으로 생성한다.Persistant API라고도 할 수 있다.<br>
ex) JPA, Hibernate 등

<br>

JDBC : Java에서 DB 접근할 수 있게 해주는 API<br>
JPA : 자바 ORM기술에 대한 API표준 명세로 Java에서 제공하는 API<br>
하이버네이트 : JPA 구현체
