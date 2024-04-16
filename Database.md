# DB
## Index
1. [RDBMS와 NoSQL](#1-rdbms와-nosql)
2. [정규화](#2-정규화)
3. [쿼리 최적화 및 DB 로직 최소화](#3-쿼리-최적화-및-db로직-최소화)
4. [DDL, DML, DCL](#4-ddl-dml-dcl)
5. [Primary Key, Foreign Key](#5-primary-key-foreign-key)
6. [Redis](#6-redis)
7. [DELETE, TRUNCATE, DROP](#7-delete-truncate-drop)
8. [WHERE, HAVING](#8-where-having)
9. [Oracle과 MySQL](#9-oracle과-mysql)

-- -- --

### 1. [RDBMS와 NoSQL](https://skroy0513.tistory.com/37)
<details>
  <summary>❓ <b><i>RDBMS와 NoSQL의 특징과 차이점에 대해서 장, 단점을 들어 설명해 주세요.</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;RDBMS는 관계형 데이터 모델을 기초로 두고 모든 데이터를 2차원 테이블 형태로 표현하는 데이터베이스입니다. 데이터들이 Column과 Row 형태로 저장되어 있고, SQL이라는 정교한 검색 query를 통해 데이터를 다룹니다. 테이블이 외래 키를 통해 서로 관계를 맺을 수 있으며, 관계를 맺고 있는 테이블 간 JOIN이 사용 가능합니다. RDBMS의 장점은 정해진 스키마에 따라 데이터를 저장해야 하기 때문에 명확한 데이터 구조를 보장하고 있으며, 각 데이터를 중복 없이 한 번만 저장할 수 있습니다. 하지만 단점으로는 시스템이 커져 복잡한 관계를 맺게 되면 JOIN문이 많은 복잡한 쿼리가 만들어질 수 있습니다. 또한 스키마로 인해 데이터가 유연하지 못해서 나중에 스키마가 변경될 경우 번거롭고 어렵습니다. 그리고 성능향상을 위해서는 Scale-up만을 지원하는데 이로 인해 비용이 기하급수적으로 늘어날 수 있는 단점들을 가지고 있습니다.<br>
    &nbsp;&nbsp;NoSQL은 RDBMS와 달리 테이블 간 관계를 정의하지 않습니다. 빅데이터의 등장으로 데이터와 트래픽이 기하급수적으로 증가함에 따라 데이터의 일관성을 포기하되 여러 대의 데이터에 분산하여 저장하는 Scale-out을 목표로 등장하였습니다. 스키마 선언 없이 필드의 추가 및 삭제가 자유로운 Schema-less구조로 유연성이 좋으며, 서버 확장이 용이하고, 대용량 데이터를 처리하는 성능이 뛰어납니다. NoSQL의 장점으로는 스키마가 없기 때문에 유연하며 자유로운 데이터구조를 가질 수 있습니다. 언제든 저장된 데이터를 조정하고 새로운 필드를 추가할 수 있습니다. 또한 데이터 분산이 용이하며 성능 향상을 위한 Scale-up, Scale-out이 가능합니다. 단점으로는 데이터의 중복이 발생할 수 있으며 중복된 데이터가 변경될 경우 수정을 모든 컬렉션에서 수정해야 합니다. 스키마가 존재하지 않기 때문에 명확한 데이터 구조를 보장하지 않으며 데이터 구조 결정이 어려울 수 있으며, key값에 대한 입, 출력만 지원합니다.
  </div>
</details>

### 2. [정규화](https://skroy0513.tistory.com/38)
<details>
  <summary>❓ <b><i>RDBMS의 정규화에 대해 설명해 주세요.</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;데이터베이스에서 튜플을 삭제, 삽입, 수정을 할 때에 이상현상이 발생하게 되는데 이상현상이 발생하는 릴레이션을 분해하여 이상현상을 없애는 과정을 정규화라고 합니다. 정규화의 목표는 테이블 간에 중복된 데이터를 허용하지 않는 것인데, 이걸 통해 무결성을 유지할 수 있고 DB의 저장 용량 역시 줄일 수 있습니다. 테이블을 분해하는 정규화 단계가 정의되어 있고 어떻게 분해되는지에 따라 정규화 단계가 달라지는데, 제1,2,3,4,5 정규화, BCNF정규화가 있습니다.<br>
    &nbsp;&nbsp;제1 정규화는 원자값을 가지고 있어야 하고, 제2 정규화는 부분 함수 종속 제거, 제3 정규화는 이행 함수 종속 제거, BCNF 정규화는 결정자가 후보키가 아닌 함수 종속을 제거, 제4 정규화는 다치 종속 제거, 제5 정규화는 조인 종속 제거를 만족해야 합니다.
  </div>
</details>

### 3. [쿼리 최적화 및 DB로직 최소화](https://skroy0513.tistory.com/46)
<details>
  <summary>❓ <b><i>쿼리 최적화 방법과 DB로직 최소화 방법을 소개해 주세요.</i></b><br></summary>
  <div markdown="1">
    &nbsp;&nbsp;먼저 쿼리를 최적화 하기 위한 방법으로는 SELECT시 필요한 컬럼만 불러오고, 조건 부여 시 별도의 연산은 걸지 않는 것이 좋습니다. LIKE사용시 와일드카드는 String 앞부분에 배치하지 않는것이 좋으며, DISTINCT와 같이 중복 값을 제거하는 연산은 사용하지 않는 것이 좋습니다.<br>
    &nbsp;&nbsp;DB로직을 최소화하는 방법에는 앞서 소개해 드린 방법으로 쿼리를 최적화하는 방법이 있고, 데이터를 일관되게 모델링 하는 방법이 있습니다. 또한 비즈니스 로직을 분리 시키고, 쿼리와 데이터를 캐싱하여 성능을 향상 시킬 수 있습니다.
  </div>  
</details>

### 4. [DDL, DML, DCL](https://skroy0513.tistory.com/47)
<details>
  <summary>❓ <b><i>SQL에 대해 설명해 주세요.</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;SQL은 Structured Query Language로 구조적인 질의 언어라는 뜻입니다. 데이터베이스의 제어, 관리할 때 사용되며 역할에 따라 DDL, DML, DCL 3가지로 나눌 수  있습니다.<br>
    &nbsp;&nbsp;DDL은 정의 언어로서, CREATE로 데이터베이스 생성, ALTER로 수정, DROP으로 삭제를 할 수 있습니다.<br>
    &nbsp;&nbsp;DML은 조작 언어로서, INSERT로 데이터 추가, SELECT로 조회, UPDATE로 수정, DELETE로 삭제할 수 있습니다.<br>
    &nbsp;&nbsp;DCL은 제어 언어로 GRANT로 권한 부여, REVOKE로 권한 박탈, COMMIT으로 결과 반영, ROLLBACK으로 작업 취소 및 복구를 할 수 있습니다.<br>
  </div>
</details>

### 5. [Primary Key, Foreign Key](https://skroy0513.tistory.com/49)
<details>
  <summary>❓ <b><i>기본 키, 외래 키에 대해 설명해 주세요.</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;기본키와 외래키는 관계형 데이터베이스에서 사용되는 중요한 개념으로, 데이터베이스 테이블 간의 관계를 설정하고 데이터 무결성을 유지하기 위해 사용됩니다.<br>
    &nbsp;&nbsp;기본 키는 Primary Key로 각 레코드를 고유하게 식별하는 역할로서 중복이 허용되지 않으며 NULL값을 가질 수 없습니다. 모든 레코드는 무조건 기본키를 가져야 하며, 대부분의 데이터베이스에서 자동으로 인덱싱이 되어 신속하게 검색하는 데 사용됩니다.<br>
    &nbsp;&nbsp;외래 키는 Foreign Key로 한 테이블에서 다른 테이블의 기본키를 참조하는 키입니다. 외래키를 통해 테이블 간의 관계를 형성할 수 있고, 두 개 이상의 테이블에서 데이터를 검색하고 JOIN 할 수 있습니다. 또한 외래키로 인해 데이터의 무결성이 유지되는 데에 중요한 역할을 하며, 일관성 또한 유지됩니다.<br>
  </div>
</details>

### 6. [Redis](https://skroy0513.tistory.com/58)

### 7. [DELETE, TRUNCATE, DROP](https://skroy0513.tistory.com/65)
<details>
  <summary>❓ <b><i>삭제하는 명령어에 대해 설명해 주세요.</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;데이터베이스에서 삭제하는 쿼리를 작성할 때 DELETE, TRUNCATE, DROP의 명령어를 사용하여 삭제를 할 수 있습니다. 이 세 가지 명령어는 각자 삭제하는 범위와 특징이 다릅니다. <br>
    &nbsp;&nbsp;먼저 DELETE는 DML에 해당하는 명령어로서, WHERE절을 사용하여 테이블에 저장된 행 하나하나를 삭제하는 명령어 입니다. DELETE로 삭제를 하게 되면 자동으로 commit이 되지 않기 때문에 실수로 데이터를 삭제한 경우 rollback을 통해 되돌릴 수 있습니다. 이 방식으로 삭제하는 것은 데이터가 담겨있던 저장공간을 반납하지 않게 됩니다. <br>
    &nbsp;&nbsp;TRUNCATE는 DDL에 해당하는 명령어로서, DELETE와 상반된 방식으로 테이블의 전제 데이터를 삭제하는 명령어 입니다. 자동 commit이 되기 때문에 다시 되돌릴 수 없는 특징이 있습니다. 하지만 전체 데이터를 한번에 삭제하기 때문에 속도가 빠르고, 테이블이 초기 상태에 할당 되었던 저장공간만 남겨두고 모두 반납합니다. <br>
    &nbsp;&nbsp;마지막으로 DROP은 마찬가지로 DDL에 해당하는 명령어로, 테이블의 존재 자체를 삭제하고 해당 테이블에 생성되 있었던 인덱스도 사라지게 되는 명령어입니다. TRUNCATE와 동일하게 자동 commit이어서 되돌릴 수 없습니다. 테이블이 가지고 있던 모든 저장공간을 다시 반납하는 특징이 있습니다.
  </div>
</details>

### 8. [WHERE, HAVING](https://skroy0513.tistory.com/66)
<details>
  <summary>❓ <b><i>WHERE과 HAVING의 차이에 대해서 설명해 주세요.</i></b></summary>
  <div markdown="1">
    &nbsp;&nbsp;where과 having은 데이터를 select 할 때 조건을 걸어 필터링 하는 역할을 합니다. <br>
    &nbsp;&nbsp;먼저 where절은 from 절 바로 뒤에 오며 개별 행을 필터링합니다. 또한 기본적인 조건절로서 우선적으로 모든 필드에 조건을 둘 수 있습니다.<br>
    &nbsp;&nbsp;having절은 group by 로 같은 값을 가진 행을 그룹 짓고 난 뒤에 그 그룹을 필터링합니다. 그렇기 때문에 group by 없이는 단독으로 사용될 수 없습니다.
  </div>
</details>
