### SQL 서브쿼리 

``` SQL
스칼라 서브쿼리 
반드시 1행 1열로만 반환 해야하고 그렇지 않으면 오류 발생 

SELECT SAL 
(SELECT AVG(SAL)
FROM EMP)
FROM EMP; 예시 


```

``` SQL 
SELECT * 인라인 뷰 
FROM (SELECT ROWNUM AS NUM ENAME FROM MP)
WHERE NUM < 5; 
``` 
EX) 가상의 테이블을 생성하여 EMP 테이블 상위 4명의 사원 이름 생성 

예제 

``` SQL
C1        
A
A
B
B
B
NULL 

C2 
100
200
100
NULL
200 


CREATE VIEW V_TBL 
AS 
SELECT * 
FROM TBL 
WHERE C1 = "B" OR C1 IS NULL 
#생성 

C1 C2 
B 200
B 100
B NULL 
NULL 200 
V_TBL 생성 

B 200 


조회 SQL 
SELECT SUM(C2) C2 
FROM V_TBL
WHERE C2 >= 200 AND C1 ="B"
``` 


> WINDOW 함수 

``` SQL
순위 함수 : RANK() DENSE_RANK()
ROW_NUMBER()
SELECT WINDOW() OVER(PARTITION BY 
ORDER BY 
ROWS, RANGE ) 
FROM TABEL ; 
```

```SQL
SELECT JOB , SUM(SAL) OVER (PARTITION BY JOB 
ORDER BY SAL DESC 
ROWS UNBOUNDED PRECEDING) AS SUM_SAL 
PARTITION BY JOB 1. JOB별로 나누어서 
ORDER BY SAL DESC 연봉별로 오름차순으로 나눔 
ROWS 

ROWS UNBOUNDED PRECEDING <- 맨 위에서 행부터 지금행까지 연산을 실시하자


> 1. JOB별로 연봉의 합계를 가져올건데 JOB별 누적합계
```

``` SQL

RANK()함수 
SELECT ENAME , SAL,RANK() OVER(ORDER BY SAL) AS RANK 
FROM EMP ; 

연속되지 않은 RANK값이 나옴 
중복 순위가 나오면 그냥 다음 값으로 넘어감 
예) 1,2,3,4,4,6 
DENSE_RANK()
예) 1,2,3,4,4,5,
DENSE_RANK() 같은 경우에는 중복값 이후 다음 값도 매겨줌
연속적 등수도 나온다 


```

``` SQL
SELECT EMPNO, ENAME , SAL.
SUM(SAL) OVER (ORDER BY SAL , ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING ) TOTSAL 연봉순으로 집계를 할건데 첫 행부터 끝행까지의 SUM(SAL)합을 구한단 뜻 

FROM EMP ;

SELECT EMPNO, ENAME, SAL,
  SUM(SAL) OVER (ORDER BY SAL
  ROWS BETWEEN UNBOUNDED PRECEDING
  AND CURRENT ROW) TOTSAL
FROM EMP;
# 이 경우 첫 행을 지정한 UNBOUNDED 부터 끝 지점을 CURRENT ROW로 지정했을때 
TOTSAL의 누적합계를 나타냄 

```

``` SQL

SELECT 고객명, 고객번호,NVL(생년,9999) AS 정답칼럼 
FROM c_INFO 

# NVL(A,B) NVL은 A값이 NULL 값이면 B출력 아니면 A값을 출력 

```