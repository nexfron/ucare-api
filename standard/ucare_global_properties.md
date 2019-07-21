# global.properties

UCARE 동작을 위해 필요한 환경 설정을 선언해 놓은 파일이다.

## 설정 속성 작성법
 - 속성명은 Namespace 방식으로 작성합니다.
 - 다음과 같은 Depth 를 가집니다.
   - 1 Depth : PATH(경로), CONFIG(설정)	
   - 2 Depth : Category(file, url, class, system, cti, ftp 등)
   - 이하 Depth : 기능 
 - 내용 추가 시 1 Depth는 현 사이트의 prefix로 한다. 이하 Depth는 위와 동일    

***Example***
```properties
# PATH(경로) 예제
PATH.FILE.BORD = D:/UCARE_PROJECT_3.7_64bit/workspace/ucareapp_egov_basic_v2/upload/inf

# CONFIG(설정) 예제
CONFIG.SYS.CHK.LOGIN = false
```

## 설정 속성 목록

### PATH(경로)

<table>
    <colgroup>
        <col style="width: 15%;"/>
        <col style="width: 35%;"/>
        <col style="width: 50%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>설명</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>PATH.FILE.BORD</td>
            <td>파일 업로드 경로 - 게시판</td>
            <td>PATH.FILE.BORD=D:/project/workspace/ucareapp/upload/inf</td>
        </tr>
        <tr>
            <td>PATH.FILE.KMS</td>
            <td>파일 업로드 경로 - 상담지식</td>
            <td>PATH.FILE.BORD=D:/project/workspace/ucareapp/upload/kms</td>
        </tr>
        <tr>
            <td>PATH.FILE.UPLOAD</td>
            <td>파일 업로드 경로</td>
            <td>PATH.FILE.BORD=D:/project/workspace/ucareapp/upload</td>
        </tr>
        <tr>
            <td>PATH.FILE.EXCEL</td>
            <td>엑셀 다운로드 경로</td>
            <td>PATH.FILE.BORD=D:/project/workspace/ucareapp/download</td>
        </tr>
        <tr>
            <td>PATH.FILE.BORD</td>
            <td>파일 업로드 경로 - 게시판</td>
            <td>PATH.FILE.BORD=D:/project/workspace/ucareapp/upload/inf</td>
        </tr>
        <tr>
            <td>PATH.URL.CTI</td>
            <td>CTI Websockt URL</td>
            <td>PATH.URL.CTI=http://192.168.123.81:3000</td>
        </tr>
        <tr>
            <td>PATH.URL.CODE.RELOAD</td>
            <td>코드 메모리 Reload URL</td>
            <td>PATH.URL.CODE.RELOAD=http://127.0.0.1:8080</td>
        </tr>
        <tr>
            <td>PATH.CLASS.ENCODE</td>
            <td>형태별 데이터 Format</td>
            <td>PATH.CLASS.ENCODE=com.nexfron.ucareapp.util.CFormat</td>
        </tr>
        <tr>
            <td>PATH.CLASS.CACHE</td>
            <td>코드 메모리 Class 경로</td>
            <td>PATH.CLASS.CACHE=com.nexfron.framework.common.CodeCache</td>
        </tr>
    </tbody>
</table>

### CONFIG(설정)

<table>
    <colgroup>
        <col style="width: 15%;"/>
        <col style="width: 35%;"/>
        <col style="width: 50%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>설명</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>CONFIG.SYS.CHK.LOGIN</td>
            <td>휴먼 계정 잠금 기능 사용 여부</td>
            <td>CONFIG.SYS.CHK.LOGIN=false</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.CHK.PWD.CHG</td>
            <td>주기별 비밀 번호 변경 기능 사용 여부</td>
            <td>CONFIG.SYS.CHK.PWD.CHG=false</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.CHK.PWD.WRG</td>
            <td>비밀번호 입력 오류 기능 사용 여부</td>
            <td>CONFIG.SYS.CHK.PWD.WRG=false</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.CHK.PWD.REUSING</td>
            <td>직전 비밀번호 사용 체크 기능 사용 여부</td>
            <td>CONFIG.SYS.CHK.PWD.REUSING=Y</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.CHK.IP</td>
            <td>접속 IP 체크 기능 사용 여부</td>
            <td>CONFIG.SYS.CHK.IP=false</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.DEFAULT.MENU</td>
            <td>Ucare 초기 화면 설정</td>
            <td>CONFIG.SYS.DEFAULT.MENU=##,11010000</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.DATABASE</td>
            <td>Ucare DB Vendor 설정</td>
            <td>CONFIG.SYS.DATABASE=ORACLE</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.CNT.PWD.WRG</td>
            <td>비밀번호 입력 오류 제한 수</td>
            <td>CONFIG.SYS.CNT.PWD.WRG=5</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.TERM.PWD.MOD</td>
            <td>비밀번호 갱신 주기</td>
            <td>CONFIG.SYS.TERM.PWD.MOD=30</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.TERM.LOGIN</td>
            <td>Ucare 미 접속 날짜</td>
            <td>CONFIG.SYS.TERM.LOGIN=30</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.MENU.MAX.LVL</td>
            <td>메뉴 레벨 정보<br/>메뉴 관리, 메뉴 권한 관리, 사용자 메뉴 정보에서 사용</td>
            <td>CONFIG.SYS.MENU.MAX.LVL=2</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.PWD.POLICY.SOURCE</td>
            <td>비밀번호 정책 설정 경로. ○ DB or File</td>
            <td>CONFIG.SYS.PWD.POLICY.SOURCE = FILE</td>
        </tr>
        <tr>
            <td>CONFIG.SYS.ERR.MSG</td>
            <td>시스템 오류 메시지 사용 여부</td>
            <td>CONFIG.SYS.ERR.MSG=on</td>
        </tr>
        <tr>
            <td>CONFIG.FILE.CHK.UPLOAD</td>
            <td>Upload File Validation 기능 사용 여부</td>
            <td>CONFIG.FILE.CHK.UPLOAD=true</td>
        </tr>
        <tr>
            <td>CONFIG.FILE.VALID.EXT</td>
            <td>Upload 가능한 File 확장자 설정</td>
            <td>CONFIG.FILE.VALID.EXT=jpg,gif,bmp,png,xls,pdf,ppt,doc,hwp</td>
        </tr>
        <tr>
            <td>CONFIG.FILE.VALID.CONTENT.TYPE</td>
            <td>Upload 가능한 File Content Type 설정</td>
            <td>CONFIG.FILE.VALID.CONTENT.TYPE=image/jpeg,image/gif,image/bmp</td>
        </tr>
        <tr>
            <td>CTI Websocket 접속 정보</td>
            <td>IP, SUB IP, PORT, SUB PORT</td>
            <td>
            CONFIG.CTI.IP=192.168.151.19<br/>
            CONFIG.CTI.IP.SUB=192.168.151.19<br/>
            CONFIG.CTI.PORT=3000
            </td>
        </tr>
        <tr>
            <td>Ucare 암호화 Key</td>
            <td>
            Ucare에서 사용 중인 암호 Key(AES, DES 등)<br/>
            CONFIG.CRPT으로 시작 된다
            </td>
            <td>CONFIG.CRPT.AES, CONFIG.CRPT.DES</td>
        </tr>
        <tr>
            <td>CONFIG.WORK.STRT.TIME</td>
            <td>상담업무 시작 시간 설정</td>
            <td>CONFIG.WORK.STRT.TIME=0900</td>
        </tr>
        <tr>
            <td>CONFIG.WORK.END.TIME</td>
            <td>상담업무 종료 시간 설정</td>
            <td>CONFIG.WORK.END.TIME=1800</td>
        </tr>
        <tr>
            <td>CONFIG.WORK.TERM</td>
            <td>상담업무 스케줄 시간 간격 설정</td>
            <td>CONFIG.WORK.TERM=15</td>
        </tr>
    </tbody>
</table>




