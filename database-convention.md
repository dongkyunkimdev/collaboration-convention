### Snake Case를 사용하라.
- First_Name❌ first_name⭕

### 임의의 약어를 사용하지 말라.
- mid_nm❌ middle_name⭕

### 긴 단어의 경우, 단어 자체보다 일반적으로 사용되는 약어를 사용하라.
- Internationalization❌ i18n⭕
- localization❌ l10n⭕

### 예약어로 간주되는 단어를 피하라.
- user❌ lock❌ table❌
- 예약어 목록 : [PostgreSQL](http://www.postgresql.org/docs/9.3/static/sql-keywords-appendix.html), [MySQL](http://dev.mysql.com/doc/refman/5.7/en/reserved-words.html), [Oracle](http://docs.oracle.com/cd/E16655_01/server.121/e17209/ap_keywd.htm#SQLRF022), [MSSQL](http://technet.microsoft.com/en-us/library/ms189822.aspx)

### 데이터를 보유하는 테이블, 뷰 및 기타 관계들은 복수형이 아닌 단수 이름을 가져야 한다.
- teams❌ team⭕

### 기본 키 필드의 이름은 id로 작성하라.
- 결합할 필드의 기본키 이름을 기억 할 필요가 없어진다.
- person_id❌ id⭕

### 외래 키 필드는 참조된 테이블의 이름과 참조된 필드 이름의 조합이어야 한다.
- **team_id** bigint NOT NULL REFERENCES **team(id)**

### 관계 유형 접두사를 사용하지 말라.
- tb_team❌ vw_team❌ team⭕

### 어플리케이션 이름 접두사를 사용하지 말라.
- hometact_board❌ board⭕

### 데이터 유형 접미사를 사용하지 말라.
- 필드 데이터 유형은 변경될 가능성이 있다.
- name_tx❌ name⭕

### 인덱스 이름을 명시적으로 사용하라.
- 인덱스의 이름이 명시적이어야 올바르게 사용되는지 알 수 있다.
- ORM 등으로 인해 자동 생성된 인덱스와 제약조건들은 `fkas9dfnksdfnks` 등 의미를 알 수 없는 없는 이름으로 생성된다.
>CREATE TABLE person (  
>&nbsp;&nbsp;&nbsp;&nbsp;id          bigserial PRIMARY KEY,  
>&nbsp;&nbsp;&nbsp;&nbsp;email       text NOT NULL,  
>&nbsp;&nbsp;&nbsp;&nbsp;first_name  text NOT NULL,  
>&nbsp;&nbsp;&nbsp;&nbsp;last_name   text NOT NULL,  
>&nbsp;&nbsp;&nbsp;&nbsp;CONSTRAINT person_ck_email_lower_case CHECK (email = LOWER(email)));  

>CREATE INDEX person_ix_first_name_last_name ON person (first_name, last_name);

### 제약 조건을 설명할 수 있는 이름을 지어라.
- 제약 조건을 위반하는 경우 이름을 기반으로 원인을 쉽게 찾을 수 있다.
>CREATE TABLE team (  
>&nbsp;&nbsp;&nbsp;&nbsp;id          bigserial PRIMARY KEY,  
>&nbsp;&nbsp;&nbsp;&nbsp;name        text NOT NULL);

>CREATE TABLE team_member (  
>&nbsp;&nbsp;&nbsp;&nbsp;team_id     bigint REFERENCES team(id),  
>&nbsp;&nbsp;&nbsp;&nbsp;person_id   bigint REFERENCES person(id),  
>&nbsp;&nbsp;&nbsp;&nbsp;CONSTRAINT team_member_pkey PRIMARY KEY (team_id, person_id));

나쁜 명명 규칙보다 더 나쁜 것은, 통일되지 않은 여러 명명 규칙이라고 한다.
좋은 명명 규칙을 기반으로 조직의 컨벤션을 통일해서 사용하는 것이 중요하다.

## Reference
- [How I Write SQL, Part 1: Naming Conventions](https://launchbylunch.com/posts/2014/Feb/16/sql-naming-conventions/)