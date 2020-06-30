# Mapper 설정화면 표준

UCARE 의 MyBatis XML 설정 파일 `sql-mapper-config.xml` 은 다음과 같은 내용으로 설정되어 있습니다. 자세한 내용은 [MyBatis 매퍼설정](https://mybatis.org/mybatis-3/ko/configuration.html) 에서 확인합니다.

### settings
Runtime 시 Mybatis 의 설정으로 정의하지 않는 경우, default 값으로 설정됩니다.

```xml
<settings>
  <setting name="cacheEnabled" value="true"/>
  <setting name="defaultStatementTimeout" value="60"/>
  <setting name="jdbcTypeForNull" value="VARCHAR"/>
  <setting name="mapUnderscoreToCamelCase" value="true"/>
  <setting name="callSettersOnNulls" value="true"/>
  <setting name="defaultExecutorType" value="REUSE"/>
</settings>
```
  - cacheEnabled (true/false) : 설정에서 각 매퍼에 설정된 캐시를 전역적으로 사용할지 말지에 대한 여부. default ***true***

  - defaultStatementTimeout (양수) : 데이터베이스로의 응답을 얼마나 오래 기다릴지를 판단하는 타임아웃을 설정. default ***설정되지 않음(null)***

  - jdbcTypeForNull : JDBC타입을 파라미터에 제공하지 않을때 null값을 처리한 JDBC타입을 명시한다. 일부 드라이버는 칼럼의 JDBC타입을 정의하도록 요구하지만 대부분은 NULL, VARCHAR 나 OTHER 처럼 일반적인 값을 사용해서 동작한다.

  - mapUnderscoreToCamelCase (true/false) : 전통적인 데이터베이스 칼럼명 형태인 A_COLUMN을 CamelCase형태의 자바 프로퍼티명 형태인 aColumn으로 자동으로 매핑하도록 함. default ***False***

  - callSettersOnNulls (true/false) : 가져온 값이 null일때 setter나 맵의 put 메소드를 호출할지를 명시 Map.keySet() 이나 null값을 초기화할때 유용하다. int, boolean 등과 같은 원시타입은 null을 설정할 수 없다는 점은 알아두면 좋다. default ***false***
  
  - defaultExecutorType (SIMPLE/REUSE/BATCH) : 디폴트 실행자(executor) 설정. SIMPLE 실행자는 특별히 하는 것이 없다. REUSE 실행자는 PreparedStatement를 재사용한다. BATCH 실행자는 구문을 재사용하고 수정을 배치처리한다.. default ***SIMPLE***


### typeAliases
JAVA 타입에 대한 짧은 이름으로 공통으로 사용하는 타입은 추가하여 사용합니다.

```xml
<typeAliases>
  <typeAlias alias="egovMap" type="egovframework.rte.psl.dataaccess.util.EgovMap"/>
  <typeAlias alias="map" type="java.util.Map"/>
  <typeAlias alias="hashMap" type="java.util.HashMap"/>
</typeAliases>
```