# CTI 개발 가이드

UCARE 의 CTI 개발을 위한 내용을 설명합니다.

### CTI 참조 URL

  - [ECMS-269](https://www.ecma-international.org/publications/standards/Ecma-269.htm)
  - [CSTA Overview](https://www.slideshare.net/Shelly38/cstaoverviewppt)

<br />

### CTI 서비스 호출 처리
  - 동작 처리 순서 (걸기)
    - 버튼 클릭 - btnCtiMakecall
    - btnCtiXXXXXClick (ucareCTIFunction.js) (btnCtiMakecallClick)
      - CTI 버튼 동작 전 Valid 체크
      - ucareCti.action.서비스명 (ucareCTIAPIOCX.js) - ucareCti.action.makeCall
      - ctiActionPostHandler 호출 에 결과 값 전달
    - ctiApi서비스명 (ucareCTIAPIOCX.js)  - ctiApiMakeCall 
      - CTI 서버 서비스 호출
      - CTI 서비스 호출결과 반환 (0: 정상)
    - ctiActionPostHandler (ucareCTIFunction.js)
      - 버튼 및 메시지 처리
      - CTI 서버 호출 오류시, 후처리
    
  - 버튼 Control 정의 : CTIDef.stateObj
  - Call Service 정의 : CTIDef.service
  - Call Event 정의 : CTIDef.event - CTIDef.cube.eventCode 에서 해당 제품 Event 코드 매핑
<br />
<br />

### CTI 이벤트 처리
  - 이벤트 처리 순서 (전화받기)
    - ctiEventHandler(ucareCTIFunction.js) 호출
      - 이벤트명 반환(CTIDef.event 에 정의된 이벤트 명) - CTIDef.cube.eventCode
    - ucareCti.event.이벤트명 (ucareCTIAPIOCX.js) (btnCtiMakecallClick)
      - UCARE 표준 이벤트 데이터 반환
      - ctiEventPostHandler 호출
    - ctiEventPostHandler (ucareCTIFunction.js)
      - 버튼 및 메시지 처리
      - 콜관련 데이터 세팅 및 화면 처리

<br />
<br />

### CTI 샘플
```javascript
# 준비
ucareCti.cti.server = {
    'isConnect' : true, // CTI 서버 접속 여부
    'isLogin'   : true, // CTI 서버 로그인 여부
    'isMonitor' : true  // CTI 서버 MonitorStart 여부    
};

ctiActionPostHandler('ctiLogin',0)

# 전화걸기
var _outEstablishedEvtObj = JSON.parse('{"callId":"8146","ani":"01050981111","eventCause":"0","callType":"OB","customData":"","isInCall":false,"isInternalCall":false,"ivrData":{"vdn":"","ani":"","etcData":""},"userData":{"agentDn":"","userId":"","ani":"","cstmrNo":"","csType":""}}')
ctiEventPostHandler(CTIDef.event.established, _makeCallEvtObj)


# 대기
ctiActionPostHandler('ctiReady',0)

# 전화인입
var _inDeliveredEvtObj = JSON.parse('{"callId":"7970","ani":"01050981111","eventCause":"22","callType":"IB","localConnectState":2,"customData":"","isInCall":true,"isInternalCall":false,"ivrData":{"vdn":"","ani":"","etcData":""},"userData":{"agentDn":"","userId":"","ani":"","cstmrNo":"","csType":""}}')
ctiEventPostHandler(CTIDef.event.delivered, _inDeliveredEvtObj)

# 전화받기
closeAnswerPopup();
var _inEstablishedEvtObj = JSON.parse('{"callId":"8146","ani":"01050981111","eventCause":"0","callType":"OB","customData":"","isInCall":false,"isInternalCall":false,"ivrData":{"vdn":"","ani":"","etcData":""},"userData":{"agentDn":"","userId":"","ani":"","cstmrNo":"","csType":""}}')
ctiEventPostHandler(CTIDef.event.established, _inEstablishedEvtObj)

```