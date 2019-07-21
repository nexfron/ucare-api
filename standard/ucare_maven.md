# Maven

UCARE 는 전자정부 프레임워크 기반으로 Maven 을 사용하여 프로젝트를 관리합니다.
Maven 에 대한 자세한 내용은 다음을 참조
 - [전자정부 표준프레임워크 기반 개발 시작하기](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:dev2:gettingstarted)
 - [Maven 정복](https://wikidocs.net/book/1910)

## 개발환경 설정
 - [MavenRepository 설치디렉토리]/settings.xml 파일의 localRepository 항목의 값을 다음과 같이 수정합니다.

```xml
<settings xmlns="http://maven.apache.org/settings/1.0.0" 
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
        ...
    <localRepository> [MavenRepository 설치디렉토리]/repository </localRepository>
        ...
</settings>
```
 - `window>preferences` 메뉴를 선택하여 설정화면을 표시합니다. 설정화면에서 Maven>Installtions 의 User Settings 항목을 [MavenRepository 설치디렉토리]/settings.xml 파일로 설정합니다.
![](http://www.nexfron.com/ucare_images/eclilpse_maven.jpg)


## 프로젝트 정보(pom.xml)
 - `pom.xml` 에서 프로젝트 정보를 수정합니다.
   - groupId
     - 프로젝트의 그룹명, 일반적으로 다른 컴포넌트와 라이브러리와 차별될 수 있는 유니크한 명칭을 가짐
     - 관례적으로 회사 도메인명(google.com, naver.com)을 거꾸로한 명칭을 사용함 
   - artifactId
     - 해당 프로젝트 명칭(컴포넌트 명칭), groupId 범위 내에서 유일해야함
   - modelVersion
     - pom.xml을 이루고 있는 maven xml문서 형식의 버전이다. 현재는 무조건 4.0.0 이다.
   - version
     - 해당 artifact(컴포넌트)의 version, 뒤쪽 SNAPSHOT은 아직 개발 중임을 의미함
   - packaging
     - 어떤 파일 형식으로 패키징할 것인가를 정의, jar, war, exe 등이 올 수 있음


***Example***

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>ucare.app.egov</groupId> <!-- 라이브러리 식별 namespace -->
	<artifactId>ucareapp_egov_basic_site</artifactId>	<!-- 라이브러리 명 -->
	<packaging>war</packaging>
	<version>1.0.0</version> <!-- 버전정보 -->
	<name>ucareapp_egov_basic_site</name>
	<url>http://www.egovframe.go.kr</url>
...    
```

## Dependencies 목록
 - UCARE Dependencies 목록은 다음과 같습니다.

### 전자정부 표준프레임워크
```xml
<dependency>
    <groupId>egovframework.rte</groupId>
    <artifactId>egovframework.rte.ptl.mvc</artifactId>
    <version>${egovframework.rte.version}</version>
    <exclusions>
        <exclusion>
            <artifactId>commons-logging</artifactId>
            <groupId>commons-logging</groupId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>egovframework.rte</groupId>
    <artifactId>egovframework.rte.psl.dataaccess</artifactId>
    <version>${egovframework.rte.version}</version>
</dependency>
<dependency>
    <groupId>egovframework.rte</groupId>
    <artifactId>egovframework.rte.fdl.idgnr</artifactId>
    <version>${egovframework.rte.version}</version>
</dependency>
<dependency>
    <groupId>egovframework.rte</groupId>
    <artifactId>egovframework.rte.fdl.property</artifactId>
    <version>${egovframework.rte.version}</version>
</dependency> 
```

### Servlet / JSP
```xml
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>servlet-api</artifactId>
    <scope>provided</scope>
    <version>2.5</version>
</dependency>

<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
    <version>1.2</version>
</dependency>

<dependency>
    <groupId>taglibs</groupId>
    <artifactId>standard</artifactId>
    <version>1.1.2</version>
</dependency>
```

### Database driver
 - Database Driver 는 사이트 환경에 맞추어 설정합니다.
 - MSSQL 은 JDBC Driver 를 다운로드 후, `mvn` 명령으로 설치합니다.
   - MSSQL JDBC Driver [다운로드](http://www.microsoft.com/ko-kr/download/details.aspx?id=11774)
   - Command 창에서 apache-Maven `bin` 디렉토리 이동하여, maven 명령어 실행 
   ```cmd
   mvn install:install-file -Dfile=D:\sqljdbc_4.0\kor\sqljdbc4.jar -Dpackaging=jar -DgroupId=com.microsoft.sqlserver -DartifactId=sqljdbc4 -Dversion=4.0
   ```
   - MSSQL 참조 [MSSQL JDBC Dependency 등록](http://hellogk.tistory.com/92)

```xml
<!-- oracle 11 이상-->
<dependency>
    <groupId>com.oracle</groupId>
    <artifactId>ojdbc6</artifactId>
    <version>14</version>
    <scope>system</scope>
    <systemPath>${project.basedir}/src/main/webapp/WEB-INF/lib/ojdbc6.jar</systemPath>
</dependency>
    
<!-- oracle 10-->
<dependency>
    <groupId>com.oracle</groupId>
    <artifactId>ojdbc14</artifactId>
    <version>10.2.0.4.0</version>
    <scope>system</scope>
    <systemPath>${project.basedir}/src/main/webapp/WEB-INF/lib/ojdbc14-10.2.0.4.0.jar</systemPath>
</dependency>
                
<!-- mysql -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>5.1.47</version>
</dependency>

<!-- mariadb -->
<dependency>
    <groupId>org.mariadb.jdbc</groupId>
    <artifactId>mariadb-java-client</artifactId>
    <version>1.6.5</version>
</dependency>   

                    
<!-- mssql -->           		
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>sqljdbc41</artifactId>
    <version>6.0</version>
</dependency>
```

### MyBatis
```xml
<!-- mybatis -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>3.3.0</version>
</dependency>
<!-- mybatis-spring -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis-spring</artifactId>
    <version>1.2.2</version>
</dependency>   
```

### DBCP
```xml
<dependency>
    <groupId>commons-dbcp</groupId>
    <artifactId>commons-dbcp</artifactId>
    <version>1.4</version>
</dependency> 
```

### jdbc log
```xml
<dependency>
    <groupId>org.lazyluke</groupId>
    <artifactId>log4jdbc-remix</artifactId>
    <version>0.2.7</version>
</dependency>
```

### XML
```xml
<dependency>
    <groupId>jdom</groupId>
    <artifactId>jdom</artifactId>
    <version>1.1</version>
</dependency>
```

### JSON
```xml
<dependency>
    <groupId>org.codehaus.jackson</groupId>
    <artifactId>jackson-core-asl</artifactId>
    <version>1.9.11</version>
    <type>jar</type>
    <scope>compile</scope>
</dependency>
        
<dependency>
    <groupId>org.codehaus.jackson</groupId>
    <artifactId>jackson-mapper-asl</artifactId>
    <version>1.9.11</version>
    <type>jar</type>
    <scope>compile</scope>
</dependency>
```

### 파일 업로드
```xml
<dependency>
    <groupId>commons-fileupload</groupId>
    <artifactId>commons-fileupload</artifactId>
    <version>1.3.1</version>
</dependency>
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.4</version>
</dependency>
```

### FTP
```xml
<dependency>
    <groupId>commons-net</groupId>
    <artifactId>commons-net</artifactId>
    <version>3.3</version>
</dependency>
```

### Excel Apache POI
```xml
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi</artifactId>
    <version>3.12</version>
</dependency>
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi-ooxml</artifactId>
    <version>3.11-beta2</version>
</dependency>
```

### HTML
```xml
<dependency>
    <groupId>org.jsoup</groupId>
    <artifactId>jsoup</artifactId>
    <version>1.7.2</version>
</dependency>
```

