# JSP 작성

JSP 파일 작성 표준에 대한 설명입니다.

## 지시자
 - 모든 jsp 페이지는 상단에 아래와 같은 지시자를 선언하여 사용합니다.

```html
<%@ page language="java" contentType="text/html; charset=utf-8" pageEncoding="utf-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
<%@ taglib prefix="ui" uri="http://egovframework.gov/ctl/ui"%>
<%@ taglib prefix="spring" uri="http://www.springframework.org/tags"%>
<%@ page import="com.nexfron.core.util.*" %>
```

## 공통 include
 - ucare 를 사용하기 위해 필요한 import, script, taglib 등을 포함하는 공통 include 파일을 모든 jsp 페이지에 추가하여 사용합니다.

### 일반화면
일반 화면은 `header.jsp` 을 상단에 include 합니다.

```html
<jsp:include page="${incPath}/header.jsp"/>
```

**Example**

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>사용자 관리</title>
    <jsp:include page="${incPath}/header.jsp"/>
    <script type="text/javascript" src="<c:out value='${jsPath}'/>/system/sysUser.js" charset="utf-8"></script>
</head>
<body class="mainbody">
...
...
</body>
</html>
```

### 팝업화면
팝업 화면은 상단에 `popup_header.jsp` 파일을 include 하고, 하단에 `popup_footer.jsp` 파일을 include 합니다.

```html
<!-- 상단 -->
<jsp:include page="${incPath}/popup_header.jsp"/>

<!-- 하단 -->
<jsp:include page="${incPath}/popup_footer.jsp"/>
```

**Example**

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	<title>사용자 조회</title>
	<jsp:include page="${incPath}/popup_header.jsp"/>
	<script type="text/javascript" src="<c:out value='${jsPath}'/>/common/comUser.js" charset="utf-8"></script>
</head>
<body>
	...
    ...
<jsp:include page="${incPath}/popup_footer.jsp"/>
</body>
</html>
```
