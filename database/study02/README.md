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

> `LIMIT` 알아보기

- 문법 1: LIMIT 몇 개
- 문법 2: LIMIT offset, 몇 개
- offset은 0부터 시작

```sql
select * from employees limit 3;
```

```sql
select * from employees limit 4, 3;
```

### 산술 연산자 `+, -, *, /`

- 1. 단순 계산

```sql
select 10 + 10;
select 20-10, 30*3, 40/2;
```

- 2. 특정 컬럼 데이터 연산
```sql
select emp_no, salary, salary + 10 as '10증가 값' from salaries;
```

- [문제] 사번, 현재 연봉, 10% 인상된 각 사원의 연봉 조회 (조회 결과에서 상위 20개 로우만 조회)

```sql
select emp_no, salary, salary * 1.1 as '10% 인상' from salaries  limit 20;
```

### `distinct` 중복 제거

```sql
select distinct dept_no from dept_manager; 
```

### `where` 사용되는 연산자
- 비교(관계) 연산자

| 기호 | 뜻 |
| :---: | :---: |
| `<` | 작다, 미만 |
| `>` | 크다, 초과 |
| `<=` | 작거나 같다, 이하 |
| `>=` | 크거나 같다, 이상 |
| `=` | 같다 |
| `<>` | 다르다 |

- 논리 연산자: 

| 기호 | 뜻 |
| :---: | :---: |
| `and` | 모두 참일 때 TRUE |
| `or` | 하나라도 참이면 TRUE |
| `not` | 조건 반전 |

- 범위 연산자: 

| 기호 | 뜻 |
| :---: | :---: |
| `between A and B` | A ~ B |

- 집합 연산자: 

| 기호 | 뜻 |
| :---: | :---: |
| `in (값1, 값2, ...)` | 일치하는 데이터 |
| `not in (값1, 값2, ...)` | 불일치하는 데이터 |

- 문자열 연산자:

| 기호 | 뜻 |
| :---: | :---: |
| `like` | 일치 |
| `not like` | 불일치 |
| `%` | 와일드 카드 |
| `_` | 값 하나 |

- `null` 연산자:

| 기호 | 뜻 |
| :---: | :---: |
| `is null` | 값이 null이면 TRUE |
| `is not null` | 값이 null이 아니면 TRUE |

> 실습

- 사번이 `10001`인 직원의 사번과 이름 조회
```sql
select emp_no, first_name from employees
```

- [문제 1] `d005` 부서 매니저의 사원번호, 부서번호 추출하시오.
```sql
select emp_no, dept_no from dept_manager
```

- [문제 2] `d003` 부서 소속(담당)이 아닌 매니저들의 사원번호, 부서번호 추출하시오.
```sql
select emp_no, dept_no from dept_manager
```

- [문제 3] 연봉이 `150,000` 이상인 사원들의 사원번호, 연봉 추출하시오.
```sql
select emp_no, salary from salaries
```

- [문제 4] `1986`년 이후에 입사한 사원의 사원번호, 입사일, 이름 추출하시오.
```sql
select emp_no, hire_date, first_name from employees
```

- [문제 5] `1990`년 이후부터 매니저로 근무하고 있는 사원들의 사원번호, 부서번호, 매니저 시작날짜 추출하시오.
```sql
select emp_no, dept_no, from_date from dept_manager
```

- [문제 6] `1990`년 이전 입사한 사원들의 사원번호, 입사일 추출하시오.
```sql
select emp_no, hire_date from employees
```

- [문제 7] `1990`년 이후 입사한 남자 사원의 사원번호, 성별, 입사일 추출
```sql
select emp_no, gender, hire_date from employees
```

- [문제 8] `1990`년 이후부터 연봉을 `60,000` 이상 받는 사원의 사원번호, 연봉, 연봉 시작일 추출
```sql
select emp_no, salary, from_date from salaries
```

- [문제 9] `d001` 부서와 `d002` 부서 매니저의 사원번호, 부서번호 추출
```sql
select emp_no, dept_no from dept_manager
```

- [문제 10] 직책이 `staff`이거나 `engineer`인 사원의 사원번호, 직책 추출
```sql
select emp_no, title from titles
```

- [문제 11] `d003` 부서 소속(담당)이 아닌 매니저의 사원번호, 부서번호 추출
```sql
select emp_no, dept_no from dept_manager
```

- [문제 12] 연봉이 `60,000` 이상 `70,000` 이하인 사원의 사번, 연봉 추출
```sql
select emp_no, salary from salaries
```

- [문제 13] `d001` 부서와 `d002` 부서 매니저의 사번, 부서번호 추출
```sql
select emp_no, dept_no from dept_manager
```

- [문제 14] `d001` 부서와 `d002` 부서가 아닌 매니저의 사번, 부서번호 추출
```sql
select emp_no, dept_no from dept_manager
```

- [문제 15] 이름이 `B`로 시작하는 사원의 사번, 이름 조회
```sql
select emp_no, first_name from employees
```

- [문제 16] 이름의 두 번째 글자가 `r`인 사원의 사번, 이름 조회
```sql
select emp_no, first_name from employees
```

- [문제 17] 이름이 `i`로 끝나는 사원의 사번, 이름 조회
```sql
select emp_no, first_name from employees
```

- [문제 18] 이름이 `B`로 시작하지 않는 사원의 사번, 이름 조회
```sql
select emp_no, first_name from employees
```
