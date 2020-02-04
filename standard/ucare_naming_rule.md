# 명명규칙

파일, DB 등 명명규칙에 대한 설명입니다.

## AppGroup Naming

 - AppGroup은 *업무별로 구분 되어지는 Module단위의 화면을 관리하는 Folder*를 나타내며 논리적 의미를 갖는 영단어(소문자) 로 작성한다.
 - Java Package 및 JSP / Javascrip 디렉토리는 AppGroup 명으로 생성합니다. 

AppGroup 은 다음과 같습니다.

<table>
    <colgroup>
        <col style="width: 15%;"/>
        <col style="width: 15%;"/>
        <col style="width: 55%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>AppGroup</th>
            <th>Prefix</th>
            <th>정의</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>bizcons</td>
            <td>biz</td>
            <td>업무관리</td>
        </tr>
        <tr>
            <td>campaign</td>
            <td>cmp</td>
            <td>캠페인관리</td>
        </tr>
        <tr>
            <td>common</td>
            <td>com</td>
            <td>공통</td>
        </tr>
        <tr>
            <td>customer</td>
            <td>crs</td>
            <td>고객관리</td>
        </tr>
        <tr>
            <td>education</td>
            <td>edc</td>
            <td>교육관리</td>
        </tr>
        <tr>
            <td>examination</td>
            <td>exm</td>
            <td>시험관리</td>
        </tr>
        <tr>
            <td>information</td>
            <td>inf</td>
            <td>정보관리</td>
        </tr>
        <tr>
            <td>knowledge</td>
            <td>kms</td>
            <td>지식관리</td>
        </tr>
        <tr>
            <td>quality</td>
            <td>qas</td>
            <td>QA</td>
        </tr>
        <tr>
            <td>schedule</td>
            <td>sch</td>
            <td>스케줄관리</td>
        </tr>
        <tr>
            <td>statistics</td>
            <td>sts</td>
            <td>통계</td>
        </tr>
        <tr>
            <td>survey</td>
            <td>svy</td>
            <td>설문관리</td>
        </tr>
        <tr>
            <td>system</td>
            <td>sys</td>
            <td>시스템관리</td>
        </tr>
        <tr>
            <td>include</td>
            <td></td>
            <td>공통 include 파일</td>
        </tr>        
        <tr>
            <td>login</td>
            <td></td>
            <td>로그인, 로그아웃</td>
        </tr>
        <tr>
            <td>main</td>
            <td></td>
            <td>메인</td>
        </tr>
        <tr>
            <td>ucare</td>
            <td></td>
            <td>Ucare 공통 Javascript</td>
        </tr>
    </tbody>
</table>


## File Naming Rule

### JSP File
  - JSP 파일명은 AppGroup 의 prefix 로 시작합니다.
  - prefix 를 제외한 단어는 영문 대문자로 시작하며, 합성어 경우 CamelCase 를 적용합니다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>prefix (AppGroup) + 의미있는 명사</td>
            <td>
                crsMain.jsp(상담메인 jsp)<br/>
                sysCodeMng.jsp(코드관리 jsp)
            </td>
        </tr>
    </tbody>
</table>


### Javascript File

 - Javascript 파일명은 AppGroup 의 prefix 로 시작합니다.
 - prefix 를 제외한 단어는 영문 대문자로 시작하며, 합성어 경우 CamelCase 를 적용합니다. 
 - Javascript 파일은 JSP 파일명과 동일 이름을 사용합니다.

> 공통 Javascript 파일은 `/js/ucare` 디렉토리에 위치하며, prefix 는 `ulib`(UCARE Library)을 사용합니다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>prefix (AppGroup) + 의미있는 명사</td>
            <td>
                crsMain.js(상담메인 javascript)<br/>
                sysCodeMng.js(코드관리 javascript)
            </td>
        </tr>
    </tbody>
</table>


### Query Xml File
  - Query XML 파일명은 AppGroup 의 prefix 로 시작합니다.
  - prefix 를 제외한 단어는 영문 대문자로 시작하며, 합성어 경우 CamelCase 를 적용합니다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>prefix (AppGroup) + 의미있는 명사</td>
            <td>
                crsMain.xml(상담메인 xml)<br/>
                sysCode.xml(코드관리 xml)
            </td>
        </tr>
    </tbody>
</table>

### Java File
  - Java 파일명은 AppGroup 의 prefix 로 시작합니다.
  - prefix 를 제외한 단어는 영문 대문자로 시작하며, 합성어 경우 CamelCase 를 적용합니다.
  - Spring MVC 구조에서 JAVA 파일은 Controller, Service, Service implement, DAO 파일을 가지며, 각 파일의 suffix 는 파일 종류에 따라 아래와 같이 사용합니다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 20%;"/>
        <col style="width: 20%;"/>
        <col style="width: 30%;"/>
        <col style="width: 30%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>파일 종류</th>
            <th>디렉토리</th>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Controller</td>
            <td>/controller</td>
            <td>prefix (AppGroup) + 의미있는 명사 + 'Controller'</td>
            <td>
                sysCodeController.java<br />
                (코드관리 Controller)
            </td>
        </tr>
        <tr>
            <td>Service</td>
            <td>/service</td>
            <td>prefix (AppGroup) + 의미있는 명사 + 'Service'</td>
            <td>
                sysCodeService.java<br />
                (코드관리 Service)
            </td>
        </tr>
        <tr>
            <td>Service Implement</td>
            <td>/service</td>
            <td>prefix (AppGroup) + 의미있는 명사 + 'ServiceImpl'</td>
            <td>
                sysCodeServiceImpl.java<br />
                (코드관리 Service implement)
            </td>
        </tr>
        <tr>
            <td>DAO</td>
            <td>/dao</td>
            <td>prefix (AppGroup) + 의미있는 명사 + 'DAO'</td>
            <td>
                sysCodeDAO.java<br />
                (코드관리 DAO)
            </td>
        </tr>
        <tr>
            <td>VO</td>
            <td>/vo</td>
            <td>prefix (AppGroup) + 의미있는 명사 + 'DVO'/ 'PVO'</td>
            <td>
                sysCodePVO.java<br />
                (코드관리 Parameter VO)<br />
                sysCodeDVO.java<br />
                (코드관리 Data VO)
            </td>
        </tr>        
    </tbody>
</table>


## DB Naming Rule

### Table
 - 모든 테이블명은 대문자로 한다.
 - 2개 이상의 단어를 합성할 경우 ‘_’로 구분한다.
 - 하나의 엔티티가 다수의 테이블로 구현되는 경우, 일련번호를 부여하여 명명한다.
 - 테이블 생성 및 변경 시 반드시 ERD로 관리가 되어야 한다.
 - 각 테이블의 외래키가 되거나 같은 성격의 컬럼들의 데이터타입은 반드시 통일시킨다.
 - 테이블의 성격에 맞추어 특성구분은 다음과 같이 구분한다.
   - M(Master,마스터), D(Detail, 상세), C(Code, 코드), H(History, 이력)

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>TB_ + Prefix(AppGroup)_ + 테이블명 + 특성구분</td>
            <td>
                TB_SYS_CODE_C(시스템_코드_마스터)
            </td>
        </tr>
    </tbody>
</table>

### Column
 - 모든 컬럼명은 대문자로 한다.
 - 컬럼명은 용어사전에 수록된 영문 약어를 이용하고, 2개 이상의 단어를 합성할 경우 ‘_’로 구분한다.
 - 하나의 속성이 다수의 컬럼으로 구현되는 경우, 속성의 영문명에 일련번호를 부여하여 명명한다. Ex) 등록일이 여러 번 가능한 경우, 컬럼명은 `REG01_DT`, `REG02_DT` 


### Index
 - Index는 PK Index와 일반 Index를 구분한다.
 - 일반 Index는 일련번호로 구분한다.
 - 모든 Index명은 대문자로 한다

<table>
    <colgroup>
        <col style="width: 20%;"/>
        <col style="width: 40%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>구분</th>
            <th>규칙</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>PK Index</th>
            <th>테이블명_PK</th>
            <th>TB_SYS_CODE_C_PK</th>
        </tr>
        <tr>
            <th>일반 Index</th>
            <th>테이블명_IX+일련번호(2자리)</th>
            <th>TB_SYS_CODE_C_IX01</th>
        </tr>     
    </tbody>
</table>


### Sequence
 - 모든 시퀀스명은 대문자로 한다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>SQ_ + 테이블명</td>
            <td>
                SQ_TB_INF_BBS
            </td>
        </tr>
    </tbody>
</table>

### View
 - 테이블명 규칙을 따르되 테이블명에 VW를 붙여 VIEW 테이블임을 나타냅니다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>VW_ + 테이블명</td>
            <td>
                VW_TB_SYS_ORG
            </td>
        </tr>
    </tbody>
</table>

### Procedure
 - 모든 Procedure명은 대문자로 한다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>SP_ + Prefix(AppGroup)_ + 기능 요약</td>
            <td>
                SP_QAS_KPI_QA_POINT
            </td>
        </tr>
    </tbody>
</table>

### Function
 - 모든 Function명은 대문자로 한다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>FN_+ 기능 요약</td>
            <td>
                FN_SYSDATE
            </td>
        </tr>
    </tbody>
</table>

## 화면 Naming Rule

### Component
 - Component id는 Prefix(type) + Name 로 합니다.
 - Prefix 는 모두 소문자로 하고 합성어는 CamelCase 를 적용합니다.

<table>
    <colgroup>
        <col style="width: 20%;"/>
        <col style="width: 40%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Component 구분</th>
            <th>Prefix</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>Button</th>
            <th>btn</th>
            <th>btnSave</th>
        </tr>
        <tr>
            <th>Div</th>
            <th>div</th>
            <th>divPool</th>
        </tr>
        <tr>
            <th>Form</th>
            <th>f</th>
            <th>fQuery, fDatail</th>
        </tr>
        <tr>
            <th>Iframne</th>
            <th>ifm</th>
            <th>ifmMenu</th>
        </tr>
        <tr>
            <th>Span</th>
            <th>spn</th>
            <th>spnPool</th>
        </tr>
        <tr>
            <th>Tab</th>
            <th>tab</th>
            <th>tabMenu</th>
        </tr>     
    </tbody>
</table>

<br/>  

 - 기본 버튼 Component 명칭은 아래와 같이 정의합니다.
 - 기본 버튼 Component 명칭은 표준용어를 사용하여 정의합니다. 
<table>
    <colgroup>
        <col style="width: 20%;"/>
        <col style="width: 30%;"/>
        <col style="width: 50%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>버튼명</th>
            <th>버튼 Name(Id)</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>조회</td>
            <td>btnSearch</td>
            <td>입력한 조건의 데이터를 조회하는 처리</td>
        </tr>
        <tr>
            <td>초기화</td>
            <td>btnInit</td>
            <td>화면의 데이터를 초기값으로 변경하는 화면 처리</td>
        </tr>
        <tr>
            <td>신규</td>
            <td>btnNew</td>
            <td>신규 데이터를 입력하기 위한 화면 처리</td>
        </tr>
        <tr>
            <td>수정</td>
            <td>btnUpdate</td>
            <td>기입력 데이터를 수정하기 위한 처리</td>
        </tr>
        <tr>
            <td>삭제</td>
            <td>btnDelete</td>
            <td>기입력 데이터를 삭제하기 위한 처리</td>
        </tr>
        <tr>
            <td>저장</td>
            <td>btnSave</td>
            <td>데이터를 신규입력 또는 수정하기 위한 처리</td>
        </tr>
        <tr>
            <td>닫기</td>
            <td>btnClose</td>
            <td>화면을 닫기(Close) 위한 처리</td>
        </tr>
        <tr>
            <td>취소</td>
            <td>btnCancel</td>
            <td>현재 화면 상태를 이전 상태로 복귀하는 처리</td>
        </tr>
        <tr>
            <td>선택</td>
            <td>btnChoice</td>
            <td>데이터 목록에서 다음 동작을 위해 선택</td>
        </tr>
        <tr>
            <td>적용</td>
            <td>btnApply</td>
            <td>선택 데이터를 (상태)변경하기 위한 처리</td>
        </tr>
        <tr>
            <td>추가</td>
            <td>btnAdd</td>
            <td> 데이터를 입력하기 위하여 목록에 Row를 추가</td>
        </tr>
        <tr>
            <td>승인</td>
            <td>btnApproval</td>
            <td>요청 상태의 데이터를 승인하는 처리</td>
        </tr>
        <tr>
            <td>엑셀</td>
            <td>btnExcel</td>
            <td>데이터 목록을 엑셀 파일로 변환하여 다운로드 하는 처리</td>
        </tr>
        <tr>
            <td>업로드</td>
            <td>btnUpload</td>
            <td>파일을 업로드하는 처리</td>
        </tr>
        <tr>
            <td>다운로드</td>
            <td>btnDownload</td>
            <td>파일을 다운로드 하는 처리</td>
        </tr>                
    </tbody>
</table>

## 기타 Naming Rule

### 공통코드
 - 대분류 코드는 Prefix (AppGroup) + 일련번호 로 합니다.
 - 단, UCARE 공통 코드는 명명규칙에서 예외사항이다. USEYN(사용여부) 등
 - 대분류 코드 구분 코드는 ‘##’으로 합니다.
 - 소분류 코드에 대한 규칙은 없으나 되도록이면 코드에 의미를 부여하는 것을 권장합니다.

<table style="width: 90%;">
    <colgroup>
        <col style="width: 60%;"/>
        <col style="width: 40%;"/>
    </colgroup>
    <thead>
        <tr>
            <th>Naming Rule</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Prefix (AppGroup)  + 일련번호</td>
            <td>
                COM001
            </td>
        </tr>
    </tbody>
</table>

### Javascript 함수
 - 되도록 함수의 기능설명을 요약한 이름을 사용합니다.
 - 동작을 나타내는 단어를 앞에 둡니다.
 - 함수명은 소문자를 시작하되 합성어일 경우 두 번째 단어부터 첫 문자를 대문자로 하여 구분합니다.

### Javascript 변수
 - 변수명 앞에 데이터타입을 나타내는 Prefix를 붙이는 것을 권장합니다.
 - “abc”와 같은 의미 없는 이름보다 “sName”과 같은 명확한 이름을 사용합니다.
 - For문 , while()문 내의 첨자로 사용될 변수는 단일문자 i,j,k와 같이 표현하여 프로그램을 읽기 쉽게 합니다.
 - 변수는 소문자로 하되 합성어일 경우 CamelCase 를 적용합니다.
 <br/><br/>
 **Example**
```
    nUserScore, sUserAddr, sOfficeTelNo
``` 
 - 전역 변수일 경우 Prefix로 ‘g’를 붙여줍니다.
 <br/><br/>
 **Example**
```
    gsUserID, gsUserName, ghMenu
``` 
 - 각 소스마다 선언하는 변수 중 같은 성격일 경우 일관성 있게 선언할 것을 권장합니다.
 <br/><br/>
 **Example**
```
    nRowCount, nColCount, sParams, oTrans, nRowIndex, sColumnKey
``` 

### Javat Method
 - 되도록 Method의 기능설명을 요약한 이름을 사용합니다.
 - 동작을 나타내는 단어를 앞에 둡니다.
 - Method명은 소문자를 시작하되 합성어일 경우 CamelCase 를 적용합니다.
 <br/><br/>
 **Example**
```
    getUserName(), setUserName(), saveInfo()
``` 

### Java 변수
 - “abc”와 같은 의미 없는 이름보다 “name”과 같은 명확한 이름을 사용합니다.
 - For문 , while()문 내의 첨자로 사용될 변수는 단일문자 i,j,k와 같이 표현하여 프로그램을 읽기 쉽게 합니다.
 - 변수는 소문자로 하되 합성어일 경우 CamelCase 를 적용합니다.
<br/><br/>
 **Example**  
```
userScore, userAddr, officeTelNo
```
