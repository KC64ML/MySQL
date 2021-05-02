# MySQL

* SQL
  * 관계형 데이터베이스에서 데이터를 조작하고 쿼리하는 표준 언어
  * 사용자가 필요하고 원하는 것을 RDBMS에게 요청(쿼리)을 하는 걸 의미한다.
* SQL 명령어 종류
  * DDL - Data Definition Language (데이터 정의 언어)
    * ![DDL](https://user-images.githubusercontent.com/72541544/116813442-d7d99a00-ab8e-11eb-9870-3f1d41e62e1d.png)
    * ![DDL1](https://user-images.githubusercontent.com/72541544/116813443-d7d99a00-ab8e-11eb-88ae-fde344afbbba.png)
  * DML - Data Manipulation Language (데이터 조작 언어)
    * ![DML](https://user-images.githubusercontent.com/72541544/116813444-d8723080-ab8e-11eb-8060-19cdd085561c.png)
    * ![DML2](https://user-images.githubusercontent.com/72541544/116813445-d8723080-ab8e-11eb-974d-1f2c02c9673a.png)
  * DCL - Data Control Language (데이터 제어 언어)
    * ![DCL](https://user-images.githubusercontent.com/72541544/116813440-d60fd680-ab8e-11eb-95c5-35339a559483.png)
    * ![DCL3](https://user-images.githubusercontent.com/72541544/116813441-d7410380-ab8e-11eb-84c2-3fa21b6be4d7.png)



## Select

![생활용어](https://user-images.githubusercontent.com/72541544/116813455-ddcf7b00-ab8e-11eb-84ed-a4de87c23def.png)

* Projection : 원하는 column만 가지고 오는 방법
* Selection : 원하는 row만 가지고 오는 방법
  * ![Project Selection](https://user-images.githubusercontent.com/72541544/116813452-dd36e480-ab8e-11eb-8d70-d197fdfd1c02.png)



## MySQL 시작하기에 앞서 MySQL Workbench

* MySQL Connection 생성

  * ![Setup Connection](https://user-images.githubusercontent.com/72541544/116813453-dd36e480-ab8e-11eb-825f-077c8e2590d3.png)

    * Hostname : 127.0.0.1, MySQL Workbench에 설치된 컴퓨터에 MySQL 서버에 접속하겠다.

    * Username : root

    * Password : 비밀번호 저장 가능

      

* Connection에 진입한 후 SCHEAMS에서 이전 MySQL 입력된 내용 확인 가능 

  * ![스키마](https://user-images.githubusercontent.com/72541544/116813456-de681180-ab8e-11eb-870f-dd97263fd920.png)

* Model 생성

  * !![Model 생성](https://user-images.githubusercontent.com/72541544/116813450-dc05b780-ab8e-11eb-8aa3-cf127198238d.png)

* ERD(Entity Relationship Diagram)

  * 개체 속성과 개체 간 관계를 도표로 표현한 것
  * ![EER Diagram](https://user-images.githubusercontent.com/72541544/116813447-dad48a80-ab8e-11eb-80b5-6b3bd73023ca.png)
    * ![ERD 관계 표현법](D:\Computer_Science\DataBase\MySQL\write\Day 1\사진2\ERD 관계 표현법.png)
    * 일 대 일 테이블(식별 관계)
    * ![일대일](https://user-images.githubusercontent.com/72541544/116813464-e031d500-ab8e-11eb-89d8-7f0333b68e72.png)
      * 상세 주소 테이블은 person_id를 기본키로 사용, person_id를 통해 person 테이블을 참조하고 있다.
      * 한 명의 주민은 한 개의 상세 주소를 가질 수 있다.
      * 상세 주소는 주민 id가 없다면 존재할 수 없다.(식별 관계)
      * 주민 (부모 테이블), 상세 주소(자식 테이블)
      * 부모테이블의 id를 저장하는 테이블은 자식 테이블, 데이터를 제공하는 테이블은 부모 테이블
  * 일대 다 (참조 필수)
  * ![일대 다](https://user-images.githubusercontent.com/72541544/116813463-e031d500-ab8e-11eb-8064-2d69f5f66839.png)
    * 부서와 회사원 관계
    * 회사원은 한 개의 부서에 반드시 소속되어야 한다.
    * 한 개의 부서에 여러 회사원이 소속 될 수 있다.
    * 한 개의 부서에 소속된 회사원이 한 명도 없을 수 있다.
  * 일대 다 (참조 Null 허용)
  * ![일대 다(참조 NULL 허용)](https://user-images.githubusercontent.com/72541544/116813462-df993e80-ab8e-11eb-9977-fd8cbb571495.png)
    * 회사원이 꼭 부서에 소속될 필요는 없다.
    * 한 개의 부서에 여러 회사원이 소속 될 수 있다.
    * 한 개의 부서에 소속된 회사원이 한 명도 없을 수 있다.
  * 비식별 관계
  * ![비식별 관계](https://user-images.githubusercontent.com/72541544/116813459-df00a800-ab8e-11eb-935d-816f78c8274d.png)
    * 기본 키에 외래키가 포함되어 있지 않다면 비식별 관계
  * 식별 관계
  * ![식별관계](https://user-images.githubusercontent.com/72541544/116813461-df993e80-ab8e-11eb-95f4-627762929e89.png)
    * 기본 키에 외래키가 포함되어있다면 이를 식별 관계

* 설계한 후 mysql db와 연결

  * 연결 방법이 기억 안난다면 https://olidang.tistory.com/95 참조
  * ![mysql 실행결과](https://user-images.githubusercontent.com/72541544/116813457-de681180-ab8e-11eb-851a-b59f3626ed92.png)

  





## MySQL 사용

* mysql을 실행하기 위해서는 cmd에서 mysql -u root -p 하여 mysql에 진입

  * 환경 변수(경로) 선언이 되어 있어야 한다.

* database를 생성해야한다.

  * ```mysql 
    create database chang;
    show database; # 현재 DBMS에 존재하는 DB 확인
    use db이름; # 사용중인 DB 전환
    show tables; # 현재 DB에 존재하는 테이블 목록 확인
    desc table이름; # 테이블 구조 확인
    ```

* SQL문을 실행하기 위해 테이블을 하나 생성한다.

  * ```mysql
    create table select_test
    (
        name varchar(50),
        dept_cd varchar(1),
        phone varchar(15)
    )character set utf8;   
    
    # character set utf8 : 테이블에 한글 데이터가 들어갈 수 있도록 캐릭터 셋을 잡아주는 명령
    ```

  * ```mysql
    desc select_test; # (Describe) 테이블 칼럼 목록을 확인
    ```








참고 자료 : https://olidang.tistory.com/95

참고 자료 : https://bamdule.tistory.com/46

참고 자료 : https://stricky.tistory.com/333

