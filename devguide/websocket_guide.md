# WebSocket 개발 가이드

UCARE 의 WebSocket 개발을 위한 내용을 설명합니다.

### WebSocket 참조 URL

  - [웹소켓 설정](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:rte2:ptl:async_request)
  - [전자정부프레임워크 웹소켓](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:rte3.5:ptl:websocket)
  - [Spring 4를 이용한 WebSocket 구현하기](https://oofbird.tistory.com/9)

<br />

### 웹소켓 환경 설정 (비동기 요청처리를 위한 환경)
  - Servlet 3.0 이상
  ```xml
    # web.xml - ucare_app_v3
    <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>/WEB-INF/config/springmvc/dispatcher-servlet.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
        <async-supported>true</async-supported> <!-- 웹소켓을 위한 설정(비동기지원) -->
    </servlet>
  ```

  - Spring MVC 3.2 이상 (eGov 3.0에 포함)
  ```xml
    # web.xml - ucare_app_v3
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://java.sun.com/xml/ns/javaee" xmlns:web="http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
    xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
    id="WebApp_ID" version="3.0"> 
  ```

  - Web.xml 설정 변경
  ```xml
    # web.xml - ucare_app_v3
    <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>/WEB-INF/config/springmvc/dispatcher-servlet.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
        <async-supported>true</async-supported> <!-- 웹소켓을 위한 설정(비동기지원) -->
    </servlet>  
  ```


### WebSocket EndPoint

```java
    // UcareWebSocketHandler.java

    public class UcareWebSocketHandler extends TextWebSocketHandler {

        private static Map<String, WebSocketSession> usersMap = new HashMap<String, WebSocketSession>();

        // Disconnect - 웹소켓 접속이 닫힌 후 호출
        @Override
        public void afterConnectionClosed(WebSocketSession session, CloseStatus status) {
        }

        // Connect - 웹소켓이 열리고 사용할 준비가 되면 호출
        @Override
        public void afterConnectionEstablished(WebSocketSession session) {
        }

        // Receive Message - 웹소켓 메시지가 도착하면 호출
        @Override
        public void handleTextMessage(WebSocketSession session) {
        }

    // 클라이언트 웹소켓 메시지 발송
    public void sendMessageToUsers(String message, List<String> receiveUserIds) {
            
            WebSocketSession webSocketSession;
            
            for (String userId : receiveUserIds) {
                webSocketSession = UcareWebSocketHandler.usersMap.get(userId);

                if (logger.isDebugEnabled()) {
                    logger.debug("### [UcareWebSocketHandler] sendMessageToUsers userId [{}], webSocketSession [{}]", userId, webSocketSession);
                }
                
                if (webSocketSession != null && webSocketSession.isOpen()) {
                    try {
                        webSocketSession.sendMessage(new TextMessage(message));
                    } catch (Exception e) {
                        logger.error("\n[handleException] sendMessageToUsers : \n{}\n", e.getMessage());
                    }

                }
            }
            
        }
    }
```


```java
    // InfBordServiceImpl.java

    // [2020-11-13] 수정: 공지사항 대상자 알림 기능 추가
    Map<String, Object> messageMap =  new HashMap<String, Object>();
    messageMap.put("type", COMConstant.MESSAGE_TYPE.BOARD.getCode());
    
    messageMap.put("receiveUserId", UserSessionInfo.getUserId());
    messageMap.put("receiver", UserSessionInfo.getUserNm());
    messageMap.put("receiveDate", DateUtil.getFormatDateTime("yyyyMMddHHmmss"));
    messageMap.put("title", infBordDVO.getBbsSj());
    messageMap.put("bbsSeq", infBordDVO.getBbsSeq()); // 게시판 SEQ
    messageMap.put("bbsId", infBordDVO.getBbsId());   // 게시판 ID 
    
    String sendMessage = "";
    
    if (StringUtils.isNoneEmpty(infBordDVO.getBbsCnText())) {
        if (infBordDVO.getBbsCnText().length() < 100) {
            sendMessage = infBordDVO.getBbsCnText().substring(0);
        } else {
            sendMessage = infBordDVO.getBbsCnText().substring(0, 100);
        }
    }
    
    messageMap.put("message", sendMessage);

    ucareWebSocketHandler.sendMessageToUsers(JsonUtil.convertJsonFromMap(messageMap), redngTrgetList);
```

### WebSocket 핸들러 등록
```xml
    <!-- dispatcher-servlet.xml -->

    <!-- WebSocket -->
    <websocket:handlers>
        <websocket:mapping path="/socket" handler="websocketHandler"/>
        <websocket:handshake-interceptors>
            <bean class="com.nexfron.core.websocket.UcareHandshakeInterceptor" />
        </websocket:handshake-interceptors>
    </websocket:handlers>

    <bean id="websocketHandler" class="com.nexfron.core.websocket.UcareWebSocketHandler" />
```

### WebSocket Client
```javascript
    // main.common.js

    var connectWs = function() {
        // TODO: 웹소켓 접속 Return

        var wsUrl = "ws://" + location.host + "/socket";
        // _umg.socket.client = new WebSocket("ws://127.0.0.1:8080/socket");
        _umg.socket.client = new WebSocket(wsUrl);

        _umg.socket.client.onopen = function (evt) {
            console.log("[connectWs] onopen ", evt);
            if (_umg.socket.client) {
                console.log("[connectWs] onopen send... ");
                _umg.socket.client.send("TEST OPEN");
            }
        }

        _umg.socket.client.onclose = function (evt) {
            console.log("[connectWs] onclose ", evt);
        }
        
        _umg.socket.client.onerror = function (err) {
            console.log("[connectWs] onerror ", err);
        }

        _umg.socket.client.onmessage = function (evt) {
            console.log("[connectWs] onmessage ", evt);

            _umg.message.showMessage(evt.data);
        }    
    }
```