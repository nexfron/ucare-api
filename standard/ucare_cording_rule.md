# 코딩 규칙

java, javascript 등 코딩 규칙에 대한 설명입니다.


## 문서 주석

 - JSP, Javascript 파일 상단에 문서에 대한 주석을 표시합니다.


### JSP
 - JSP 문서 주석은 다음과 같은 형식으로 추가합니다.

```jsp
<%
 /**
 * PROJ : 프로젝트명
 * NAME : 소스파일명
 * DESC : 소스 설명
 * Author : 작성자 
 * VER  : 1.0
 * Copyright 2009 Nexfron All rights reserved
 * ===============================================================================
 * 								변		경		사		항
 * ===============================================================================
 * VERSION		DATE		AUTHOR		DESCRIPTION
 * ===============================================================================
 * 1.0		    일자		작성자		 변경사항
 */
%>
``` 

***Example***
```jsp
<%
/**
 * PROJ : Nexfron APP
 * NAME : smpSampleMng.jsp
 * DESC : 샘플관리
 * Author : 연구개발팀 
 * VER  : 1.0
 * Copyright 2009 Nexfron All rights reserved
 * ===============================================================================
 * 								변		경		사		항
 * ===============================================================================
 * VERSION		DATE		AUTHOR		DESCRIPTION
 * ===============================================================================
 * 1.0		2019.01.02		연구개발팀		신규작성
 */
%>
```

### Javascript
 - Javascript 문서 주석은 다음과 같은 형식으로 추가합니다.

```js
 /**
 * PROJ : 프로젝트명
 * NAME : 소스파일명
 * DESC : 소스 설명
 * Author : 작성자 
 * VER  : 1.0
 * Copyright 2009 Nexfron All rights reserved
 * ===============================================================================
 * 								변		경		사		항
 * ===============================================================================
 * VERSION		DATE		AUTHOR		DESCRIPTION
 * ===============================================================================
 * 1.0		    일자		작성자		변경사항
 */
``` 

***Example***
```js
/**
 * PROJ : Nexfron APP
 * NAME : smpSampleMng.js
 * DESC : 샘플 관리
 * Author : 연구개발팀 
 * VER  : 1.0
 * Copyright 2009 Nexfron All rights reserved
 * ===============================================================================
 * 								변		경		사		항
 * ===============================================================================
 * VERSION		DATE		AUTHOR		DESCRIPTION
 * ===============================================================================
 * 1.0		2019.01.02		연구개발팀		신규작성
 */
```

### Java
 - Java 문서 주석은 다음과 같은 형식으로 추가합니다.

```java
/**
 * @Project : 프로젝트명
 * @Class Name : 소스파일명
 * @Description : 소스 설명
 * @Modification Information
 * @
 * @  수정일      수정자              수정내용
 * @ ---------   ---------   -------------------------------
 * @ 일자         작성자       변경사항
 *
 * @author 작성자
 * @since 최초 생성일자
 * @version 1.0
 * @see
 *
 *  Copyright (C) by Nexfron All right reserved.
 */
``` 

***Example***
```java
/**
 * @Project : Nexfron APP
 * @Class Name : QasCloseController.java
 * @Description : QA - QA마감관리
 * @Modification Information
 * @
 * @  수정일      수정자              수정내용
 * @ ---------   ---------   -------------------------------
 * @ 2019.06.01   넥스프론        최초생성
 *
 * @author 넥스프론
 * @since 2009. 03.16
 * @version 1.0
 * @see
 *
 *  Copyright (C) by Nexfron All right reserved.
 */
```


## 소스 주석

### JSP
 - JSP 소스 주석은 <%-- --%> 을 사용합니다.
> &lt;!-- --&gt; 주석은 컴파일이 되어 소스보기를 하면 주석 내용이 보입니다.<br />
> &lt;%-- --%&gt; 주석은 컴파일이 되지 않아 소스보기를 하면 주석 내용이 보이지 않습니다.

### Javascript
 - 함수(Function) 에는 기능을 설명하는 주석을 추가합니다.

```js
/**
 * 함수 설명
 * @param {타입} argument1 : argument1 설명
 * @param {타입} argument2 : argument2 설명
 */
```

***Example***
```js
/**
 * Grid 클릭 시 이벤트
 * @param {string} id : Grid ID
 * @param {object} oGrid : Grid 객체
 * @param {int} nRow : 선택 Row
 * @param {int} nCol : 선택 Col
 */
 ```

 - 일반적인 코드 주석은 라인(Line) 주석(`//`) 을 권장합니다.
 - 블럭(Block) 주석(`/* */`) 은 로직 변경 등 꼭 필요한 경우 사용하며, 로직 변경 등이 있는 경우 상세 이유를 기재합니다.

### Java
 - Method 에는 기능을 설명하는 주석을 추가합니다.

```java
/**
 * Method 기능 설명
 *
 * @param Parameter 설명
 * @return Return 설명
 */
```

***Example***
```java
/**
 * 지정된 index 에 위치하는 문자 반환
 *
 * @param index 문자 index 값
 * @return 지정된 index 의 문자
 */
```


