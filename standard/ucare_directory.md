# 디렉토리 구조

UCARE 디렉토리 구조는 `/src/main` 기준으로 다음과 같습니다.

<table>
    <colgroup>
        <col style="width: 15%;"/>
        <col style="width: 20%;"/>
        <col style="width: 15%;"/>
        <col style="width: 50%;"/>
    </colgroup>
    <thead>
        <tr>
            <th colspan="3">디렉토리</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>/java/com</td>
            <td rowspan=2>/nexfron</td>
            <td>framgework</td>
            <td>UCARE 프레임워크 JAVA 소스</td>
        </tr>
        <tr>
            <td>ucareapp</td>
            <td>Applicaion 및 업무별 JAVA 소스</td>
        </tr>        
        <tr>
            <td rowspan=3>/resource</td>
            <td colspan=2>/spring</td>
            <td>전자정부 프레임워크 설정 파일을 관리</td>
        </tr>
        <tr>
            <td>/sqlmap/mappers</td>
            <td>/oracle</td>
            <td>업무별 SQL 파일을 관리</td>
        </tr>
        <tr>
            <td colspan=2>/log4j2.xml</td>
            <td>Logging 설정 파일</td>
        </tr>
        <tr>
            <td rowspan=9>/webapp</td>
            <td colspan=2>/common</td>
            <td>공통 파일(jsp, xml) 을 관리</td>
        </tr>
        <tr>
            <td colspan=2>/css</td>
            <td>CSS 파일을 관리</td>
        </tr>
        <tr>
            <td colspan=2>/images</td>
            <td>Image 파일을 관리</td>
        </tr>
        <tr>
            <td colspan=2>/lib</td>
            <td>javascript 라이브러리(editor, grid, jquery 등)</td>
        </tr>        
        <tr>
            <td colspan=2>/js</td>
            <td>업무별 Javascript 파일 소스</td>
        </tr>
        <tr>
            <td rowspan=3>/WEB-INF</td>
            <td>/config</td>
            <td>실행 환경 파일을 관리</td>
        </tr>
        <tr>
            <td>/jsp</td>
            <td>업무별 JSP 파일을 관리</td>
        </tr>
        <tr>
            <td>/lib</td>
            <td>프레임워크 실행에 필요한 JAVA 라이브러리(jar) 파일을 관리</td>
        </tr>
    </tbody>
</table>