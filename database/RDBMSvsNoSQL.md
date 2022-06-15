## Q. 대표적인 RDBMS와 NoSQL에는 어떤 것들이 있고, 두 데이터베이스 시스템이 무엇이 다른지 차이점에 대해 설명해주세요

- DBMS(DataBase Management System) : 사용자와 데이터베이스 사이에서 사용자의 요구에 따라 정보를 생성해 주고 데이터베이스를 관리해 주는 소프트웨어
- 스키마 : 데이터베이스를 구성하는 개체(Entity), 속성(Attribute), 관계(Relationship) 및 제약 조건 등에 관해 전반적으로 정의한 메타데이터의 집합

<br>
<br>

### RDBMS(관계형 데이터베이스 관리 시스템)

우선 **SQL(Structured Query Language)** 은 데이터베이스에서 사용하는 쿼리 언어다. SQL을 사용하여 RDBMS에서 데이터를 검색, 저장, 수정, 삭제 등이 가능하다.<br>
**RDB(Relational Database)** 란 관계형 데이터 모델에 기초를 둔 데이터베이스다. 관계형 데이터 모델이란 데이터를 구성하는데 필요한 방법 중 하나로 모든 데이터를 2차원 테이블 형태로 표현해준다.<br>
**RDBMS(Relational Database Management System)** 란 관계형 데이터베이스를 생성하고 수정, 삭제 관리할 수 있는 소프트웨어라고 정의할 수 있다.

<br>

#### 특징

- Data를 Column과 Row형태로 저장한다.
- SQL(Structured Query Language, 구조화 질의어)라는 정교한 검색 query를 통해 데이터를 다룬다.
- Transaction 지원(작업의 완전성을 보장)
- 테이블 간 관계를 가질 수 있다(JOIN)
- 테이블 간 관계를 맺고 있어 JOIN문이 많은 복잡한 쿼리가 만들어질 수 있습니다.
- 반드시 Schema 규격에 맞춰야 한다. (유연한 데이터 저장 X)
- 부하의 분산이 어렵다.
- 성능 향상을 위해서는 서버의 성능을 향상 시켜야하는 **Scale-up만을 지원** → **비용이 기하급수적으로 증가** 할 수 있다.
- 데이터의 분류, 정렬, 탐색 속도가 비교적 빠르다.
- MySQL, SQLite, ORACLE, SQL Server 등 ...

<br>
<br>

### NoSQL(Not Only SQL)

**NoSQL(Not Only SQL)** 은 관계형 데이터베이스와 반대되는 방식을 사용하여 데이터간의 관계(join)를 정의하지 않는다.<br>
RDBMS에서는 스키마에 맞추어 데이터를 관리하여야 하지만 NOSQL은 스키마가 없어 좀 더 자유롭게 데이터를 관리할 수 있다.<br>
NOSQL에서 테이블과 같은 개념으로 컬렉션이라는 형태로 데이터를 관리한다.
<br>

#### 특징
- 데이터간의 관계를 정의하지 않는다. (Table 간의 join 도 불가능)
- RDBMS의 복잡도와 용량 한계를 극복하기 위한 목적으로 등장한 만큼 RDBMS에 비해 훨씬 더 대용량의 데이터를 저장할 수 있다.
- 분산형 구조 : 데이터를 여러 대의 서버에 분산해 저장
- 데이터 분산이 용이하며 성능 향상을 위한 **Scale-up , Scale-out 모두 가**능하다.
- 고정되지 않은 Table Schema (Schema가 없어 다루기 쉬움)
- Key에 대한 put/get 만 지원한다.
- MongoDB, Cassand, Redis 등 ...
  - [https://velog.io/@swhan9404/NoSQL-의-종류별-특징](https://velog.io/@swhan9404/NoSQL-%EC%9D%98-%EC%A2%85%EB%A5%98%EB%B3%84-%ED%8A%B9%EC%A7%95)
  - [https://azderica.github.io/00-db-nosql/](https://azderica.github.io/00-db-nosql/)

- 단점
  - Schema가 없다보니 Data에 대한 규격화된 결과 값을 얻기 힘들다.
  - 데이터 중복이 발생할 수 있으며 중복된 데이터가 변경 될 경우 수정을 모든 컬렉션에서 수행을 해야한다.
  - ACID 트랜잭션 지원 X

<br>
<br>

### 정리
**RDBMS**는 데이터 구조가 명확하며 변경 될 여지가 없으며 명확한 스키마가 중요한 경우 사용하는 것이 좋다. 또한 중복된 데이터가 없어(데이터 무결성) 변경이 용이하기 때문에 관계를 맺고 있는 데이터가 자주 변경이 이루어지는 시스템에 적합하다.
**NoSQL**은 정확한 데이터 구조를 알 수 없고 데이터가 변경/확장이 될 수 있는 경우에 사용하는 것이 좋다. 또한 단점에서도 명확하듯이 데이터 중복이 발생할 수 있으며 중복된 데이터가 변경될 시에는 모든 컬렉션에서 수정을 해야한다. 이러한 특징들을 기반으로 Update가 많이 이루어지지 않는 시스템이 좋으며 또한 Scale-out이 가능하다는 장점을 활용해 막대한 데이터를 저장해야 해서 Database를 Scale-Out를 해야 되는 시스템에 적합하다.
