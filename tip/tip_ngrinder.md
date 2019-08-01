# nGrinder 성능 테스트

nGrinder Open Source를 이용한 성능 테스트입니다.

## 테스트 환경
### nGrinder Download
 [nGrinder Download Link](https://naver.github.io/ngrinder/)<br/>

<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_link.png" width="100%" height="100%"><br/>
- 링크 클릭<br>
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_download_open.png" width="100%" height="100%"><br/>
- ngrinder-controller-3.4.3.war Download<br/>
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_download.png" width="100%" height="100%"><br/>

### nGrinder Controller
    - 부하테스트를 위한 웹 인터페이스
    - 테스트 프로세스를 체계화
    - 테스트 결과 수집

 #### nGrinder Controller 실행
cmd창에서 다운받은 war파일 위치로 이동하여 명령어 실행
```html
[ngrinder war pah] > java -XX:MaxPermSize=200m -jar [ngrinder war fine name].war --port [임의 포드 선정]
```

***Example***
<img src="http://www.nexfron.com/ucare_images/ngrinder/controller_command.png" width="100%" height="100%"><br/>
<img src="http://www.nexfron.com/ucare_images/ngrinder/controller_action.png" width="100%" height="100%">

#### nGrinder 접속
    - User ID  : admin
    - Password : admin
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_login.png" width="100%" height="100%">

### Agent
    - Controller 명령을 받아 실행
    - agent 모드가 실행 되면 Target이 된 머신에 프로세스와 스레드를 실행시켜 부하 발생
    - monitor 모드가 실행 되면 대상 시스템의 CPU와 Memory 모니터링

#### Agent Download
nGrinder 접속 후 오른쪽 상단의 admin > Download Agent 선택<br/>
<img src="http://www.nexfron.com/ucare_images/ngrinder/agent_download.png" width="100%" height="100%">

#### Agent 실행
다운 받은 ngrinder agent tar파일 압축 풀기.<br/>
ngrinder-agent 폴더 내의 run_agent.bat 실행.<br/>
<img src="http://www.nexfron.com/ucare_images/ngrinder/agent_action.png" width="100%" height="100%">

#### Agent 접속 확인
nGrinder 오늘쪽 상단의 admin > Agent Management 선택<br/>
<img src="http://www.nexfron.com/ucare_images/ngrinder/agent_management.png" width="100%" height="100%">

## Script 작성
테스트 실행을 할 수 있는 Script<br/>
Script는 Groovy, Jython, Groovy Maven Project 총 3가지로 작성 가능하나 Groovy로 작성<br/>
 - Annotation
 <table>
    <colgroup>
        <col style="width="10%">
        <col style="width="40%">
        <col style="width="10%">
        <col style="width="40%">
    </colgroup>
    <thead>
        <tr>
            <th></th>
            <th>설명</th>
            <th>적용</th>
            <th>사용</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                @BeforeProcess
            </td>
            <td>
                프로세스가 생성될때 실행해야 하는 동작 정의
            </td>
            <td>
                static Method
            </td>
            <td>
                - 프로세스 내 쓰레드가 공유 할 리소스 파일 로드<br/>
                - GTest를 사용한 테스트 항목 Instrumentation
            </td>
        </tr>
        <tr>
            <td>
                @AfterProcess
            </td>
            <td>
                프로세스가 종료하기 직전에 실행해야 해야 하는 동작 정의
            </td>
            <td>
                static Method
            </td>
            <td>
                - 리소스 파일 닫기
            </td>
        </tr>
        <tr>
            <td>
                @BeforeThread
            </td>
            <td>
                각 Thread가 실행되기 전에 실행해야 하는 동작 정의
            </td>
            <td>
                Member Method
            </td>
            <td>
                - 테스트 대상 시스템 로그인<br/>
                - Thread별 Cookie 핸들러 설정
            </td>
        </tr>
        <tr>
            <td>
                @AfterThread
            </td>
            <td>
                각 Thread가 종료하기 직전에 실행해야 하는 동작 정의
            </td>
            <td>
                Member Method
            </td>
            <td>
                - 테스트 대상 시스템 로그아웃
            </td>
        </tr>
        <tr>
            <td>
                @Before
            </td>
            <td>
                모든 @Test 메소드가 실행되기 전에 실행해야 하는 동작 정의
            </td>
            <td>
                static Method
            </td>
            <td>
                - 여러 @Test 메소드가 공유하는 로직<br/>
                - 설정 검증
            </td>
        </tr>
        <tr>
            <td>
                @After
            </td>
            <td>
                모든 @Test 메소드가 종료된 이후 실행해야 하는 동작 정의
            </td>
            <td>
                static Method
            </td>
            <td>
            </td>
        </tr>
        <tr>
            <td>
                @Test
            </td>
            <td>
                테스트 동작 정의
            </td>
            <td>
                static Method
            </td>
            <td>
                - Test Body
            </td>
        </tr>
    </tbody>
 </table>

 - Login 처리

