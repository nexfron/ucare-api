# SQL 작성

XML(MyBatis) 파일 작성 표준에 대한 설명입니다.  
MyBatis 에 대한 자세한 내용은 [myBatis](http://www.mybatis.org/mybatis-3/ko/index.html) 가이드 문서를 참조합니다.

## SQL 작성표준
  - SQL은 파라미터를 제외하고 모두 대문자로 작성
  - SELECT, FROM, WHERE 등 SQL 예약어는 오른쪽 정렬 을 기준
  - 1 Line 에 1개 컬럼, 1개 테이블을 표시
  - 필드명 사이의 콤마(,) 는 컬럼 앞에 사용
  - 테이블 Alias 는 A,B,C 순서로 지정
  - 컬럼에 Alias 를 부여하는 경우, `AS` 를 사용
  - SQL 식별자 `XML파일경로 - SQL ID (SQL 설명)` 를 열기(/*), 닫기(*/) 로 표시
  - SELECT 는 필요한 컬럼만 포함하여 구성하고, `SELECT *` 같은 사용을 금합니다.

## SQL FORMAT
 - 다음의 경우 공백(space) 를 부여합니다.
   - equals(=) 전후
   - comma(,) 뒤
 - AND 또는 OR 전, New Line 을 부여합니다.
 - sub query 는 동일하게 Format 을 사용합니다.

**Example**

```sql
SELECT /* /sample/sample.xml - selectSampleList(샘플 목록 조회) */
       A.COL1
       , A.COL2
       , FN_CODEBOOK('TEST001', A.COL3) AS "COL3_NM"
  FROM TB_TABLE1 A
     , TB_TABLE2 B
 WHERE A.COL1 = B.COL1  
   AND A.COL1 = #{col1}
 ORDER BY A.COL1
        , A.COL2
;

SELECT /* /sample/sample.xml - selectSampleList(샘플 목록 조회) */
       A.COL1
       , (SELECT MAX(B.COL2)
            FROM TB_TABLE2 B
           WHERE B.COL1 = A.COL1
             AND B.COL2 = 'Y') AS "MAX_COL"
  FROM TB_TABLE1 A
 WHERE A.COL3 IN (SELECT C.COL3
                    FROM TB_TABLE2 C
                   WHERE C.COL5 = 'N')
;

INSERT /* /sample/sample.xml - insertSample(샘플 등록) */
  INTO TB_TABLE1
     ( COL1
     , COL2
     , COL3)
VALUES
     ( #{col1}
     , #{col2}
     , SYSDATE)
;

UPDATE /* /sample/sample.xml - updateSample(샘플 수정) */
       TB_TABLE1
   SET COL1 = #{col1}
     , COL2 = #{col2}
 WHERE COL5 = #{col5}
;

DELETE /* /sample/sample.xml - deleteSample(샘플 삭제) */
  FROM TB_TABLE1 A
 WHERE A.COL1 = #{col1}
   AND A.COL2 IN (SELECT B.COL2
                    FROM TB_TABLE2 B
                   WHERE B.COL1 = A.COL1)
;
```