## SQL 채우기

- 동등 조인을 할 때 NULL 끼리는 동등하지 않게 간주된다. 
- 논리 모델링의 외래키는 물리 모델에서 반드시 구현되지는 않는다.(OPTION)
- 데이터 모델링의 3요소 : Things, Attributes, Relationship
- GROUP BY 집합
  - GROUP BY ROLLUP(DNAME, JOB) <BR>= GROUP BY DNAME,JOB UNION ALL GROUPT BY DNAME UNION ALL 모든 집합 그룹 결과<BR>
  - GROUP BY GROUPING SET(DNAME, JOB) <BR>=GROUP BY DNAME UNION ALL GROUP BY JOB <BR>
  - GROUP BY CUBE(DNAME, JOB) <BR> = GROUP BY DNAME, JOB UNION ALL GROUP BY NAME UNION ALL GROUP BY JOB UNION ALL 모든 집합 그룹 결과 <BR>
  - GROUP BY GROUPING SETS(A,B,C) <BR>=GROUP BY A UNION ALL GROUP BY B UNION ALL GROUP BY C
  - GROUPING SETS(A,B,NULL) → NULL은 모든 데이터를 합 그룹으로 간주해 집계 함수의 전체 결과를 구하는 역할을 수행한다. 
- ANSI SQL
  - 조인 조건절(ON절)에 사용된 조건절은 조인 전 조건으로 적용
  - ON 절 이후 WHERE 절에 쓰인 조건절은 조인 후 조건으로 적용
- VIEW는 논리적인 SELECT를 포함하는 OBJECT로 실제 데이터를 저장하지 않는다.
- SQL SERVER - INSERT 구문
  - IDENTITY[SEED, INCREMENT] : 시작값, 증가값 - 해당 컬럼에 값 넣을 경우 에러 발생 
- ORACLE
  - CHECK : 조건을 만족하지 못할 경우 에러가 발생하나 NULL은 무시되고 진행된다. 
- HASH JOIN
  - Equal join만 가능하다.
  - 각 테이블에 INDEX가 반드시 필요한 것은 아니다.
  - 일반적으로 작은 테이블을 MEMORY에 올리는 선행 테이블로 사용한다.
- Sort Merge Join은 조인을 위해 사전 sort 작업이 필요하다.
- LIKE의 경우 컬럼을 무조건 문자로 형변환한다.(숫자 > 문자)
- 부정형 비교는 INDEX 사용이 불가능하다. 
- CHAR 타입은 길이가 다르다면 작은 쪽에 SPACE를 추가하여 길이를 같게 한 후 비교한다.
- RANGE BETWEEN start_point AND end_point
  - start_point는 end_point와 같거나 작은 값이 들어감
  - Default값은 RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
  - UNBOUNDED PRECEDING : start_point만 들어갈 수 있으며, 파티션의 first row
  - UNBOUNDED FOLLOWING : end_point만 들어갈 수 있으며, 파티션의 last row
  - CURRENT ROW : start, end_point 둘다 가능. 윈도우는 CUREENT ROW에서 start하거나 end 함
* TOP (Expression) [PERCENT] [WITH TIES]
  - WITH TIES : ORDER BY 조건 기준으로 TOP N 의 마지막 행으로 표시되는 데이터 값과 동일한 값을 가진 행 추가 반환
- ASCI JOIN SQL > NATURAL JOIN은 열 식별자가 사용될 수 없다. (ex: EMP.DEPTNO) 에러난다. 자연 조인하면 두 개의 열 중 한 개만 남으니깐

<br> 여기까지 21회차 sqld 모의고사 부족한 개념 채우기

---