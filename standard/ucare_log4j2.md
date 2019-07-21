# 로깅

UCARE 는 log4j2 를 사용하여 로깅하며, 동작 시 서버의 log레벨 및 경로 설정에 대한 설명입니다.

 - UCARE 프레임워크는 [log4j2](https://logging.apache.org/log4j/2.x/) 를 사용합니다.
 - log4j2 에 대한 참조
   - [Log4j2 환경설정 - 전자정부 프레임워크](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:rte3:fdl:%EC%84%A4%EC%A0%95_%ED%8C%8C%EC%9D%BC%EC%9D%84_%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94_%EB%B0%A9%EB%B2%95)
   - [Log4j2 설정](https://theuphill.tistory.com/7)

## 로그레벨

> 디버그용 로그는 꼭 `DEBUG` 를 사용하여 로깅합니다.

<table>
    <colgroup>
        <col style="width: 20%;"/>
        <col style="width: 80%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>로그레벨</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>FATAL</td>
            <td>아주 심각한 에러가 발생한 상태를 나타냄. 시스템적으로 심각한 문제가 발생해서 어플리케이션 작동이 불가능할 경우가 해당하는데, 일반적으로는 어플리케이션에서는 사용할 일이 없음</td>
        </tr>
        <tr>
            <td>ERROR</td>
            <td>요청을 처리하는중 문제가 발생한 상태를 나타냄</td>
        </tr>
        <tr>
            <td>WARN</td>
            <td>처리 가능한 문제이지만, 향후 시스템 에러의 원인이 될 수 있는 경고성 메시지를 나타냄</td>
        </tr>
        <tr>
            <td>INFO</td>
            <td>로그인, 상태변경과 같은 정보성 메시지를 나타냄</td>
        </tr>
        <tr>
            <td>DEBUG</td>
            <td>개발시 디버그 용도로 사용한 메시지를 나타냄</td>
        </tr>
        <tr>
            <td>TRACE</td>
            <td>디버그 레벨이 너무 광범위한 것을 해결하기 위해서 좀더 상세한 상태를 나타냄</td>
        </tr>
    </tbody>
</table>

## Appender

<table>
    <colgroup>
        <col style="width: 20%;"/>
        <col style="width: 20%;"/>
        <col style="width: 60%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Appenders</th>
            <th>태그명</th>
            <th>출력위치</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ConsoleAppender</td>
            <td>Console</td>
            <td>로그를 콘솔에 출력하기 위한 Appender</td>
        </tr>
        <tr>
            <td>FileAppender</td>
            <td>File</td>
            <td>로그를 파일에 출력하기 위한 Appender</td>
        </tr>
        <tr>
            <td>RollingFileAppender</td>
            <td>RollingFile</td>
            <td>조건에 따라 로그를 파일에 출력하기 위한 Appender</td>
        </tr>
        <tr>
            <td>JDBCAppender</td>
            <td>JDBC</td>
            <td>로그를 RDB에 출력하기 위한 Appender</td>
        </tr>
    </tbody>
</table>

## UCARE 로그 설정
 - `log4j2.xml` 파일 위치는 `/src/main/resources/` 하위에 있습니다.

### log 파일 디렉토리 및 파일명 설정
 - `property` 로 log 파일의 디렉토리 및 파일명을 설정합니다.
 - log 파일명은 `filename` 으로 설정합니다.

```xml
<Properties>
    <!-- log 파일 디렉토리 -->
    <property name="filedir">D://UCARE_PROJECT_3.7_64bit//log//basic</property>
    <!-- log 파일명 -->
    <property name="filename">ucare_${date:yyyyMMddHHmmss}</property>
</Properties>
```
위 예제의 경우 파일명은 `ucare_20190701121315.log` 와 같은 파일명으로 로깅됩니다.

### Appenders 설정
 - `ConsoleAppender`, `RollingFileAppender` 를 설정합니다.
 - `RollingFileAppender` 의 경우, 필요에 따라 다음 설정을 변경합니다.
   - SizeBasedTriggeringPolicy
   - filePattern

 ```xml
<Appenders>
    <Console name="console" target="SYSTEM_OUT">
        <PatternLayout pattern="%d %5p [%c] %m%n" />
    </Console>

    <RollingFile name="dailyRollingFile" fileName="${filedir}/${filename}.log" 
                                    filePattern="${filedir}/$${date:yyyy}/$${date:MM}/$${date:dd}/${filename}.%d{yyyy-MM-dd}.%i.log">
        <PatternLayout pattern="%d %5p [%c] %m%n"/>
        <Policies>
            <!-- size 단위: Byte(default), KB, MB, or GB -->
            <SizeBasedTriggeringPolicy size="10 MB" />
        </Policies>
        
        <DefaultRolloverStrategy fileIndex="nomax" />
    </RollingFile>		
</Appenders>
 ```