## 📖 데이터베이스의 큰 그림

### 🎯 데이터베이스와 DBMS

**데이터베이스**
- 여러 사람이 공유하며 사용할 목적으로 체계화해 통합, 관리하는 데이터의 집합
- 원하는 기능을 동작시키기 위해 마땅히 저장해야 하는 정보의 집합

**DBMS (Database Management System)**
- 데이터베이스를 관리하기 위한 프로그램
- 서버와 같은 형태로 실행됨

### 🔧 DBMS의 종류

**RDBMS (관계형 데이터베이스)**
- MySQL, Oracle, PostgreSQL, SQLite, MariaDB, Microsoft SQL Server
- 점유율이 가장 높음

**NoSQL DBMS**
- MongoDB, Redis
- 비관계형 데이터베이스

### 🗄️ 파일 대신 데이터베이스를 이용하는 이유

1. **데이터 일관성 및 무결성 제공의 어려움**
   - 동시 접근 시 레이스 컨디션 문제 발생
   - 데이터 검증의 어려움

2. **불필요한 중복 저장**
   - 저장 공간 낭비
   - 데이터 관리의 복잡성

3. **데이터 변경 시 연관 데이터 변경의 어려움**
   - 일관성 유지의 번거로움

4. **정교한 검색의 어려움**
   - 복합 조건 검색의 한계

5. **백업 및 복구의 어려움**
   - 복구 기능의 부족

## 🏗️ 데이터베이스의 저장 단위와 트랜잭션

### 📝 엔티티와 스키마

**엔티티 (Entity)**
- 독립적으로 존재할 수 있는 객체
- 속성을 가진 대상

**속성 (Attribute)**
- 엔티티의 특성을 의미

**엔티티 집합**
- 같은 속성을 공유하는 엔티티들의 집합

**레코드 (Record)**
- 데이터베이스에 저장된 엔티티

**필드 (Field)**
- 데이터베이스에 저장된 엔티티 속성

### 🎨 스키마 (Schema)

**정의**
- 데이터베이스에 저장되는 레코드의 구조와 제약 조건을 정의한 것
- 레코드가 지켜야 할 틀이자 청사진

**RDBMS vs NoSQL**
- **RDBMS**: 명확한 스키마 정의, 정형화된 데이터
- **NoSQL**: 스키마-리스 데이터베이스, 유연한 형태

### ⚡ 트랜잭션과 ACID

**트랜잭션 (Transaction)**
- 데이터베이스와의 논리적 상호작용의 단위
- 하나 이상의 쿼리 포함 가능

**ACID 특성**

1. **원자성 (Atomicity)**
   - All or Nothing
   - 트랜잭션의 모든 작업이 성공하거나 모두 실패

2. **일관성 (Consistency)**
   - 트랜잭션 전후로 데이터베이스가 일관된 상태 유지

3. **격리성 (Isolation)**
   - 동시 수행되는 트랜잭션들이 서로 간섭하지 않음

4. **지속성 (Durability)**
   - 성공적으로 완료된 트랜잭션의 결과가 영구적으로 반영

## 🏢 RDBMS의 기본

### 📊 테이블의 구성

**필드 타입**

| 분류 | 타입 | 설명 |
|------|------|------|
| 숫자형 | TINYINT | 1바이트 정수 |
| | SMALLINT | 2바이트 정수 |
| | INT | 4바이트 정수 |
| | BIGINT | 8바이트 정수 |
| | FLOAT | 4바이트 부동소수점 |
| | DOUBLE | 8바이트 부동소수점 |
| 문자형 | CHAR | 고정길이 문자열 |
| | VARCHAR | 가변길이 문자열 |
| | TEXT | 대량 가변길이 문자열 |
| 날짜/시간형 | DATE | YYYY-MM-DD 형식 |
| | TIME | HH:MM:SS 형식 |
| | DATETIME | 날짜와 시간 |

### 🔑 키 (Key)

**후보 키 (Candidate Key)**
- 유일성과 최소성을 모두 만족하는 키
- 테이블 내에 하나 이상 존재 가능

**기본 키 (Primary Key)**
- 한 레코드를 식별하도록 선정된 키
- 테이블당 하나만 존재
- NULL 값 가질 수 없음

**외래 키 (Foreign Key)**
- 다른 테이블의 기본 키를 참조하는 필드
- 테이블 간의 참조 관계 형성

### 🔗 테이블의 관계

**일대일 대응 관계 (1:1)**
- 하나의 레코드가 다른 테이블의 레코드 하나에만 대응

**일대다 대응 관계 (1:N)**
- 하나의 레코드가 다른 테이블의 여러 레코드와 대응

**다대다 대응 관계 (M:N)**
- 한 테이블의 여러 레코드가 다른 테이블의 여러 레코드와 대응
- 중간 테이블 필요

### 🛡️ 무결성 제약 조건

1. **도메인 제약 조건**
   - 필드 타입과 범위에 대한 규칙
   - 원자 값 보장

2. **키 제약 조건**
   - 키로 지정된 필드에 중복된 값 불허

3. **엔티티 무결성 제약 조건**
   - 기본 키는 고유하고 NULL 불가

4. **참조 무결성 제약 조건**
   - 외래 키는 참조하는 테이블의 기본 키와 같은 값 또는 NULL

**참조 무결성 위반 시 대응**
- **CASCADE**: 참조하는 데이터도 함께 수정/삭제
- **SET NULL**: 참조하는 데이터를 NULL로 변경
- **SET DEFAULT**: 참조하는 데이터를 기본값으로 변경
- **RESTRICT**: 수정/삭제를 허용하지 않음

```sql
FOREIGN KEY (user_id) REFERENCES users(user_id)
ON UPDATE CASCADE
ON DELETE SET NULL;
```

## 💻 SQL

### 📋 DDL (Data Definition Language)

**CREATE**
```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE
);
```

**ALTER**
```sql
ALTER TABLE users ADD COLUMN age INT;
ALTER TABLE users MODIFY email VARCHAR(100) NOT NULL;
```

**DROP**
```sql
DROP TABLE users;
DROP DATABASE mydb;
```

**TRUNCATE**
```sql
TRUNCATE TABLE users;
```

### 🔄 DML (Data Manipulation Language)

**INSERT**
```sql
INSERT INTO users (username, email) VALUES ('kim', 'kim@example.com');
```

**UPDATE**
```sql
UPDATE users 
SET email = 'newemail@example.com' 
WHERE username = 'kim';
```

**DELETE**
```sql
DELETE FROM users WHERE username = 'kim';
```

**SELECT**
```sql
SELECT username, email FROM users WHERE age >= 20;
```

### 🎯 SELECT문의 주요 절

**WHERE절**
- 조건에 맞는 레코드 필터링

**GROUP BY절**
- 특정 필드를 기준으로 그룹화

**HAVING절**
- 그룹화된 결과에 조건 적용

**ORDER BY절**
- 정렬 (ASC/DESC)

**LIMIT절**
- 조회할 레코드 수 제한

### 🔧 TCL (Transaction Control Language)

**COMMIT**
- 트랜잭션을 데이터베이스에 반영

**ROLLBACK**
- 트랜잭션을 이전 상태로 되돌림

**SAVEPOINT**
- 롤백 기준점 설정

```sql
START TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;
COMMIT;  -- 또는 ROLLBACK;
```

### 🔐 DCL (Data Control Language)

**GRANT**
- 사용자에게 권한 부여

**REVOKE**
- 사용자로부터 권한 회수

```sql
GRANT SELECT, INSERT ON users TO 'username';
REVOKE DELETE ON users FROM 'username';
```

## ⚡ 효율적 쿼리

### 🔍 서브 쿼리와 조인

**서브 쿼리**
- 다른 SQL문 안에 포함된 SELECT문
- 복잡한 질의 가능

```sql
-- SELECT 안에 SELECT
SELECT username, 
       (SELECT COUNT(*) FROM posts WHERE posts.user_id = users.user_id) AS post_count
FROM users;

-- DELETE 안에 SELECT
DELETE FROM posts 
WHERE user_id = (SELECT user_id FROM users WHERE email = 'kim@example.com');
```

**조인 (Join)**
- 여러 테이블을 하나로 합치는 연산

**INNER JOIN**
```sql
SELECT users.name, orders.amount
FROM users
INNER JOIN orders ON users.id = orders.user_id;
```

**LEFT OUTER JOIN**
```sql
SELECT users.name, orders.amount
FROM users
LEFT OUTER JOIN orders ON users.id = orders.user_id;
```

**RIGHT OUTER JOIN**
```sql
SELECT users.name, orders.amount
FROM users
RIGHT OUTER JOIN orders ON users.id = orders.user_id;
```

**FULL OUTER JOIN**
```sql
-- MySQL에서는 UNION 사용
SELECT users.name, orders.amount FROM users LEFT JOIN orders ON users.id = orders.user_id
UNION
SELECT users.name, orders.amount FROM users RIGHT JOIN orders ON users.id = orders.user_id;
```

### 👁️ 뷰 (View)

**정의**
- SELECT문의 결과로 만들어진 가상의 테이블

**생성**
```sql
CREATE VIEW user_orders AS
SELECT users.name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id;
```

**장점**
- 쿼리 단순화
- 재사용성 향상
- 보안성 제공

### 🚀 인덱스 (Index)

**정의**
- 검색 속도 향상을 목적으로 만드는 테이블 필드에 대한 자료구조

**종류**
- **클러스터형 인덱스**: 테이블당 하나 (기본 키)
- **세컨더리 인덱스**: 테이블당 여러 개 가능

**생성**
```sql
CREATE INDEX idx_username ON users(username);
SHOW INDEX FROM users;          -- 인덱스 조회
DROP INDEX idx_username FROM users;  -- 인덱스 삭제
```

**자료구조**
- 주로 B 트리(B+ 트리) 사용
- 해시 테이블도 활용

**고려사항**
- ✅ SELECT 성능 향상
- ❌ INSERT/UPDATE/DELETE 성능 저하
- ❌ 저장 공간 필요
- 📝 테이블당 3개 이하 권장
- 📝 데이터가 많고 조회가 빈번한 필드에 적용

## 🎨 데이터베이스 설계

### 📊 ER 다이어그램

**목적**
- 데이터베이스 구조의 시각적 모델링
- 엔티티 간의 관계 표현

**표기법**
- **피터 첸 표기법**: 전통적인 형태
- **IE 표기법**: 테이블 형태로 직관적

### 🔧 정규화 (Normalization)

**목적**
- 잠재적인 문제가 발생하지 않도록 테이블 설계

**제1 정규형 (1NF)**
- 모든 속성이 원자 값을 가져야 함
- 더 이상 쪼갤 수 없는 단일한 값

**제2 정규형 (2NF)**
- 1NF + 기본 키가 아닌 모든 필드가 기본 키에 완전 함수 종속
- 부분 함수 종속성 제거

**제3 정규형 (3NF)**
- 2NF + 이행적 종속성 제거
- 기본 키가 아닌 필드들 간의 종속 관계 제거

**보이스/코드 정규형 (BCNF)**
- 3NF + 모든 결정자가 후보 키

**함수 종속성**
- **완전 함수 종속**: 기본 키 전체에 종속
- **부분 함수 종속**: 기본 키 일부에만 종속
- **이행적 종속**: A→B, B→C일 때 A→C

**역정규화**
- 성능 향상을 위해 의도적으로 정규화를 하지 않음
- 조인 연산 감소로 검색 속도 향상

## 🌐 NoSQL

### 🆚 RDBMS vs NoSQL

| 특성 | RDBMS | NoSQL |
|------|-------|-------|
| 스키마 | 고정됨 | 유연함 |
| 확장성 | 수직 확장 | 수평 확장 |
| ACID | 엄격한 준수 | 선택적 지원 |
| 성능 | 일관성 우선 | 성능 우선 |

### 📚 NoSQL의 종류

**키-값 데이터베이스**
- Redis, Memcached
- 간단한 키-값 쌍으로 저장
- 캐시, 세션 저장에 활용

**도큐먼트 데이터베이스**
- MongoDB
- JSON 형태의 도큐먼트로 저장
- 유연한 스키마

**그래프 데이터베이스**
- Neo4j
- 노드와 엣지로 관계 표현
- SNS, 네트워크 분석에 활용

**칼럼 패밀리 데이터베이스**
- Cassandra, HBase
- 행과 열의 개념 존재
- 동적으로 열 추가 가능

### 🔴 Redis 기본 명령어

**문자열 타입**
```bash
SET key "value"     # 값 저장
GET key             # 값 조회
MGET key1 key2      # 여러 값 조회
DEL key             # 키 삭제
```

**리스트 타입**
```bash
LPUSH key value     # 왼쪽에 추가
RPUSH key value     # 오른쪽에 추가
LPOP key            # 왼쪽에서 제거
RPOP key            # 오른쪽에서 제거
LRANGE key 0 -1     # 전체 조회
```

### 🍃 MongoDB 기본 명령어

**데이터베이스 및 컬렉션 생성**
```javascript
use mydb;                        // 데이터베이스 사용
db.createCollection("mycollection");  // 컬렉션 생성
show dbs;                        // 데이터베이스 조회
show collections;                // 컬렉션 조회
```

**도큐먼트 삽입**
```javascript
db.collection.insertOne({name: "Kim", age: 30});
db.collection.insertMany([{...}, {...}]);
```

**도큐먼트 조회**
```javascript
db.collection.find();
db.collection.find({name: "Kim"});
db.collection.find({age: {$gt: 20}});    // age > 20
db.collection.find({age: {$gte: 20}});   // age >= 20
db.collection.find({$and: [{name: "Lee"}, {age: 12}]});
```

**MongoDB 연산자**
| 연산자 | 설명 | 예시 |
|--------|------|------|
| $eq | 같음 | {field: {$eq: value}} |
| $ne | 같지 않음 | {field: {$ne: value}} |
| $gt | 큼 | {field: {$gt: value}} |
| $gte | 크거나 같음 | {field: {$gte: value}} |
| $lt | 작음 | {field: {$lt: value}} |
| $lte | 작거나 같음 | {field: {$lte: value}} |
| $and | 모든 조건 참 | {$and: [조건1, 조건2]} |
| $or | 하나 이상 조건 참 | {$or: [조건1, 조건2]} |

**도큐먼트 수정**
```javascript
db.collection.updateOne({name: "Kim"}, {$set: {age: 31}});
db.collection.updateMany({age: {$gte: 20}}, {$set: {status: "active"}});
db.collection.updateMany({age: {$gte: 10}}, {$unset: {status: ""}});  // 필드 제거
```

**도큐먼트 삭제**
```javascript
db.collection.deleteOne({name: "Kim"});
db.collection.deleteMany({age: {$gte: 20}});
```

## 🔄 데이터베이스 분할

### 📊 파티셔닝 (Partitioning)

**수평적 분할**
- 테이블의 행을 기준으로 분할
- 범위 분할, 목록 분할, 해시 분할, 키 분할

**수직적 분할**
- 테이블의 열을 기준으로 분할
- 보안이나 성능상의 이유

### 🌐 샤딩 (Sharding)

**정의**
- 분할된 테이블을 별개의 데이터베이스 서버에 분산 저장

**장점**
- 부하 분산 효과
- 확장성 향상

**단위**
- 샤드(Shard): 분할되어 저장된 단위