### [함수] 숫자

- 절댓값
```sql
select abs(100), abs(-100);
```

- 소수점 이하 올림
```sql
select ceil(10.42), ceil(10.5), ceil(10.6);
```

- 소수점 이하 내림
```sql
select floor(10.432), floor(10.5), floor(10.6);
```

- 반올림
```sql
select round(10.432), round(10.5), round(10.6) round(166.555, 0), round(166.555, 1), round(166.555, -1);
```

- 버림
```sql
select truncate(166.555,0), truncate(166.555, 1), truncate(166.555, -1);
```

### [함수] 문자

- 이어주기
```sql
select concat('one', 'two', 'three');
```

> 실습

- 직원의 사번, 이름 조회 단, 이름은 first_name, last_name을 한 컬럼으로 표시
```sql
select emp_no as '사번', concat(first_name, '', last_name) as '이름' from employees;
```

### [함수] 특정 위치에 추가

- 문법: `insert('문자'(컬럼명), 시작위치, 몇개, '추가문자')`
```sql
select insert('abcdefg', 2, 1, 'wow');
```

- 2번째 자리에서 0개를 wow로 변경
```sql
select insert('abcdefg', 2, 0, 'wow');
```

- bcd를 삭제하시오!
```sql
select insert('abcdefg', 2, 3, '');
```

### [정렬] `order by`

| 정렬 | 결과 |
| :---: | :---: |
| `asc` | 오름차순 (기본값) |
| `desc` | 내림차순 |

- 연봉 오름차순, 연봉 시작일 내림차순으로 하여 사번, 연봉, 연봉 시작일 조회
```sql
select emp_no, salary, from_date from salaries order by salary asc, from_date desc;
```

- 직책을 오름차순, 업무 시작일을 내림차순하여 사번, 직책, 업무 시작일을 조회
```sql
select emp_no, title, from_date from titles order by 2 asc, 3 desc;
```
