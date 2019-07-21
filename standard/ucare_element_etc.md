# 기타 Element 그리기
기타 Element 생성 및 속성을 설명입니다.  

---
기타 Element 는 HTML Element 와 **dataset** 요소를 통하여 UCARE 에 맞게 Customize 합니다.

## 버튼 (Button)

버튼 는 HTML 의 기본적인 [button](https://developer.mozilla.org/ko/docs/Web/HTML/Element/button) 요소로 작성합니다.<br/>

```html
<button type="button" class="button blue">텍스트</button>
```
  - button 의 class 는 `button blue` 으로 정의합니다.

***Example***

```html
<button type="button" class="button blue" id="btnTest" name="btnTest" title="테스트" onclick="test()">테스트</button>
```
<br />


## 탭 (Tab)

탭(가로) 은 HTML 의 `ul` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다.<br/><br/> 

```html
<ul id="탭ID" data-cmp-type="TAB" data-title="탭 표시 목록"></ul>
```
  - **data-cmp-type** : component 타입. `TAB` 로 정의합니다.
  - **data-title** : 탭으로 표현할 텍스트 목록. `comma(,)` 로 구분.

> - 탭을 클릭하면 `탭ID_OnTabClick` Function 을 호출하며, 탭 순서(index)를 argument 로 전달합니다.
> - `탭ID_OnTabClick` Function 의 처음에 `_UL.html.changeTab(탭ID, 탭index)` 공통 Function 을 호출해야 합니다.

***Example***

```html
<ul id="tabObj" data-cmp-type="TAB" data-title="개요,관련지식,담당자,변경이력"></ul>
```

위 예제에서 탭ID 가 `tabObj` 경우, `tabObj_OnTabClick` Function 을 호출합니다.<br />
Function 의 처음에 `_UL.html.changeTab('tabObj', index)` 공통함수를 호출합니다.

```js
function tabObj_OnTabClick(index)
{
	_UL.html.changeTab('tabObj', index);

	switch (index)
	{
	    case 0 : // 개요
	    	document.all["ifmKnw"].src= "/knowledge/kmsKnwldgSumry.do?"+sParam;
	        break;
	
	    case 1 : // 관련카테고리
	    	document.all["ifmKnw"].src= "/knowledge/kmsKnwldgRelateCntnts.do?"+sParam;
	        break;
	       
	    case 2 : // 담당자
	    	document.all["ifmKnw"].src= "/knowledge/kmsKnwldgCharger.do?"+sParam;
	        break;
			
		  case 3 : // 변경이력
	    	document.all["ifmKnw"].src= "/knowledge/kmsKnwldgChgHst.do?"+sParam;
	        break;			
	    default : break;
	  }
}
```
<br />

## 제목 (title)

제목 은 HTML 의 `span` 요소로 작성합니다.<br/>

```html
<span class="title title-1deps">제목</span>
```
  - span 의 class 는 `title title-1deps` 으로 정의합니다.
  - 제목(title) 의 깊에(depth) 에 따라 아래와 같이 `class` 를 구분합니다.
    - 1 depth : title **title-1deps**
    - 2 depth : title **title-2deps**

***Example***

```html
<span class="title title-1deps">상담이력 목록</span>
```
<br />

## 상담원 찾기

상담원 찾기 는 HTML 의 `input-text` 요소로 작성합니다.<br/>

```html
<input type="text" id="상담원명 ID" data-cmp-type="AGNT"/>
```
  - **data-cmp-type** : component 타입. `AGNT` 로 정의합니다.

> 상담원 ID 는 `input` 타입의 `hidden` 으로 생성되며 id 는 `상담원명ID_hid` 로 생성됩니다.

***Example***

```html
<input type="text" id="s_user_id_nm" name="s_user_id_nm" style="width:75px;" data-cmp-type="AGNT"/>
```
위 예제의 경우 상담원ID 는 `hidden` 타입으로 id 는 `s_user_id_nm_hid` 로 생성됩니다.

<br />


## 달력

달력 은 HTML 의 `input-text` 요소로 작성합니다.<br/>
달력 API는 [Air Datepicker](http://t1m0n.name/air-datepicker/docs/) 라이브러리 참조합니다.

```html
<input type='text' data-cmp-type="CLND" class="datepicker-here" data-min-view="최소 단위" data-view="시작 표시단위" data-date-format="표시 최소단위" value="기본값" />
```
  - **data-cmp-type** : component 타입. `CLND` 로 정의합니다.
  - **data-view** : 달력 시작 시, 표시 단위
    - days : 일 (Default 값)
    - months : 월
    - years : 년    
  - **data-min-view** : 달력 표시 최소 단위
    - days : 일 (Default 값)
    - months : 월      
  - **data-date-format** : 날짜 표시 Format
    - @ : time in milliseconds
    - d : date number
    - dd : date with leading zero
    - D : short day name
    - DD : full day name
    - m : month number
    - mm : month number with leading zero
    - M : short month name
    - MM : full month name
    - yy : two digit year number
    - yyyy : four digit year number
    - yyyy1 : first year of decade, which included current year
    - yyyy2 : last year of decade, which included current year
  - input 의 class 는 `datepicker-here` 으로 정의합니다.

***Example***

```html
달력(Day) 
<input type='text' id="calSample" class="datepicker-here" data-cmp-type="CLND" />

달력(Month) 
<input type='text' id="calSample2" class="datepicker-here" data-cmp-type="CLND" data-min-view="months" data-view="months" data-date-format="yyyy-MM"/>
```
<br />


## 상담 유형 Combo

상담유형 Combo 는 HTML 의 `select` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다.<br/><br/> 

```html
<!-- 대분류 -->
<select data-default-option="기본옵션" data-codes='공통코드' onChange="_UL.evnt.setSubSelect(this, 코드분류, 중분류ID, 소분류ID)"></select>
<!-- 중분류 -->
<select data-default-option="기본옵션" onChange="_UL.evnt.setSubSelect(this, 코드분류, 소분류ID)"></select>
<!-- 소분류 -->
<select data-default-option="기본옵션"></select>
```
  - **data-default-option** : 추가 코드
    - 1: ["00", "전체"]
    - 2: ["00", "선택"]
    - 4 : ["00", "== 선택 =="]
    - 10 : ["00", "== 전체 =="]
  - **data-codes** : Select 생성 코드 Object.

>  - 대분류, 중분류 `select` Element 에서 `onChange` 를 정의해야 합니다.<br />
> `onChange` 에서 하위 코드를 조회하는 `_UL.evnt.setSubSelect` 공통함수를 호출합니다. 
> - 코드분류는 `CONSL_CD` 를 사용합니다.

***Example***

```html
<select id="s_consl_lcd" name="s_consl_lcd" style="width:100px;" data-default-option="10" data-codes='${CONSLLCD}' onChange="_UL.evnt.setSubSelect(this, 'CONSL_CD', 's_consl_mcd', 's_consl_scd')"></select>
<select id="s_consl_mcd" name="s_consl_mcd" style="width:100px" data-default-option="10" onChange="_UL.evnt.setSubSelect(this, 'CONSL_CD', 's_consl_scd')"></select>
<select id="s_consl_scd" name="s_consl_scd" style="width:120px" data-default-option="10"></select>
```

<br />

## 조직 Combo

조직 Combo 는 HTML 의 `select` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다.<br/><br/> 

```html
<!-- 대분류 -->
<select data-default-option="기본옵션" data-codes='공통코드' onChange="_UL.evnt.setSubSelect(this, 코드분류, 중분류ID, 소분류ID)"></select>
<!-- 중분류 -->
<select data-default-option="기본옵션" onChange="_UL.evnt.setSubSelect(this, 코드분류, 소분류ID)"></select>
<!-- 소분류 -->
<select data-default-option="기본옵션"></select>
```
  - **data-default-option** : 추가 코드
    - 1: ["00", "전체"]
    - 2: ["00", "선택"]
    - 4 : ["00", "== 선택 =="]
    - 10 : ["00", "== 전체 =="]
  - **data-codes** : Select 생성 코드 Object.

>  - 대분류, 중분류 `select` Element 에서 `onChange` 를 정의해야 합니다.<br />
> `onChange` 에서 하위 코드를 조회하는 `_UL.evnt.setSubSelect` 공통함수를 호출합니다. 
> - 코드분류는 `TEAM_CD` 를 사용합니다.

***Example***

```html
<select id="s_team_lcd" name="s_team_lcd" style="width:100px" data-default-option="10" data-codes='${TEAMLCD}' onChange="_UL.evnt.setSubSelect(this, 'TEAM_CD', 's_team_mcd', 's_team_scd')"></select>
<select id="s_team_mcd" name="s_team_mcd" style="width:100px" data-default-option="10" onChange="_UL.evnt.setSubSelect(this, 'TEAM_CD', 's_team_scd')"></select>
<select id="s_team_scd" name="s_team_scd" style="width:120px" data-default-option="10"></select>
```

<br />