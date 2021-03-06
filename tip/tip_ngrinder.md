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
[ngrinder war pah] > java -XX:MaxPermSize=200m -jar [ngrinder war fine name].war --port [임의 포트 선정]
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

 - Login 처리<br/>
***Example***
```java
class TestRunner{
    public static HTTPRequest request
    public static Cookie[] cookies = []

    @BeforeProcess
    public static void beforeProcess() {
        request = new HTTPRequest();
    }

    @BeforeThread
    public void beforeThread() {
        def threadContext = HTTPPluginControl.getThreadHTTPClientContext();

        cookies = CookieModule.listAllCookies(threadContext);

        cookies.each{
            CookieModule.removeCookie(it, threadContext)
        }

        // 로그인
        NVPair[] params = [new VNPair("user_id", "1"), new NVPair("pass_word", "./..")];
        HTTPResponse result = request.POST("http://www.nexfron.com/login.do", params);

        cookies = CookieModule.listAllCookies(threadContext)
    }

    @Before
    public void before() {
        Object threadContext = HTTPPluginControl.getThreadHTTPClientContext()

        cookies.each {
            CookieModule.addCookie(it, threadContext)

            grinder.logger.info("{}", it)
        }
    }
}
```

- Test Script 작성<br/>
***Example 상담이력관리 조회***
```java
class TestRunner{
    // Test 선언
    public static GTest test01;
    
    public static HTTPRequest request
    public static Cookie[] cookies = []

    // Parameter 선언
    public static NVPair[] params = [];

    @BeforeProcess
    public static void beforeProcess() {
        HTTPPluginControl.getConectionDefaults().timeout = 6000

        // Test 초기화
        test01 = new GTest(1, "상담이력관리");

        request = new HTTPRequest()
    }

    @BeforeThread
    public void beforeThread() {
        def threadContext = HTTPPluginControl.getThreadHTTPClientContext();

        cookies = CookieModule.listAllCookies(threadContext);

        cookies.each{
            CookieModule.removeCookie(it, threadContext)
        }

        // 로그인
        NVPair[] params = [new VNPair("user_id", "1"), new NVPair("pass_word", "./..")];
        HTTPResponse result = request.POST("http://www.nexfron.com/login.do", params);

        cookies = CookieModule.listAllCookies(threadContext)

        // Test 매핑
        test01.record(this, "conslTest");

        grinder.statistics.delayReports=true;
    }
    
    @Before
    public void before() {
        Object threadContext = HTTPPluginControl.getThreadHTTPClientContext()

        cookies.each {
            CookieModule.addCookie(it, threadContext)

            grinder.logger.info("{}", it)
        }
    }

    @Test
    public void conslTest() {
        // Parameter
        NVPair[] params = [
            new VNPair("fQuery_strt_dt", "20190729"),
            new VNPair("fQuery_end_dt", "20190802"),
        ];

        HTTPResponse result = request.POST("http://www.nexfron.com:8000/bizcons/selectConslList.do", params)

		if (result.statusCode == 301 || result.statusCode == 302) {
			grinder.logger.warn("Warning. The response may not be correct. The response code was {}.", result.statusCode); 
		} else {
			assertThat(result.statusCode, is(200));
		}
    }
}
```
## 성능 테스트
- 테스트 생성 및 설정
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_test_conf.png" width="100%" height="100%">
    - Agent     : 사용 할 Agent 수<br/>
    - Vuser per Agent : Agent당 가상 User(Thread를 많이 지정 할수록 좋음)<br/>
    - Script    : Test Script<br/>
    - Duration  : 테스트 시간<br/>
    - Run Count : Thread당 실행 수<br/>
    - Rame-Up   : 부하를 점차 늘리면서 진행<br/>

## 테스트 결과
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_test_report.png" width="100%" height="100%"><br/>
- 상세 보고서

    - 결과
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_test_report_d.png" width="100%" height="100%"><br/>
    - TPS (Transaction Per Second / 초당 트랜젝션 처리량)
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_test_tps.png" width="100%" height="100%"><br/>
    - MTT (Mean Test Time) 평균 응답 시간(ms)
<img src="http://www.nexfron.com/ucare_images/ngrinder/ngrinder_test_mtt.png" width="100%" height="100%"><br/>

## 적용 사례 및 참고
### 정보제공 : 채준범
    - 외부 Agent에서 Controller 접속 할 경우 Agent 설정 변경
        - 설정 파일명 : __agent.conf (ngrinder agent tar파일 압축해제한 폴더 내에 존재)
        - 적용이 안된 경우 : C:\Users\{pc name}\.ngrinder_agent\agent.conf 파일을 수정하거나, 해당 폴더를 전제 삭제후 agent 재실행
    - Agent와 Controller 연결 Port(단방향)
        - Agent : Any ==> Controller : 16001
        - Agent : Any ==> Controller : 12000 ~ 12000+(the number of concorrent tests allowed)
        참조 : http://ngrinder.642.n7.nabble.com/nGrinder-td1046.html
    - Agent가 부하를 주지 못할 경우
        - Agent PC를 늘리거나 User 세팅 수를 줄여 테스트 진행.
    - WAS Server TIME_WAIT SOCKET
        - 서버 파라미터 변경으로 TIME_WAIT SOCKET 설정을 변경하여 TCP 성능을 향상시킬 수 있음.
        참조(서버 파라미터 변경 방법) : https://www.slideshare.net/ienvyou/v13-122857784 (31page)
        참조(TIME_WAIT SOCKT)       : https://meetup.toast.com/posts/55