# 디렉토리 구조

UCARE 디렉토리 구조는 `/src/main` 기준으로 다음과 같습니다.

|디렉토리|||설명|
|-------|-------|-------|-------|
|/java/com|/nexfron|core|UCARE 프레임워크 JAVA 소스|
|||ucareapp|Application 및 업무별 JAVA 소스|
|/resource|/spring||전자정부 프레임워크 설정 파일을 관리
||/properties||properties 파일을 관리
||/sqlmap/mappers|/oracle|업무별 SQL(Oracle) 파일을 관리
|||/mariadb|업무별 SQL(MariaDB) 파일을 관리
||/log4j2.xml||Logging 설정 파일
|/webapp|/common||공통 파일(jsp)을 관리
||/static|/css|CSS 파일을 관리
|||/images|Image 파일을 관리
|||/js|업무별 Javascript 파일 소스
|||/lib|javascript 라이브러리(editor, grid, jquery 등)
||/WEB-INF|/config|실행 환경 파일을 관리
|||/jsp|업무별 JSP 파일을 관리
|||/lib|프레임워크 실행에 필요한 JAVA 라이브러리(jar) 파일을 관리
|||/tiles|메인화면을 구성하는 Layout JSP 파일을 관리