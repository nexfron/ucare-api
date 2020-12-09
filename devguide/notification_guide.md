# 윈도우 Notification 개발 가이드

UCARE 의 Notification 개발을 위한 내용을 설명합니다.

### WebSocket 참조 URL

  - [Notification - MDN](https://developer.mozilla.org/ko/docs/Web/API/notification)
  - [알림 API 사용하기](https://developer.mozilla.org/ko/docs/WebAPI/Using_Web_Notifications)

<br />

### 알림 권한 요청

```javascript
    Notification.requestPermission()
```


### 알림 표시

```javascript
    // Example
    var notification = new Notification('신규 공지사항', {
    icon: '/static/images/site/willvi/common/win_noti.png',
    body: notiObj.title,
    });
```
