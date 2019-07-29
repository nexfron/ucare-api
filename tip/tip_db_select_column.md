# DB 별 컬럼 목록 조회

Database 별 컬럼 목록 조회 Query 

## Oracle
 
```sql
SELECT
     A.OWNER
    , A.TABLE_NAME
    , A.COLUMN_ID
    , A.COLUMN_NAME
    , B.COMMENTS
    , A.DATA_TYPE
    , A.DATA_LENGTH
    , A.NULLABLE
FROM   ALL_TAB_COLUMNS A
     , ALL_COL_COMMENTS B
WHERE  A.OWNER = B.OWNER
      AND A.TABLE_NAME = B.TABLE_NAME
      AND  A.COLUMN_NAME = B.COLUMN_NAME
      AND A.OWNER = 'UCARE_APP_BASIC'      /*owner name*/
--      AND A.TABLE_NAME = 'UC_SYS_USER'   /*table name*/
ORDER BY A.TABLE_NAME, A.COLUMN_ID
```


## MariaDB
 
```sql
SELECT
  TABLE_NAME
, ORDINAL_POSITION
, COLUMN_NAME
, COLUMN_COMMENT
, DATA_TYPE
, CHARACTER_MAXIMUM_LENGTH
, IS_NULLABLE
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_SCHEMA = 'ucare_app_basic'
-- AND   TABLE_NAME = 'UC_SYS_USER' /*table name*/
ORDER BY TABLE_NAME, ORDINAL_POSITION
```


## MS-SQL
 
```sql
SELECT 
     A.NAME                    AS TABLE_NAME            -- Table Name
     , D.COLORDER                AS COLUMN_IDX            -- Column Index
     , C.VALUE                    AS TABLE_DESCRIPTION    -- Table Description
     , D.NAME                    AS COLUMN_NAME            -- Column Name
     , E.VALUE                    AS COLUMN_DESCRIPTION    -- Column Description
     , F.DATA_TYPE                AS TYPE                    -- Column Type
     , F.CHARACTER_OCTET_LENGTH    AS LENGTH                -- Column Length
     , F.IS_NULLABLE            AS IS_NULLABLE            -- Column Nullable
     , F.COLLATION_NAME            AS COLLATION_NAME        -- Column Collaction Name
  FROM SYSOBJECTS A WITH (NOLOCK)
  INNER JOIN SYSUSERS B WITH (NOLOCK)        ON A.UID = B.UID
  INNER JOIN SYSCOLUMNS D WITH (NOLOCK)        ON D.ID = A.ID
  INNER JOIN INFORMATION_SCHEMA.COLUMNS F WITH (NOLOCK)
     ON A.NAME = F.TABLE_NAME
    AND D.NAME = F.COLUMN_NAME
   LEFT OUTER JOIN SYS.EXTENDED_PROPERTIES C WITH (NOLOCK)
     ON C.MAJOR_ID = A.ID
    AND C.MINOR_ID = 0
    AND C.NAME = 'MS_Description'
   LEFT OUTER JOIN SYS.EXTENDED_PROPERTIES E WITH (NOLOCK)
     ON E.MAJOR_ID = D.ID
    AND E.MINOR_ID = D.COLID
    AND E.NAME = 'MS_Description'  
  WHERE 1=1
    AND A.TYPE = 'U'
--    AND A.NAME = 'UC_SYS_USER' /*table name*/
  ORDER BY A.NAME, D.COLORDER
```