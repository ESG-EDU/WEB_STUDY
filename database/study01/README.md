# MySQL 또는 MariaDB 기준 (SQL)

## 1. 주석

- 한 줄 주석
```sql
--
```

- 여러 줄 주석
```sql
/*

*/
```

## 2. 데이터베이스 목록 확인
```sql
show databases;
```

## 3. 데이터베이스 선택
```sql
use [데이터베이스명];
```

## 4. 테이블 목록 확인
```sql
show tables;
```

## 5. 테이블 구조(정보) 확인
```sql
desc [테이블명];
```

## 6. 정의어(DDL) - [Create, Drop, Alter]

> ✔ Create 

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/data-definition/create/create-table)
```sql
CREATE [OR REPLACE] [TEMPORARY] TABLE [IF NOT EXISTS] tbl_name
  (create_definition,...) 
	[table_options]... 
	[partition_options]
```

> ✔ Drop

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/data-definition/drop/drop-table)
```sql
DROP [TEMPORARY] TABLE [IF EXISTS] [/*COMMENT TO SAVE*/]
    tbl_name [, tbl_name] ...
    [WAIT n|NOWAIT]
    [RESTRICT | CASCADE]
```

> ✔ Alter

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/data-definition/alter/alter-table)
```sql
ALTER [ONLINE] [IGNORE] TABLE [IF EXISTS] tbl_name
    [WAIT n | NOWAIT]
    alter_specification [, alter_specification] ...
```

## 7. 조작어(DML) - [Select, Insert, Update, Delete]

> ✔ Select

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/data-manipulation/selecting-data/select)
```sql
SELECT
    [ALL | DISTINCT | DISTINCTROW]
    [HIGH_PRIORITY]
    [STRAIGHT_JOIN]
    [SQL_SMALL_RESULT] [SQL_BIG_RESULT] [SQL_BUFFER_RESULT]
    [SQL_CACHE | SQL_NO_CACHE] [SQL_CALC_FOUND_ROWS]
    select_expr [, select_expr ...]
    FROM table_references
      [WHERE where_condition]
      [GROUP BY {col_name | expr | position} [ASC | DESC], ... [WITH ROLLUP]]
      [HAVING where_condition]
      [ORDER BY {col_name | expr | position} [ASC | DESC], ...]
      [LIMIT {[offset,] row_count | row_count OFFSET offset [ROWS EXAMINED rows_limit]} ]
```

> ✔ Insert

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/data-manipulation/inserting-loading-data/insert)
```sql
INSERT [LOW_PRIORITY | DELAYED | HIGH_PRIORITY] [IGNORE]
 [INTO] tbl_name [PARTITION (partition_list)] [(col,...)]
 {VALUES | VALUE} ({expr | DEFAULT},...),(...),...
```

> ✔ Update

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/data-manipulation/changing-deleting-data/update)
```sql
UPDATE [LOW_PRIORITY] [IGNORE] table_references
    SET col1={expr1|DEFAULT} [, col2={expr2|DEFAULT}] ...
    [WHERE where_condition]
```

> ✔ Delete

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/data-manipulation/changing-deleting-data/delete)
```sql
DELETE [LOW_PRIORITY] [QUICK] [IGNORE]
    FROM tbl_name[.*] [, tbl_name[.*]] ...
    USING table_references
    [WHERE where_condition]
```

## 8. 제어어(DCL) - [Grant, Revoke, Commit, Rollback]

> ✔ Grant

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/account-management-sql-statements/grant)
```sql
GRANT rolename TO grantee [, grantee ...]
    [WITH ADMIN OPTION]
```

> ✔ Revoke

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/account-management-sql-statements/revoke)
```sql
REVOKE ALL PRIVILEGES, GRANT OPTION
    FROM user [, user] ...
```

> ✔ Commit

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/transactions/commit)
```sql
COMMIT [WORK] [AND [NO] CHAIN] [[NO] RELEASE]
```

> ✔ Rollback

- 예시: [참조](https://mariadb.com/docs/server/reference/sql-statements/transactions/rollback)
```sql
ROLLBACK [ WORK ] [ AND [ NO ] CHAIN ] 
[ TO [ SAVEPOINT ] {<savepoint name> | <simple target specification>} ]
```