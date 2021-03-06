# PostgreSQL

## PostgreSQL의 대표적인 특징
**PostgreSQL**은 **ORDBMS**중 하나이며 <u>**무료**로 제공되는 오픈소스 데이터베이스</u>이다.    
오라클 개발자들이 PostgreSQL 개발에 합류하여 실제 기능적인 면에서 Oracle과 유사한 것이 많다.

>- ACID 및 트랜잭션 지원
>- 다양한 인덱싱 기법 지원
>- 유연한 Full-text search 기능
>- 동시성 성능을 높여주는 MVCC 기능
>- 다양하고 유연한 복제 방식 지원
>- 다양한 프로시져(PL/pgSQL, Perl, Python, Ruby, TCL 등) / 인터페이스(JDBC, ODBC, C/C++, .Net. Perl, Python 등) 언어
>- 질 좋은 커뮤니티 지원 및 상업적인 지원
>- 잘 만든 문서 및 충분한 메뉴얼 제공

## PostgreSQL의 특장점
- 라이센스에 대한 비용문제가 전혀 없다.
- 표준SQL을 잘 준수하고 있다.
- 오래된 오픈소스의 안정성을 가진다.
- 꾸준히 발전중인 데이터베이스이다.
- Oracle에 버금가는 통계 함수를 가지고 있다.

## ORDBMS
    객체 지향 데이터베이스 시스템과 관계형 데이터베이스 시스템을 기반으로하며 복잡한 객체가 중심 역할을 하는 DBMS

### ORDBMS vs RDBMS ?
    RDBMS는 행과 열이 있는 하나 이상의 관계 또는 테이블의 모음이지만 ORDBMS는 데이터가 객체로 저장된 것처럼 작동한다.

## Vacuum
> PostgreSQL은 다른 RDBMS와 달리, UPDATE 쿼리와 DELETE 쿼리가 순전히 기존 데이터를 변형하거나 삭제하는 방식으로 동작하지 않는다.   
> UPDATE 쿼리는 기존에 있던 데이터는 그대로 둔 채 새로운 데이터를 추가하는 방식으로 동작하며,   
> DELETE 쿼리는 기존의 데이터를 삭제하지 않고 삭제해야한다는 표시만 남겨두는 방식으로 동작한다.   
> 이러한 이유는 PostgreSQL이 동시접근에 의한 이슈들을 방지하기 위한 MVCC 모델을 적용하고 있기 때문이다.

## MVCC
> 동시접근을 허용하는 데이터베이스에서 동시성을 제어하기 위해 사용하는 방법이다.   
> 즉, MVCC 모델에서 데이터에 접근하는 사용자는 접근한 시점에서의 데이터베이스의 Snapshot을 읽는다.   
> 이 Snapshot 데이터에 대한 트랜잭션이 commit 될 때까지의 변경사항은 다른 사용자가 볼 수 없다.   
> 이러한 개념으로 사용자가 데이터를 업데이트하면 새로운 버전의 데이터를 생성하고, 사용자는 마지막 버전의 데이터를 읽게 된다.


snapshot이란 SQL Server 데이터베이스(원본 데이터베이스)의 읽기 전용 정적 뷰이다.


## PostgreSQL 설치

* https://www.postgresql.org/
* postgresql 공식 사이트에서 다운로드 한다.

![postgre설치(1)](https://user-images.githubusercontent.com/92859179/173670389-b96e1a4b-0cac-4667-b9a1-cde4ce33dada.jpg)

* 데이터베이스의 superuser인 postgres 계정의 비밀번호를 설정한다.

![postgre설치(2)](https://user-images.githubusercontent.com/92859179/173670398-063ae6ae-bda7-4816-96e2-2c6b9ae326b7.jpg)

* 사용 Port (MySQL은 기본 포트가 3306인 반면 PostgreSQL의 기본 포트는 5432이다)

![postgre설치(3)](https://user-images.githubusercontent.com/92859179/173670408-d39d44be-602b-4821-bd8d-1f503dc64235.jpg)

* 지역 설정 - Locale : Korean, Korea

![postgre설치(4)](https://user-images.githubusercontent.com/92859179/173670409-1828513f-3e8f-4739-9322-5c6db3097530.jpg)

* 성공적으로 설치 완료

## Database 생성

![pgadmin(1)](https://user-images.githubusercontent.com/92859179/173670417-6f01ed08-4321-4041-bdff-86a7c75756a9.jpg)

* MySQL의 MySQL Workbench 같은 툴인 pgAdmin4를 실행한다.
* 최초 실행시 pgAdmin 비밀번호를 생성한다.

![pgadmin(2)](https://user-images.githubusercontent.com/92859179/173670439-e5a6b29b-ef40-4afd-9217-606e4e8a80e9.jpg)

* 좌측 Servers를 클릭한 뒤, superuser인 postgres 계정으로 로그인한다.
* 이전에 등록한 비밀번호를 입력한다.

![pgadmin(3)](https://user-images.githubusercontent.com/92859179/173670448-bc472d54-8cdc-426d-9e05-37fb8bb33797.jpg)

* Database 생성

![pgadmin(4)](https://user-images.githubusercontent.com/92859179/173670454-412c95fb-fed8-4c98-8414-50c498c07e3d.jpg)

* 다음과 같이 생성된 것을 확인할 수 있다.

![pgadmin(5)](https://user-images.githubusercontent.com/92859179/173670427-58a75e15-87e9-47a0-9f9c-8ca82d0c86a3.jpg)

* 이번에는 schema를 생성한다.

![pgadmin(6_생성된스키마확인)](https://user-images.githubusercontent.com/92859179/173670463-53e2de0a-b869-418b-a9ac-88dba674e53c.jpg)

* 다음과 같이 PRJ1 schema가 생성된 것을 확인할 수 있다.

![pgadmin(7_회원테이블생성)](https://user-images.githubusercontent.com/92859179/173670470-01d9f8e3-53b7-4126-85f0-ae62ee618b3b.jpg)

* 회원 테이블을 생성한다. 테이블명과 테이블스페이스, 코멘트를 작성한다.
* Tablespace(테이블스페이스)는 일부 DB에서 등장하는 개념이다. 다음은 PostgreSQL 공식사이트에서 정의하는 테이블스페이스이다.
```
포스트그레스-큐엘에서 테이블스페이스는 DB관리자에 의해 데이터베이스의 객체가 저장될 수 있는 파일시스템의 경로로 정의된다.
테이블스페이스가 생성되면 데이터베이스 객체에 객체를 생성할 때 이름에 의해서 테이블스페이스가 참조될 수 있다.
포스트그레스-큐엘이 설치될 때 디스크레이아웃에 따라 관리자가 생성할 수 있는데 두가지 관점에서 매우 유용하다. 
첫번째는 DB가 생성된 볼륨 또는 파티션에 여유공간이 부족할 때 테이블스페이스를 다른 파티션이나 디스크에 생성하여 시스템을 재구성할 때까지 DB를 확장할 수 있다. 
또 다른 하나는 데이터베이스 객체의 성능 최적화를 위해 사용할 수 있다는 것이다. 
예를 들어 매우 사용량이 많으면서 자주 업데이트 되는 인덱스를 위해 고성능 SSD를 장착하고테이블스페이스를 생성하여 인덱스를 SSD에 생성하여 성능을 개선하는데 사용될 수 있다.
```

![pgadmin(8_회원테이블컬럼생성)](https://user-images.githubusercontent.com/92859179/173670477-714bd854-1e0f-45ba-bc2f-e58b41836d45.jpg)

* 테이블을 생성함과 동시에 컬럼도 생성한다. 컬럼이름, 데이터타입, 길이, null과 기본키를 체크할 수 있다.

![pgadmin(9_sequence생성)](https://user-images.githubusercontent.com/92859179/173670484-15d82867-80f4-4766-9ab7-577f3e25d2d6.jpg)

* Sequence를 생성한다.
    * Sequence
        - 자동으로 증가(감소)하는 숫자를 생성시키는 객체
        - MySQL에서는 Auto Increment로 사용하지만, Oracle과 PostgreSQL 등에서는 Sequence 객체를 통해 관리한다.
        - 다음은 시퀀스 객체의 현재 값과 시퀀스 객체의 다음 값을 구하는 쿼리이다.
```sql
SELECT LAST_VALUE FROM Sequence명
NEXTVAL(Sequence명)
```

![pgadmin(10_querytool)](https://user-images.githubusercontent.com/92859179/173670491-16b417a4-1d9f-46da-9788-86dcd855acb9.jpg)

* Query Tool을 이용해 여러 쿼리를 작성할 수 있다.
* "Schema명"."객체명"으로 객체에 접근할 수 있다.

![pgadmin(11_insert)](https://user-images.githubusercontent.com/92859179/173670497-b4e180d0-edb8-45bb-96e7-327a56099387.jpg)

* 테이블 조회 쿼리
* SEQ_USER의 현재값 조회
* TBL_USER 테이블에 Sequence를 이용해 Data를 Insert 하는 쿼리

![pgadmin(12_movie)](https://user-images.githubusercontent.com/92859179/173670504-077b9408-f879-483d-b63a-5671e46a11f0.jpg)

* 추가로 영화 테이블을 만들고 데이터를 삽입했다.
* 7 line부터 13 line까지 영화 테이블을 조회하고 데이터를 삽입하는 쿼리이다.

![pgadmin(13_backup)](https://user-images.githubusercontent.com/92859179/173670509-35753afe-23b6-43f7-bc7a-bcb506baa668.jpg)

* 데이터베이스를 백업하는 절차이다.

![pgadmin(14_backupsucc)](https://user-images.githubusercontent.com/92859179/173670517-6548194d-3560-41f0-b221-64714899d499.jpg)

* 성공적으로 백업한 것을 확인할 수 있다.


## DDL

### Database

```sql
CREATE DATABASE 데이터베이스_이름 [OWNER 소유자명];

ALTER DATABASE 데이터베이스_이름 OWNER TO 소유자명;

ALTER DATABASE 데이터베이스_이름 RENAME TO 데이터베이스_이름2;

ALTER DATABASE 데이터베이스_이름 SET [바꿀_설정값] TO [값];

DROP DATABASE 데이터베이스_이름;
```




### Schema

```sql
CREATE SCHEMA 스키마명 [AUTHORIZATION 소유자명];

ALTER SCHEMA 스키마명 RENAME TO 이름;

ALTER SCHEMA 스키마명 OWNER TO 소유자;

DROP SCHEMA 스키마명;
```




### Tablespace
```sql
CREATE TABLESPACE 테이블스페이스명 [OWNER 소유자명] [LOCATION 위치];

ALTER TABLESPACE 테이블스페이스명 RENAME TO 테이블스페이스명;

ALTER TABLESPACE 테이블스페이스명 OWNER TO 소유자명;

DROP TABLESPACE 테이블스페이스명;
```




### Table
```sql
CREATE TABLE 테이블명(

컬럼이름 데이터타입 [NOT NULL | NULL] [DEFAULT default_value] [UNIQUE [KEY]] [[PRIMARY] KEY] [타테이블명 (컬럼명) ] ,

[CONSTRAINT] PRIMARY KEY 칼럼이름) ,

[CONSTRAINT] UNIQUE [INDEX | KEY] [인덱스이름] (칼럼이름) ,

[CONSTRAINT] FOREIGN KEY [인덱스이름] (칼럼이름) (타테이블명 (컬럼명) ) ,

CHECK (expr)

)


ALTER TABLE 테이블명 ADD CHECK (제약조건);

ALTER TABLE 테이블명 ADD CONSTRAINT 제약조건명 UNIQUE (컬럼명);

ALTER TABLE 테이블명 ADD FOREIGN KEY (FK이름) REFERENCES 타테이블명(칼럼명);

ALTER TABLE 테이블명 RENAME TO 새_테이블명;
```

### COLUMN
```sql
ALTER TABLE 테이블_이름 ADD COLUMN 컬럼_이름 TYPE;

ALTER TABLE 테이블_이름 DROP COLUMN 컬럼_이름;

ALTER TABLE 테이블_이름 CHANGE 컬럼_이름1 컬럼_이름2 [TYPE];

ALTER TABLE 테이블_이름 ALTER COLUMN 컬럼_이름 TYPE NOT NULL;

ALTER TABLE 테이블_이름 RENAME COLUMN 컬럼_이름 TO 새_컬럼_이름;
```

## DML
```sql
SELECT [DISTINCT] 컬럼명..

FROM 테이블명

[ WHERE condition ]

[ GROUP BY expression [, ...] ]

[ HAVING condition [, ...] ]

[ ORDER BY expression [ ASC | DESC | USING operator ] [ NULLS { FIRST | LAST } ]

[ LIMIT { count | ALL } ]

[ OFFSET start [ ROW | ROWS ] ]

INSERT INTO 테이블명 (컬럼1, 컬럼2 …) VALUES (값1, 값2 …);

INSERT INTO 테이블명 (컬럼1, 컬럼2 …) SELECT ~ ;

UPDATE 테이블명 SET 칼럼명 = 값 [WHERE 조건];

DELETE FROM 테이블명 [WHERE 조건];
```
## DCL
```sql
CREATE USER 유저_이룸 [PASSWORD '패스워드'] [권한];

ALTER USER [유저_이름1] RENAME TO [유저_이름2];

ALTER USER 유저_이름 WITH PASSWORD '패스워드';

ALTER USER 유저_이름 WITH [권한];

GRANT [권한] [ ON object [,...] ] TO { PUBLIC | GROUP group | username};

REVOKE [권한] [ON object [,...] ] FROM { PUBLIC | GROUP gname | username };

Begin Transaction;

Commit / rollback ;
```