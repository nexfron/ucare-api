# UI 구성 Element
UI 구성을 위한 Element 생성 및 속성에 대한 설명입니다.

---
모든 HTML Element 는 기본적인 HTML Element 의 Spec 으로 생성하며, **dataset** 요소를 통하여 UCARE 에 맞게 Customize 합니다.

HTML Element 는 MDN 의 [HTML 요소 레퍼런스
](https://developer.mozilla.org/ko/docs/Web/HTML/Element) 를 참조하시기 바랍니다.


## Input (Text)

Input(Text) 는 HTML 의 기본적인 [Input](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input) 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다. 

```html
<input type="text" data-format="Format 종류" data-enter="함수명" />
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-format</td>
            <td>N</td>
            <td>Format 종류
                <ul>
                  <li>DATE : 8자리(yyyy-MM-dd), 6자리(yyyy-MM)</li>
                  <li>DATET : 14자리(yyyy-MM-dd HH:mm:ss)</li>
                  <li>TIME : 6자리(HH:mm:ss), 4자리(HH:mm)</li>
                  <li>MONEY : 금액 형식(comma)</li>
                  <li>TEL : 전화번호(000-0000-0000) 형식</li>
                  <li>SEC : 시간(HH:mm:ss) 형식</li>
                  <li>SSN : 주민번호(뒤에 6자리 * 표시)</li>
                  <li>NUMBER : 숫자만 입력 가능</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-enter</td>
            <td>N</td>
            <td>Enter 실행 시, 호출 함수명</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<input type="text" id="registDt" data-format="DATET" data-enter="searchList" />

<script>
  function searchList() {
    ...
  }
</script>
```
<br />


## Radio

Input(Radio) 는 HTML 의 `div` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다. 

```html
<div data-cmp-type="RADIO" data-id="radio 엘리먼트 ID" data-codes='공통코드' data-default-option="추가코드" data-default-value="기본값" data-click="click 이벤트 함수명" data-change="change 이벤트 함수명"></div>
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-cmp-type</td>
            <td>Y</td>
            <td>component 타입. "RADIO" 로 정의합니다</td>
        </tr>
        <tr>
            <td>data-id</td>
            <td>Y</td>
            <td>Radio Element 에서 사용할 ID</td>
        </tr>
        <tr>
            <td>data-codes</td>
            <td>Y</td>
            <td>Radio 생성 공통코드</td>
        </tr>
        <tr>
            <td>data-default-option</td>
            <td>N</td>
            <td>추가 Radio 코드
                <ul>
                  <li>1 : ["00", "전체"]</li>
                  <li>2 : ["00", "선택"]</li>
                  <li>4 : ["", "선택"]</li>
                  <li>10 : ["", "전체"]</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-default-value</td>
            <td>N</td>
            <td>기본 선택값. 코드값과 value 가 동일한 경우 check 처리</td>
        </tr>
        <tr>
            <td>data-click</td>
            <td>N</td>
            <td>click 이벤트 호출 함수명</td>
        </tr>
        <tr>
            <td>data-change</td>
            <td>N</td>
            <td>change 이벤트 호출 함수명</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<div id="divSchdulTypeCd" data-cmp-type="RADIO" data-id="schdulTypeCd" data-codes='TST002' data-default-option="1" data-click="setData" data-change="setValid"></div>

<script>
  function setData() {
    ...
  }

  function setValid() {
    ...
  }
</script>
```
<br />

## Checkbox

Input(Checkbox) 는 HTML 의 `div` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다. 

```html
<div data-cmp-type="CHECKBOX" data-id="checkbox 엘리먼트 ID" data-codes='공통코드' data-default-option="추가코드" data-default-value="기본값" data-click="click 이벤트 함수명" data-change="change 이벤트 함수명"></div>
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-cmp-type</td>
            <td>Y</td>
            <td>component 타입. "CHECKBOX" 로 정의합니다</td>
        </tr>
        <tr>
            <td>data-id</td>
            <td>Y</td>
            <td>Checkbox Element 에서 사용할 ID</td>
        </tr>
        <tr>
            <td>data-codes</td>
            <td>Y</td>
            <td>Checkbox 생성 공통코드</td>
        </tr>
        <tr>
            <td>data-default-option</td>
            <td>N</td>
            <td>추가 Checkbox 코드
                <ul>
                  <li>1 : ["00", "전체"]</li>
                  <li>2 : ["00", "선택"]</li>
                  <li>4 : ["", "선택"]</li>
                  <li>10 : ["", "전체"]</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-default-value</td>
            <td>N</td>
            <td>기본 선택값. 코드값과 value 가 동일한 경우 check 처리</td>
        </tr>
        <tr>
            <td>data-click</td>
            <td>N</td>
            <td>click 이벤트 호출 함수명</td>
        </tr>
        <tr>
            <td>data-change</td>
            <td>N</td>
            <td>change 이벤트 호출 함수명</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<div id="divTalkTypeCd" data-cmp-type="CHECKBOX" data-id="talkTypeCd" data-codes='TST001' data-default-option="1" data-click="setData" data-change="setValid"></div>

<script>
  function setData() {
    ...
  }

  function setValid() {
    ...
  }
</script>
```
<br />

## Select

Input(Checkbox) 는 HTML 의 `div` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다. 

```html
<select data-codes='공통코드' data-default-option="추가코드" data-default-value="기본값"></select>
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-codes</td>
            <td>Y</td>
            <td>Select 생성 공통코드</td>
        </tr>
        <tr>
            <td>data-default-option</td>
            <td>N</td>
            <td>추가 Checkbox 코드
                <ul>
                  <li>1 : ["00", "전체"]</li>
                  <li>2 : ["00", "선택"]</li>
                  <li>4 : ["", "== 선택 =="]</li>
                  <li>10 : ["", "== 전체 =="]</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-default-value</td>
            <td>N</td>
            <td>기본 선택값. 코드값과 value 가 동일한 경우 check 처리</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<select id="searchType" name="searchType" data-codes='TST001' data-default-option="10" onchange="setData"></select>

<script>
  function setData() {
    ...
  }
</script>
```
<br />

## 달력

달력 은 HTML 의 `input-text` 요소로 작성합니다.<br/>
달력 API는 [Air Datepicker](http://t1m0n.name/air-datepicker/docs/) 라이브러리 참조합니다.<br/>
input 의 class 는 `datepicker-here` 으로 정의합니다.

```html
<input type='text' data-cmp-type="CLND" class="datepicker-here" data-min-view="최소 단위" data-view="시작 표시단위" data-date-format="표시 최소단위" value="기본값" />
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-cmp-type</td>
            <td>Y</td>
            <td>component 타입. "CLND" 로 정의합니다.</td>
        </tr>
        <tr>
            <td>data-view</td>
            <td>N</td>
            <td>달력 시작 시, 표시 단위
                <ul>
                  <li>days : 일 (Default 값)</li>
                  <li>months : 월</li>
                  <li>years : 년</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-min-view</td>
            <td>N</td>
            <td>달력 시작 시, 표시 단위
                <ul>
                  <li>days : 일 (Default 값)</li>
                  <li>months : 월</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-date-format</td>
            <td>N</td>
            <td>날짜 표시 Format
                <ul>
                  <li>@ : time in milliseconds</li>
                  <li>d : date number</li>
                  <li>dd : date with leading zero</li>
                  <li>D : short day name</li>
                  <li>DD : full day name</li>
                  <li>m : month number</li>
                  <li>mm : month number with leading zero</li>
                  <li>M : short month name</li>
                  <li>MM : full month name</li>
                  <li>yy : two digit year number</li>
                  <li>yyyy : four digit year number</li>
                  <li>yyyy1 : first year of decade, which included current year</li>
                  <li>yyyy2 : last year of decade, which included current year</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-default-value</td>
            <td>N</td>
            <td>기본 선택값. 코드값과 value 가 동일한 경우 check 처리</td>
        </tr>
    </tbody>
</table>

***Example***

```html
 - 달력(Day) 
<input type='text' id="calSampleDay" class="datepicker-here" data-cmp-type="CLND" value="<%=DateUtil.getFormatDateTime("yyyy-MM-dd")%>" />

 - 달력(Month) 
<input type='text' id="calSampleMonth" class="datepicker-here" data-cmp-type="CLND" data-min-view="months" data-view="months" data-date-format="yyyy-MM" value="<%=DateUtil.getFormatDateTime("yyyy-MM")%>"/>

 - 달력(Year) 
<input type="text" id="calSampleYear" class="datepicker-here" data-cmp-type="CLND" data-min-view="years" data-view="years" data-date-format="yyyy" data-format="DATE" value="<%=DateUtil.getFormatDateTime("yyyy")%>" />
```
<br />

## 시간

시간 은 HTML 의 `input-text` 요소로 작성합니다.<br/>
시간 API는 [flatpicke](https://flatpickr.js.org/examples/#time-picker) 라이브러리 의 `Time Picker` 를 참조합니다.<br/>

```html
<input type='text' data-cmp-type="TIME" data-format="TIME" value="기본값" />
```

시간(Time Picker) Elemet 를 사용하는 화면 은 상단에 아래 리소스를 추가해야 합니다.<br/>

```html
<!-- flatpickr  -->
<link rel='stylesheet' type='text/css' href="<c:out value='${libPath}'/>/flatpickr/dist/flatpickr.css"/>
<script type="text/javascript" src="<c:out value='${libPath}'/>/flatpickr/dist/flatpickr.js" charset="utf-8"></script>
<script type="text/javascript" src="<c:out value='${libPath}'/>/flatpickr/dist/l10n/ko.js" charset="utf-8"></script>
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-cmp-type</td>
            <td>Y</td>
            <td>component 타입. "TIME" 로 정의합니다.</td>
        </tr>
        <tr>
            <td>data-format</td>
            <td>Y</td>
            <td>"TIME" 로 정의합니다.</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<input type="text" id="endTime" style="width:75px;" data-cmp-type="TIME" data-format="TIME" value="2359" />
```
<br />

## 상담원 찾기

상담원 찾기 는 HTML 의 `input-text` 요소로 작성합니다.<br/>

```html
<input type="text" id="상담원명 ID" data-cmp-type="AGNT"/>
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-cmp-type</td>
            <td>Y</td>
            <td>component 타입. "AGNT" 로 정의합니다.</td>
        </tr>
        <tr>
            <td>data-id</td>
            <td>Y</td>
            <td>상담원 ID 를 Setting할 Hidden Element에서 사용할 ID</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<input type="text" id="rceptUserNm" data-id="rceptUserId" data-cmp-type="AGNT"/>
```

<br />

## 상담 유형 Combo

상담유형 Combo 는 HTML 의 `select` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다.<br/>
`onChange` 에서 하위 코드를 조회하는 `_UL.evnt.setSubSelect` 공통함수를 호출합니다.<br/><br/>  

```html
<!-- 대분류 -->
<select data-codes='CONSL_CD' data-level='1' data-default-option="기본옵션" onChange="_UL.evnt.setSubSelect(this, 'CONSL_CD', 중분류ID, 소분류ID)"></select>
<!-- 중분류 -->
<select data-level='2' data-default-option="기본옵션" onChange="_UL.evnt.setSubSelect(this, 'CONSL_CD', 소분류ID)"></select>
<!-- 소분류 -->
<select data-level='3' data-default-option="기본옵션"></select>
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-level</td>
            <td>Y</td>
            <td>계층형 레벨</td>
        </tr>
        <tr>
            <td>data-default-option</td>
            <td>N</td>
            <td>추가 Select 코드
                <ul>
                  <li>1 : ["00", "전체"]</li>
                  <li>2 : ["00", "선택"]</li>
                  <li>4 : ["", "== 선택 =="]</li>
                  <li>10 : ["", "== 전체 =="]</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-codes</td>
            <td>Y</td>
            <td>상담유형 공통코드, "CONSL_CD" 로 정의합니다.</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<!-- 상담유형 대분류 -->
<select id="cnsltTyLclasCode" style="width:150px;" data-level="1" data-default-option="10" data-codes='CONSL_CD' onChange="_UL.evnt.setSubSelect(this, 'CONSL_CD', 'cnsltTyMlsfcCode', 'cnsltTySclasCode')"></select>
<!-- 상담유형 중분류 -->
<select id="cnsltTyMlsfcCode" style="width:150px" data-level="2" data-default-option="10" onChange="_UL.evnt.setSubSelect(this, 'CONSL_CD', 'cnsltTySclasCode')"></select>
<!-- 상담유형 소분류 -->
<select id="cnsltTySclasCode" style="width:150px" data-level="3" data-default-option="10"></select>
```

<br />

## 조직 Combo

조직 Combo 는 HTML 의 `select` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다.<br/><br/> 
`onChange` 에서 하위 코드를 조회하는 `_UL.evnt.setSubSelect` 공통함수를 호출합니다.<br/><br/>  

```html
<!-- 대분류 -->
<select data-codes='TEAM_CD' data-level='1' data-default-option="기본옵션" onChange="_UL.evnt.setSubSelect(this, 'TEAM_CD', 중분류ID, 소분류ID)"></select>
<!-- 중분류 -->
<select data-level='2' data-default-option="기본옵션" onChange="_UL.evnt.setSubSelect(this, 'TEAM_CD', 소분류ID)"></select>
<!-- 소분류 -->
<select data-level='3' data-default-option="기본옵션"></select>
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-level</td>
            <td>Y</td>
            <td>계층형 레벨</td>
        </tr>
        <tr>
            <td>data-default-option</td>
            <td>N</td>
            <td>추가 Select 코드
                <ul>
                  <li>1 : ["00", "전체"]</li>
                  <li>2 : ["00", "선택"]</li>
                  <li>4 : ["", "== 선택 =="]</li>
                  <li>10 : ["", "== 전체 =="]</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data-codes</td>
            <td>Y</td>
            <td>상담유형 공통코드, "CONSL_CD" 로 정의합니다.</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<!-- 조직 대분류 -->
<select id="teamLclasCode" style="width:150px" data-level="1" data-default-option="4" data-codes='TEAM_CD' onchange="_UL.evnt.setSubSelect(this, 'TEAM_CD', 'teamMlsfcCode', 'teamSclasCode')"></select>
<!-- 조직 중분류 -->
<select id="teamMlsfcCode" style="width:150px" data-level="2" data-default-option="4" onchange="_UL.evnt.setSubSelect(this, 'TEAM_CD', 'teamSclasCode')"></select>
<!-- 조직 소분류 -->
<select id="teamSclasCode" style="width:150px" data-level="3" data-default-option="4"></select>		
```

<br />

## UI Element 공통 속성

모든 UI Elemet 에서 사용하는 공통 `dataset` 속성을 정의합니다. 

```html
<input type="text" data-group-id="그룹id" data-required="필수여부" data-requirednm="항목명" />
```

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-group-id</td>
            <td>N</td>
            <td>입력 Element 그룹 ID</td>
        </tr>
        <tr>
            <td>data-required</td>
            <td>N</td>
            <td>필수 입력여부. (true/false)</td>
        </tr>
        <tr>
            <td>data-requirednm</td>
            <td>N</td>
            <td>필수 입력 체크 시, 표시할 항목명</td>
        </tr>
    </tbody>
</table>

***Example***

```html
<input type="text" id="userNm" name="userNm" data-group-id="gpDatail" data-required="true" data-requirednm="사용자명" />
```
<br />

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

***Attributes***

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>속성</th>
            <th>필수</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>data-cmp-type</td>
            <td>Y</td>
            <td>component 타입. "TAB" 로 정의합니다.</td>
        </tr>
        <tr>
            <td>data-title</td>
            <td>Y</td>
            <td>Tab 으로 표현할 텍스트 목록. "comma(,)" 로 구분.</td>
        </tr>
    </tbody>
</table>

> - 탭을 클릭하면 `TabID_OnTabClick` Function 을 호출하며, 탭 순서(index)를 argument 로 전달합니다.
> - `TabID_OnTabClick` Function 의 처음에 `_UL.page.changeTab(Tab ID, Tab index)` 공통 Function 을 호출해야 합니다.

***Example***

```html
<ul id="tabObj" data-cmp-type="TAB" data-title="개요,관련지식,담당자,변경이력"></ul>
```

위 예제에서 탭ID 가 `tabObj` 경우, `tabObj_OnTabClick` Function 을 호출합니다.<br />
Function 의 처음에 `_UL.page.changeTab('tabObj', index)` 공통함수를 호출합니다.

```js
function tabObj_OnTabClick(index)
{
	_UL.page.changeTab('tabObj', index);

	switch (index)
	{
	    case 0 :
	    	alert("1 번째 탭 클릭");
	        break;
	
	    case 1 :
	    	alert("2 번째 탭 클릭");
	        break;
	       
	    case 2 :
	    	alert("3 번째 탭 클릭");
	        break;
	    default : 
            break;
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