# 입력 Element 그리기
입력 Element 생성 및 속성을 설명입니다.  

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
  - **data-format <span style="color:red;">(_Option_)</span>** : Format 종류
    - DATE : yyyy-MM-dd
    - DATET : yyyy-MM-dd hh:mm:ss
    - NUMBER :
    - TIME :
    - TEL :
    - TNO :
    - SEC :
    - POST :
    - SSN :

  - **data-enter <span style="color:red;">(_Option_)</span>** : Enter 실행 시, 호출 Function 명

***Example***

```html
<input type="text" data-format="DATET" data-enter="searchList" />
```
<br />


## Radio

Input(Radio) 는 HTML 의 `div` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다. 

```html
<div data-cmp-type="RADIO" data-id="radio 엘리먼트 ID" data-codes='공통코드' data-default-option="기본옵션" data-default-value="기본값" data-click="click 이벤트 함수명" data-change="change 이벤트 함수명"></div>
```
  - **data-cmp-type** : component 타입. `RADIO` 로 정의합니다.
  - **data-id** : Radio Element 에서 사용할 ID.
  - **data-codes** : Radio 생성 코드 Object.
  - **data-default-option <span style="color:red;">(_Option_)</span>** : 추가 코드
    - 1: ["00", "전체"]
    - 2: ["00", "선택"]
    - 4 : ["", "== 선택 =="]
    - 10 : ["", "== 전체 =="]
  - **data-default-value <span style="color:red;">(_Option_)</span>** : 기본 선택값. 코드값과 value 가 동일한 경우 check 처리.
  - **data-click <span style="color:red;">(_Option_)</span>** : click 이벤트 호출할 함수명
  - **data-change <span style="color:red;">(_Option_)</span>** : change 이벤트 호출할 함수명

***Example***

```html
<div id="div_schdul_type_cd" data-cmp-type="RADIO" data-id="s_schdul_type_cd" data-codes='${TST002}' data-default-option="1" data-click="setData" data-change="setValid"></div>
```
<br />

## Checkbox

Input(Checkbox) 는 HTML 의 `div` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다. 

```html
<div data-cmp-type="CHECKBOX" data-id="checkbox 엘리먼트 ID" data-codes='공통코드' data-default-option="기본옵션" data-default-value="기본값" data-click="click 이벤트 함수명" data-change="change 이벤트 함수명"></div>
```
  - **data-cmp-type** : component 타입. `CHECKBOX` 로 정의합니다.
  - **data-id** : Checkbox Element 에서 사용할 ID.
  - **data-codes** : Checkbox 생성 코드 Object.
  - **data-default-option <span style="color:red;">(_Option_)</span>** : 추가 코드
    - 1: ["00", "전체"]
    - 2: ["00", "선택"]
    - 4 : ["", "== 선택 =="]
    - 10 : ["", "== 전체 =="]
  - **data-default-value <span style="color:red;">(_Option_)</span>** : 기본 선택값. 코드값과 value 가 동일한 경우 check 처리.
  - **data-click <span style="color:red;">(_Option_)</span>** : click 이벤트 호출할 함수명
  - **data-change <span style="color:red;">(_Option_)</span>** : change 이벤트 호출할 함수명

***Example***

```html
<div id="div_talk_type_cd" data-cmp-type="CHECKBOX" data-id="s_talk_type_cd" data-codes='${TST001}' data-default-option="1" data-click="setData" data-change="setValid"></div>
```
<br />

## Select

Input(Checkbox) 는 HTML 의 `div` 요소로 작성합니다.<br/>
`dataset` 속성을 이용하여 Custom 속성을 정의합니다. 

```html
<select data-codes='공통코드' data-default-option="기본옵션" data-default-value="기본값"></select>
```
  - **data-codes** : Select 생성 코드 Object.
  - **data-default-option <span style="color:red;">(_Option_)</span>** : 추가 코드
    - 1: ["00", "전체"]
    - 2: ["00", "선택"]
    - 4 : ["", "== 선택 =="]
    - 10 : ["", "== 전체 =="]
  - **data-default-value <span style="color:red;">(_Option_)</span>** : 기본 선택값. 코드값과 value 가 동일한 경우 selected 처리.

***Example***

```html
<select id="consl_cd" name="consl_cd" data-codes='${TST001}' data-default-option="4" style="width:170px;" onchange="setConslCdData(this)"></select>
```
<br />

## 공통 속성

모든 Elemet 에서 사용하는 공통 `dataset` 속성을 정의합니다. 

```html
<input type="text" data-required="필수여부" data-requirednm="항목명" />
```
  - **data-required <span style="color:red;">(_Option_)</span>** : 필수 입력여부.
  - **data-requirednm <span style="color:red;">(_Option_)</span>** : 필수 입력 체크 시, 표시할 항목명.

***Example***

```html
<input type="text" id="user_nm" name="user_nm" data-required="true" data-requirednm="사용자명" />
```
<br />