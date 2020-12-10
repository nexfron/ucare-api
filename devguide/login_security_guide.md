# 로그인 정책 설정 가이드

UCARE 의 로그인 정책 관련 설정을 하기 위한 시스템 내용을 설명합니다.

#### 정책(기능) 설정

`global.properties` 에서 다음과 같은 설정이 필요

```properties
  # global.properties

  # 비밀번호 정책 출처(FILE: global_properties 관리, DB: Database 관리)
  CONFIG.SYS.PWD.POLICY.SOURCE = FILE

  # 휴먼 계정 잠금 기능 사용 여부/일자
  CONFIG.SYS.ID.LOCK.TERM.LOGIN=false
  CONFIG.SYS.ID.LOCK.TERM.LOGIN.DAYS=30

  # 비밀 번호 변경 갱신 잠금 기능 사용 여부/일자/알림일자
  CONFIG.SYS.ID.LOCK.TERM.PWD.RENEWAL=true
  CONFIG.SYS.ID.LOCK.TERM.PWD.RENEWAL.DAYS=10
  CONFIG.SYS.ID.LOCK.TERM.PWD.RENEWAL.ALERT.DAYS=5

  # 비밀번호 입력 오류 잠금 기능 사용 여부/횟수
  CONFIG.SYS.ID.LOCK.PWD.WRG=true
  CONFIG.SYS.ID.LOCK.PWD.WRG.CNT=5

  # 직전 비밀번호 체크 여부(true: 직전 비밀번호 체크, false: 직전 비밀번호 체크 하지 않음)
  CONFIG.SYS.ID.CHK.PWD.REUSING=true

  # 사용자 접속 IP 체크 여부
  CONFIG.SYS.ID.CHK.PERMISSION.IP=false

  # 직전 비밀번호 체크여부
  CONFIG.SYS.CHK.PWD.REUSING=true
```
<br>



### 로그인 체크

`checkLogin` 메소드에서 로그인 정책에 대한 check 를 합니다.  
로그인 체크 결과는 LoginConstant 클래스의 LOGIN_PROC_RESULTCODE 에 정의

```java
  // LoginController.java
  public void checkLogin...() {

    // 1.사용자 정보 체크

    // 1-1. UcareBaseLoginController.findUserDetail() 호출
    LoginDVO loginDVO = this.findUserDetail()
      - 사용자 조회
      - 사용자 라이센스 검증
    // 1-2. 다음의 경우 로그인 페이지로 이동
      - 사용자 정보 없음
      - 사용자 라이센스 유효하지 않음 

    // 2.로그인 보안정책 체크
    // 2-1. Loginservice.checkAuthentication() 호출
    LoginConstant.LOGIN_PROC_RESULTCODE loginProcResultcode = loginService.checkAuthentication(loginPVO, loginDVO);

    // checkAuthentication() 는 UcareBaseLoginServiceImpl.processLogin
    LoginConstant.LOGIN_PROC_RESULTCODE checkResult = this.processLogin(loginPVO, loginDVO);
      - 비밀번호 정책 체크 
        - 휴면잠금상태 체크
        - 비밀번호 오류 잠금상태 체크
        - 비밀번호 갱신주기 잠금상태 체크
        - 허가되지 않은 IP 접속 체크
        - 비밀번호 오류 체크
        - 사용여부 체크

      - 로그인 정보 DB 업데이트
        - 비밀번호 오류 횟수
        - 로그인 여부 업데이트
      - 로그인 이력 입력

    // 2-2. 다음의 경우 로그인 페이지로 이동
      - 비밀번호 정책 관련 오류

    // 2-3. 로그인 성공 시, Session 생성
    this.createUserSession(request, loginPVO, loginDVO, new SessionVO(), loginService);

    // 2-4. main.do 화면으로 Redirect
    response.sendRedirect(request.getContextPath() + "/main/main.do");

  }
```

### 비밀번호 갱신주기 알람 처리
```java
  // MainController.java

  @RequestMapping(value = "main")
  public String main() {
    if (isIdLockTermPwdRenewal) {
      model.addAttribute("pwdRenewalDays"	    , pwdRenewalDays);       // 비밀번호 갱신 일자
      model.addAttribute("pwdRenewalAlertDays"  , pwdRenewalAlertDays);  // 비밀번호 갱신 알림일자
    }
  }
```

```javascript
  // uclib_default.js
  UCG.PASSWORD = {
        'OPTIONS'    : {
          'isIdCheck'	: false,	// 사용자 ID 비밀번호 포함 제외 체크 여부
          'lengthMin'	: 8,		// 비밀번호 최소 자리수 설정
          'isNumber'	: true,		// 숫자 포함여부
          'isLower'		: false,	// 소문자 포함여부
          'isUpper'		: false,	// 대문자 포함여부
          'isAlphabet'	: true,		// 영문자(대소문자) 포함여부
          'isSpecial'	: true		// 특수문자 포함여부
        },
        'PWD_RENEWAL_DAYS'       : 30,  // 비밀번호 갱신 주기(일수) - 비밀번호는 30 일이 지나기 전에 변경해야 함 
        'PWD_RENEWAL_ALERT_DAYS' : 7,   // 비밀번호 갱신 알람 기간(일수) -> 갱신일자가 7일 이내의 경우, 알람
        'PWD_DIFF_DAY'           : 0    // 비밀번호 변경 경과 일수 -> 현재일자 - 비밀번호 변경일자      
  }

  // mainTop.jsp

  // 비밀번호 정책 정보
  UCG.PASSWORD.PWD_RENEWAL_DAYS       = "<c:out value='${pwdRenewalDays}'/>";       // 비밀번호 갱신 주기(일수)
  UCG.PASSWORD.PWD_RENEWAL_ALERT_DAYS = "<c:out value='${pwdRenewalAlertDays}'/>";  // 비밀번호 갱신 알람 기간(일수)
  UCG.PASSWORD.PWD_DIFF_DAY           = "<c:out value='${userInfo.pwdDiffDay}'/>";  // 비밀번호 변경 경과 일수


  // main.common.js

  function checkPwdRenewalRemainPopup() {

      // 비밀 번호 변경 갱신 잠금 기능 미사용 시, 갱신 잠금 일자 값이 없음
      if (_UL.util.isEmpty(UCG.PASSWORD.PWD_RENEWAL_DAYS)) {
          return;
      }

      // 비밀번호 변경 만료일까지 남을 일수
      // 비밀번호 변경 주기 일수 - 비밀번호 변경부터 경과일수
      var pwdLeftDays  = UCG.PASSWORD.PWD_RENEWAL_DAYS - UCG.PASSWORD.PWD_DIFF_DAY;

    if (UCG.PASSWORD.PWD_RENEWAL_DAYS - UCG.PASSWORD.PWD_DIFF_DAY <= UCG.PASSWORD.PWD_RENEWAL_ALERT_DAYS) {
      var param = {
              'pwdRenewalDays' : UCG.PASSWORD.PWD_RENEWAL_DAYS,
              'pwdLeftDays'    : pwdLeftDays
          };

          console.log(param);

          var popOption = {
              'type'  : 'window',
              'id'    : "notiPwdRemainingDaysP",
              'title' : "비밀번호 변경알림",
              'url'   : "/main/notiPwdRemainingDaysP.do",
              'param' : param,
              'width' : 500,
              'height' : 200,
              'winOption' : 'scrollbars=no, status=no'
          };

          _UL.popup.open(popOption);
    }
  }
```
