## 데이터베이스 실습 준비

1. docker 설치
2. docker container 생성
```bash
docker compose up -d
```
3. mariadb에 실습 데이터 넣기

- docker mariadb 접속
```bash
docker exec -it db bash
```

- dump 파일 위치 이동
```bash
cd /usr/local/share/samples
```

- 클라이언트 접속 명령어
```bash
mariadb -uroot -p
```

- 데이터베이스 연결
```sql
use edu
```

- 테이블 목록 확인
```sql
show tables
```

- dump 데이터 넣기
```sql
source load_departments.dump ;
source load_employees.dump ;
source load_dept_emp.dump ;
source load_dept_manager.dump ;
source load_titles.dump ;
source load_salaries1.dump ;
source load_salaries2.dump ;
source load_salaries3.dump ;
```

## 데이터 확인 (로컬 클라이언트 접속)

1. 데이터베이스 선택
```sql
use edu;
```

2. 테이블 목록 확인
```
show tables;
```

3. `employees` 테이블 구조(정보) 확인
```slq
desc edu.employees;
```

4. `employees` 테이블 조회
```sql
select emp_no, birth_date, first_name,last_name, gender, hire_date from employees;
```

> 실습

- 1. 사원의 이름, 성별 정보 추출 
```sql
select first_name, gender
from employees;
```

- 2. 부서의 부서번호, 부서명 추출
```sql
select dept_no, dept_name
from departments;
```

- 3. 사원의 사원번호, 연봉 추출  
```sql
select emp_no, salary
from salaries;
```

- 4. 사원의 사원번호, 직책 추출
```sql
select emp_no, title
from titles;
```
