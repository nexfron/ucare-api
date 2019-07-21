# 공통 include 파일

UCARE 공통 include 파일에 대한 설명입니다.

## include_doctype.jsp
 - doctype 을 포함하는 파일
 - 모든 jsp 페이지에 추가하여 사용합니다.

```html
<%@ include file="../include/include_doctype.jsp"%>
```

## include.jsp
 - ucare 를 사용하기 위해 필요한 import, script, taglib 등을 포함하는 파일
 - 모든 jsp 페이지에 추가하여 사용합니다.

```html
<%@ include file="../include/include.jsp"%>
```

## include_pop_top.jsp
 - 팝업화면 상단 공통 파일

```html
<%@ include file="../include/include_pop_top.jsp" %>
```

## include_pop_bottom.jsp
 - 팝업화면 하단 공통 파일

```html
<%@ include file="../include/include_pop_bottom.jsp" %>
```
