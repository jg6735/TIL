# PostgreSQL 사용해 보기

## TIL
- PostgreSQL을 공부하면서 이름만 여러번 들어봤지, 사용하는 것은 처음이다.
이렇게 직접 사용해보면서 PostgreSQL의 특징과 장점 및 단점을 공부하게 돼서 의미있었다.
한국에서는 잘 사용하지 않는다고 하는데, 전세계적인 트렌드로는 점유율이 증가하고 있었다.
그냥 관계형 데이터베이스가 아닌 객체 관계형(object-relational) 데이터베이스라는 점이 신선하게 와닿았다.
MySQL이 많이 사용되긴 하지만, 특별한 경우에 PostgreSQL의 장점을 살려서 사용할 수도 있을 것 같다는 생각이 들었다.

## PostgreSQL의 대표적인 특징
- PostgreSQL은 **ORDBMS**중 하나이며 **무료**로 제공되고 있다.
- 오라클 개발자들이 PostgreSQL 개발에 합류하여 오라클과 유사하다.

- ACID 및 트랜잭션 지원
- 다양한 인덱싱 기법 지원
- 유연한 Full-text search 기능
- 동시성 성능을 높여주는 MVCC 기능
- 다양하고 유연한 복제 방식 지원
- 다양한 프로시져(PL/pgSQL, Perl, Python, Ruby, TCL 등) / 인터페이스(JDBC, ODBC, C/C++, .Net. Perl, Python 등) 언어
- 질 좋은 커뮤니티 지원 및 상업적인 지원
- 잘 만든 문서 및 충분한 메뉴얼 제공

## ORDBMS
- 객체 지향 데이터베이스 시스템과 관계형 데이터베이스 시스템을 기반으로하며 복잡한 객체가 중심 역할을 하는 DBMS

- ORDBMS vs RDBMS ?
	- RDBMS는 행과 열이 있는 하나 이상의 관계 또는 테이블의 모음이지만 ORDBMS는 데이터가 객체로 저장된 것처럼 작동한다.

## PostgreSQL 설치

* https://www.postgresql.org/   
	* postgresql 공식 사이트에서 다운로드 한다.

* ![image](/uploads/81dff96db67e9f729b22ec639fc85bc9/image.png)

* 데이터베이스의 superuser인 postgres 계정의 비밀번호를 설정한다.

* ![image](/uploads/e93d676d52be161b8f9319f5eb60f2a6/image.png)

* 사용 Port (MySQL은 기본 포트가 3306인 반면 PostgreSQL의 기본 포트는 5432이다)

* ![image](/uploads/09291fa664e0dbc7abbaf3920f1ae8f3/image.png)

* 지역 설정 - Locale : Korean, Korea

* ![image](/uploads/3bed9510dfaaacbf8a492009c20cc955/image.png)

* 성공적으로 설치 완료

## Database 생성

* ![image](/uploads/4332e74cb3b5fd3daf1a38d5e98083a4/image.png)

* MySQL의 MySQL Workbench 같은 툴인 pgAdmin4를 실행한다.
* 최초 실행시 pgAdmin 비밀번호를 생성한다.

* ![image](/uploads/8f7eb95470bf0ad1ba5c39675ac02713/image.png)

* 좌측 Servers를 클릭한 뒤, superuser인 postgres 계정으로 로그인한다.
* 이전에 등록한 비밀번호를 입력한다.

* ![image](/uploads/da987d9b7647491bc41017942858e43d/image.png)

* Database 생성

* ![image](/uploads/adf5c9a01de48608afc504ae8ba4ed35/image.png)

* 다음과 같이 생성된 것을 확인할 수 있다.

* ![image](/uploads/1361d059afc9aac7a353d188373b18c7/image.png)

* 이번에는 schema를 생성한다.

* ![image](/uploads/247d6c6aaa153d38e03bcfcf0d784cdb/image.png)

* 다음과 같이 PRJ1 schema가 생성된 것을 확인할 수 있다.

* ![image](/uploads/80e18259e653a0ae957741a13a692e8a/image.png)

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

* ![image](/uploads/cab2a4fe5ff03b4e07ba7d69ca06b36f/image.png)

* 테이블을 생성함과 동시에 컬럼도 생성한다. 컬럼이름, 데이터타입, 길이, null과 기본키를 체크할 수 있다.

* ![image](/uploads/451632f8fc52a500aa4ecc501db8af9e/image.png)

* Sequence를 생성한다.
	* Sequence
		- 자동으로 증가(감소)하는 숫자를 생성시키는 객체
		- MySQL에서는 Auto Increment로 사용하지만, Oracle과 PostgreSQL 등에서는 Sequence 객체를 통해 관리한다.
		- 다음은 시퀀스 객체의 현재 값과 시퀀스 객체의 다음 값을 구하는 쿼리이다.
```sql
SELECT LAST_VALUE FROM Sequence명
NEXTVAL(Sequence명)
```

* ![image](/uploads/7c4b8e33807dac774c063ccfe3cacfff/image.png)

* Query Tool을 이용해 여러 쿼리를 작성할 수 있다.
* "Schema명"."객체명"으로 객체에 접근할 수 있다.

* ![image](/uploads/7d3c5bce463cbb426a4d41b431dbc0b7/image.png)

* 테이블 조회 쿼리
* SEQ_USER의 현재값 조회
* TBL_USER 테이블에 Sequence를 이용해 Data를 Insert 하는 쿼리

* ![image](/uploads/62d0880e018a52432ce12374070a7302/image.png)

* 추가로 영화 테이블을 만들고 데이터를 삽입했다.
* 7 line부터 13 line까지 영화 테이블을 조회하고 데이터를 삽입하는 쿼리이다.

* ![image](/uploads/c5e5e262dccd8065aee91b2ef137fd92/image.png)

* 데이터베이스를 백업하는 절차이다.

* ![image](/uploads/5c10ddf2e1fc3366d8cb94ae56fda906/image.png)

* 성공적으로 백업한 것을 확인할 수 있다.