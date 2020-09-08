# UCARE API
UCARE API에 대한 설명입니다.  

---

## page

Page 관련 API 목록입니다.

### getEl

***Descrition***  
element 객체를 반환합니다.

***Syntax***  
```js
_UL.page.getEl(id)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 해당 id 에 해당하는 Element 객체를 반환

***Example***

```html
<input type="text" id="userNm" value="john" />

<script>
_UL.page.getEl('userNm');
</script>

<!-- 
<input type="text" id="userNm" value="john" />
 -->
```
<br />

### get

***Descrition***  
element 의 값을 반환합니다.

***Syntax***  
```js
_UL.page.get(id)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String / Array  
> input, select, textarea, radio 는 String 을 반환, checkbox 는 Array 를 반환

***Example***

```html
<input type="text" id="userNm" value="john" />

<script>
_UL.page.get('userNm');
// john
</script>
```
<br />


### set

***Descrition***  
element 의 값을 세팅합니다.

***Syntax***  
```js
_UL.page.set(id)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" value="john" />

<script>
_UL.page.set('userNm', 'smith');
</script>
```
<br />

### attr

***Descrition***  
element 의 속성을 반환 또는 변경합니다.

***Syntax***  
```js
_UL.page.attr(id, attributeName, value)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
        <tr>
            <td>attributeName</td>
            <td>String</td>
            <td>속성의 이름</td>
        </tr>
        <tr>
            <td>value</td>
            <td>String</td>
            <td>속성의 값</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String
> Element 의 속성 값을 반환

***Example***

```html
<input type="text" id="userNm" value="john" style="width:150px;" />

<script>
// get 샘플
_UL.page.attr('userNm', "style");
// width:150px;

// set 샘플
_UL.page.attr('userNm', "style", "width:300px;");
</script>
```
<br />

### data

***Descrition***  
element 의 사용자 지정 데이터 속성을 반환 또는 변경합니다.

***Syntax***  
```js
_UL.page.data(id, key, value)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
        <tr>
            <td>key</td>
            <td>String</td>
            <td>데이터 속성의 이름</td>
        </tr>
        <tr>
            <td>value</td>
            <td>String</td>
            <td>데이터 속성의 값</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String
> Element 의 데이터 속성 값을 반환

***Example***

```html
<input type="text" id="userNm" value="john" data-required="false" />

<script>
// get 샘플
_UL.page.data('userNm', "required");
// false

// set 샘플
_UL.page.data('userNm', "required", "true");
</script>
```
<br />

### hide

***Descrition***  
element 를 화면에서 숨깁니다.

***Syntax***  
```js
_UL.page.hide(id, isHide)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
        <tr>
            <td>isHide</td>
            <td>boolean</td>
            <td>숨김 여부 (true: 숨김, false: 표시)</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" value="john" />

<script>
// 숨김
_UL.page.hide('userNm', true);
</script>
```
<br />

### disable

***Descrition***  
element 의 비활성화 처리를 합니다.

***Syntax***  
```js
_UL.page.disable(id, isDisable)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
        <tr>
            <td>isDisable</td>
            <td>boolean</td>
            <td>비활성화 여부 (true: 비활성, false: 활성)</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" value="john" />

<script>
// 비활성화
_UL.page.disable('userNm', true);
</script>
```
<br />

### readonly

***Descrition***  
element 의 읽기전용 처리를 합니다.

***Syntax***  
```js
_UL.page.readonly(id, isReadonly)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
        <tr>
            <td>isReadonly</td>
            <td>String</td>
            <td>읽기전용 여부 (true: readonly 활성, false: readonly 비활성)</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" value="john" />

<script>
// 읽기전용
_UL.page.readonly('userNm', true);
</script>
```
<br />

### addClass

***Descrition***  
element 의 class 를 추가합니다.

***Syntax***  
```js
_UL.page.addClass(el, className)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>el</td>
            <td>String/Object</td>
            <td>대상 element id 또는 element 객체</td>
        </tr>
        <tr>
            <td>className</td>
            <td>String</td>
            <td>추가 class Name.<br /> multiple class 추가는 comma(,) 로 구분</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" value="john" class="" />

<script>
// single add
_UL.page.addClass('warning');

// multiple add
_UL.page.addClass(['warning','open']);
</script>
```
<br />

### removeClass

***Descrition***  
element 의 class 를 제거합니다.

***Syntax***  
```js
_UL.page.removeClass(el, className)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>el</td>
            <td>String/Object</td>
            <td>대상 element id 또는 element 객체</td>
        </tr>
        <tr>
            <td>className</td>
            <td>String</td>
            <td>삭제 class Name.<br /> multiple class 삭제는 comma(,) 로 구분</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" value="john" class="" />

<script>
// single remove
_UL.page.removeClass('warning');

// multiple remove
_UL.page.removeClass(['warning','open']);
</script>
```
<br />

### hasClass

***Descrition***  
element 의 class 의 존재유뮤를 반환합니다.

***Syntax***  
```js
_UL.page.hasClass(el, className)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>el</td>
            <td>String/Object</td>
            <td>대상 element id 또는 element 객체</td>
        </tr>
        <tr>
            <td>className</td>
            <td>String</td>
            <td>존재여부 확인 class Name</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : boolean  
> class 존재여부 반환 (true: 존재, false: 미존재)


***Example***

```html
<input type="text" id="userNm" value="john" class="warning" />

<script>
_UL.page.hasClass('warning');
// true
</script>
```
<br />

### toggleClass

***Descrition***  
element 에 class 존재여부 확인하여 toggle 처리합니다. 

***Syntax***  
```js
_UL.page.toggleClass(el, className)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>el</td>
            <td>String/Object</td>
            <td>대상 element id 또는 element 객체</td>
        </tr>
        <tr>
            <td>className</td>
            <td>String</td>
            <td>Toggle class Name</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<div id="divTest" class="show"></div>

<script>
var testEl = _UL.page.getEl('divTest');
_UL.page.toggleClass(testEl, 'show');
</script>
```
<br />

### focus

***Descrition***  
element 에 focus 를 처리 합니다.

***Syntax***  
```js
_UL.page.setFocus(id)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" value="john" />

<script>
_UL.page.focus('userNm');
</script>
```
<br />

### getText

***Descrition***  
Select element 에서 선택된 Option 의 Text 를 반환합니다.

***Syntax***  
```js
_UL.page.getText(id)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> select 에서 선택된 Option 의 Text 반환

***Example***

```html
<select id="testSelect" name="testSelect">
    <option value="">== 선택 ==</option>
    <option value="A">약속</option>
    <option value="G" selected>일반</option>
    <option value="W">작업</option>
</select>

<script>
_UL.page.getText('testSelect');
// 일반
</script>
```
<br />

### getRadioText

***Descrition***  
Radio element 에서 Checked Text 를 반환합니다.
Radio 는 `input`  과 `label` 구조로 되어 있어야 하며, label 에 for 속성이 정의되어야 합니다.

***Syntax***  
```js
_UL.page.getRadioText(name)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>name</td>
            <td>String</td>
            <td>대상 Radio Name</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> radio 에서 checked Text 반환

***Example***

```html
<input type="radio" id="recallTyCode_0" name="recallTyCode" value="" title="전체">
<label for="sRecallTyCode_0" class="mr-10">전체</label>
<input type="radio" id="recallTyCode_1" name="recallTyCode" value="RECL" title="재통화예약" checked>
<label for="sRecallTyCode_1" class="mr-10">재통화예약</label>
<input type="radio" id="recallTyCode_2" name="recallTyCode" value="CB" title="콜백">
<label for="sRecallTyCode_2" class="mr-10">콜백</label>

<script>
_UL.page.getRadioText('recallTyCode');
// 재통화예약
</script>
```
<br />

### setHtmlById

***Descrition***  
element 에 포함되는 HTML 을 설정합니다.

***Syntax***  
```js
_UL.page.setHtmlById(id, html)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
        <tr>
            <td>html</td>
            <td>String</td>
            <td>element 에 설정할 HTML String</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<div id="divSample"></div>

<script>
_UL.page.setHtmlById('divSample',"<span>테스트</span>");
</script>

<!-- 
    <div id="divSample">
        <span>테스트</span>
    </div>
 -->
```
<br />

### getGroup

***Descrition***  
Element 그룹의 값을 Object 로 반환합니다.

***Syntax***  
```js
_UL.page.getGroupData(groupId)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>groupId</td>
            <td>String</td>
            <td>대상 그룹 id</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 그룹 element (input, hidden, select, textarea, radio, checkbox) 의 값을 element 의 id 를 key 하는 object 로 반환

***Example***

```html
<input type="text" id="userNm" data-group-id="gpDtl" value="john" />
<select id="typeCd" data-group-id="gpDtl">
    <option value="">== 선택 ==</option>
    <option value="A">약속</option>
    <option value="G" selected>일반</option>
    <option value="W">작업</option>
</select>

<script>
_UL.page.getGroupData('gpDtl');
// {'userNm': 'john' , 'typeCd': 'G'}
</script>
```
<br />

### setGroup

***Descrition***  
Element 그룹의 값을 입력한 Object 의 데이터로 설정합니다.  
Object 의 key 와 매칭되는 Element id 가 있으면, Object 값을 설정합니다.

***Syntax***  
```js
_UL.page.setGroupData(groupId, groupData)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>groupId</td>
            <td>String</td>
            <td>대상 그룹 id</td>
        </tr>
        <tr>
            <td>groupData</td>
            <td>Object</td>
            <td>그룹 Element 에 설정할 그룹 data</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" data-group-id="gpDtl" value="john" />
<select id="typeCd" data-group-id="gpDtl">
    <option value="">== 선택 ==</option>
    <option value="A">약속</option>
    <option value="G" selected>일반</option>
    <option value="W">작업</option>
</select>

<script>
_UL.page.setGroupData('gpDtl', {'userNm': 'smith' , 'typeCd': 'A'});
</script>
```
<br />

### clearGroup

***Descrition***  
Element 그룹의 값을 초기화 합니다.

***Syntax***  
```js
_UL.page.setGroupData(groupId)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>groupId</td>
            <td>String</td>
            <td>대상 그룹 id</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" data-group-id="gpDtl" value="john" />
<select id="typeCd" data-group-id="gpDtl">
    <option value="">== 선택 ==</option>
    <option value="A">약속</option>
    <option value="G" selected>일반</option>
    <option value="W">작업</option>
</select>

<script>
_UL.page.clearGroup('gpDtl');
</script>
```
<br />


### disableGroup

***Descrition***  
그룹의 Element 를 비활성화 처리를 합니다.  

***Syntax***  
```js
_UL.page.disableGroup(groupId, isDisable)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>groupId</td>
            <td>String</td>
            <td>대상 그룹 id</td>
        </tr>
        <tr>
            <td>isDisable</td>
            <td>boolean</td>
            <td>비활성화 여부 (true: 비활성, false: 활성)</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="userNm" data-group-id="gpDtl" value="john" />
<select id="typeCd" data-group-id="gpDtl">
    <option value="">== 선택 ==</option>
    <option value="A">약속</option>
    <option value="G" selected>일반</option>
    <option value="W">작업</option>
</select>

<script>
_UL.page.disableGroup('gpDtl', true);
</script>
```
<br />

### setGroupText

***Descrition***  
Element 그룹의 html을 입력한 Object 의 데이터로 설정합니다.  
Object 의 key 와 매칭되는 Element id 가 있으면, Object 값을 설정합니다.

***Syntax***  
```js
_UL.page.setGroupText(groupId, groupData, cb)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>groupId</td>
            <td>String</td>
            <td>대상 그룹 id</td>
        </tr>
        <tr>
            <td>groupData</td>
            <td>Object</td>
            <td>그룹 Element 에 설정할 그룹 data</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<tr>
    <th>등록자</th>
    <td id="registUserNm" data-group-id="gpDtl"></td>
</tr>
<tr>
    <th>제목</th>
    <td id="bbsSj" data-group-id="gpDtl"></td>
</tr>

<script>
_UL.page.setGroupText('gpDtl', {'registUserNm': '관리자' , 'bbsSj': '게시판 등록 테스트'});
</script>
```
<br />

### createElement

***Descrition***  
DOM 를 생성하여 반환합니다.

***Syntax***  
```js
_UL.page.createElement(tag, attrs, text, event, innerHTML)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>tag</td>
            <td>String</td>
            <td>element Tag</td>
        </tr>
        <tr>
            <td>attrs</td>
            <td>Object</td>
            <td>element 속성</td>
        </tr>
        <tr>
            <td>text</td>
            <td>String</td>
            <td>element 의 Text</td>
        </tr>
        <tr>
            <td>event</td>
            <td>Array</td>
            <td>element 에 추가할 Event</td>
        </tr>
        <tr>
            <td>innerHTML</td>
            <td>String</td>
            <td>대상 element 에 추가할 HTML</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> element 를 생성하여 반환

***Example***

```html
<div id="divBtn"></div>

<script>
var parentEl = _UL.page.getEl('divBtn');
var childEl = _UL.page.createElement('button',
                                     {'id':'btnTest', 'class': 'btn blue'},
                                     '테스트',
                                     [{'event' : 'click','action' : function() { console.log("test...");}}]);

parentEl.appendChild(childEl);
</script>

<!-- 
<div id="divBtn">
    <button type="button" id="btnTest" class="btn blue" onclick="function() {.....}">테스트</button>
</div>
 -->
```
<br />

### appendTag

***Descrition***  
대상 Element 에 DOM 를 생성하여 추가합니다.

***Syntax***  
```js
_UL.page.appendTag(parentEl, tagInfo)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>parentEl</td>
            <td>Object</td>
            <td>부모 element 객체</td>
        </tr>
        <tr>
            <td>tagInfo</td>
            <td>Object</td>
            <td>DOM 생성 객체 정보
                <ul>
                  <li>tag : element Tag</li>
                  <li>options : element 속성</li>
                  <li>text : element 의 Text</li>
                  <li>event : element 에 추가할 Event</li>
                  <li>innerHTML : element 에 추가할 HTML</li>
                  <li>child : element 의 하위 DOM 정보</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 부모 element 에 생성된  DOM 을 추가하여 반환

***Example***

```html
<div id="divSample"></div>

<script>
var parentEl = _UL.page.getEl('divSample');

var childTagInfo = {'tag'     : 'ul',
                    'options' : {'id':'ulSample', 'class': 'ul-sample'},
                    'child'   : [
                        {'tag' : 'li', 'options': {'class': 'li-sample'}, 'text': '사과',
                         'event': [{'event': 'click', 'action': function() {fnTeat('사과');}}]},
                        {'tag' : 'li', 'options': {'class': 'li-sample'}, 'text': '배'}
                        {'tag' : 'li', 'options': {'class': 'li-sample'}, 'text': '오렌지'}
                    ]
                   }

_UL.page.appendTag(parentEl, childTagInfo);
</script>

<!-- 
<div id="divSample">
    <ul class="ul-sample">
        <li class="li-sample" onclick="function() {fnTeat('사과');}">사과</li>
        <li class="li-sample">배</li>
        <li class="li-sample">오렌지</li>
    </ul>
</div>
 -->
```
<br />

### removeChild

***Descrition***  
element 에서 모든 자식 Element 를 제거합니다.

***Syntax***  
```js
_UL.page.removeChild(id)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<div id="divSample">
    <div id="child1">사과</div>
    <div id="child2">배</div>
    <div id="child3">오렌지</div>
</div>

<script>
_UL.page.removeChild('divSample');
</script>

<!-- 
<div id="divSample">
</div>
 -->
```

<br />

### createSelectOption

***Descrition***  
Select element 에 Option 을 추가합니다.

***Syntax***  
```js
_UL.page.createSelectOption(el, optList, settings)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>el</td>
            <td>String</td>
            <td>대상 Select element 객체</td>
        </tr>
        <tr>
            <td>optList</td>
            <td>Array</td>
            <td>Option 생성 데이터 목록</td>
        </tr>
        <tr>
            <td>settings</td>
            <td>Object</td>
            <td>Option 생성을 위한 설정 정보
                <ul>
                  <li>textPty : 데이터 목록 (JSON List)에서 Text 프로퍼티</li>
                  <li>valuePty : 데이터 목록 (JSON List)에서 Value 프로퍼티</li>
                  <li>initOption : Option 초기화 여부. (true: 기존 Option 초기화 삭제, false: 미삭제)</li>
                  <li>defaultValue : Option 기본 선택 Value</li>
                  <li>cb : Option 생성 후, 호출 콜백함수</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<select id="selectSample">
    <option value='banana'>바나나</option>
</select>

<script>
var dataList =[
    {'code': 'apple', 'codeNm': '사과'},
    {'code': 'pear', 'codeNm': '배'},
    {'code': 'orange', 'codeNm': '오렌지'}
];

var tgtEl = _UL.page.getEl("selectSample");

_UL.page.createSelectOption(tgtEl, dataList, {'textPty': 'codeNm', 'valuePty': 'code', 'initOption': true, 'defaultValue': 'orange'});
</script>

<!-- 
<select id="selectSample">
    <option value='apple'>사과</option>
    <option value='pear'>배</option>
    <option value='orange' selected>오렌지</option>
</select>
 -->
```
<br />

### removeSelectOption

***Descrition***  
Select element 에 Option 을 삭제합니다.

***Syntax***  
```js
_UL.page.removeSelectOption(el, defaultText, cb)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>el</td>
            <td>String</td>
            <td>대상 Select element 객체</td>
        </tr>
        <tr>
            <td>defaultText</td>
            <td>String</td>
            <td>Default Text (미삭제)</td>
        </tr>
        <tr>
            <td>cb</td>
            <td>Object</td>
            <td>Option 삭제 후, 호출 콜백함수</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<select id="selectSample">
    <option value='banana'>바나나</option>
    <option value='apple'>사과</option>
    <option value='orange' selected>오렌지</option>
</select>

<script>
var tgtEl = _UL.page.getEl("selectSample");

_UL.page.removeSelectOption(tgtEl, '사과');
</script>

<!-- 
<select id="selectSample">
    <option value='apple'>사과</option>
</select>
 -->
```
<br />

### getChildElementsByIdStartsWith

***Descrition***  
element 의 하위 element 에서 입력한 id 로 시작하는 element 목록을 반환합니다.

***Syntax***  
```js
_UL.page.getChildElementsByIdStartsWith(parentEl, startId)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>parentEl</td>
            <td>String</td>
            <td>부모 element 객체</td>
        </tr>
        <tr>
            <td>startId</td>
            <td>String</td>
            <td>시작 element id</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Array  
> 대상 element 의 하위 element 에서 id 가 검색 id 값으로 시작하는 element 요소 Array 를 반환

***Example***

```html
<div id="divSamples">
    <div id="page1"></div>
    <div id="page2"></div>
    <div id="test1"></div>
    <div id="test2"></div>
    <div id="page3"></div>
</div>

<script>
var parentEl = _UL.page.getEl('divSamples');
_UL.page.getChildElementsByIdStartsWith(parentEl, 'page');
</script>
```

<!-- 
    <div id="page1"></div>
    <div id="page2"></div>
    <div id="page3"></div>
-->

<br />

### changeTab

***Descrition***  
ucare Tab UI 에서 대상 tab 의 선택 class 를 설정합니다.

***Syntax***  
```js
_UL.page.changeTab(id, index)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>id</td>
            <td>String</td>
            <td>대상 element id</td>
        </tr>
        <tr>
            <td>index</td>
            <td>Number</td>
            <td>대상 tab index</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<ul id="tabObj" data-cmp-type="TAB" data-title="개요,관련지식,담당자,변경이력"></ul>

<script>
function tabObj_OnTabClick(index) {
    _UL.page.changeTab('tabObj', index);
    ...
}
</script>
```
<br />

### toggleGroupTab

***Descrition***  
ucare Tab UI에서 Tab 선택 시, 선택 div 를 표시(display 변경) 합니다.

***Syntax***  
```js
_UL.page.toggleGroupTab(showId, tabGroupId)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>showId</td>
            <td>String</td>
            <td>표시할 div element id</td>
        </tr>
        <tr>
            <td>tabGroupId</td>
            <td>String</td>
            <td>대상 tab group id (`data-tab-group` 로 정의함)</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<ul id="tabMainFunc" data-cmp-type="TAB" data-title="상담등록,재통화/콜백,캠페인"></ul>
<div id="tabMainConslSave" data-tab-group="tabMainFuncGroup"></div>
<div id="tabMainReCall" data-tab-group="tabMainFuncGroup" style="display: none;" ></div>
<div id="tabMainCampaign" data-tab-group="tabMainFuncGroup" style="display: none;" ></div>

<script>
function tabObj_OnTabClick(index) {

    switch (index) {
        case 0: // 상담등록
            _UL.page.toggleGroupTab('tabMainConslSave', 'tabMainFuncGroup');
            break;

        case 1: // 재통화/콜백
            _UL.page.toggleGroupTab('tabMainReCall', 'tabMainFuncGroup');
            break;

        case 2: // 캠페인
            _UL.page.toggleGroupTab('tabMainCampaign', 'tabMainFuncGroup');
            break;

        default: break;
    }    
    ...
}
</script>
```
<br />

### getStepCode

***Descrition***  
계층형 공통코드 목록을 반환합니다.

***Syntax***  
```js
_UL.page.getStepCode(stepCode, codeLevel, upperClCode)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>stepCode</td>
            <td>String</td>
            <td>최상위 코드분류 ('CONSL_CD': 상담유형코드,'TEAM_CD': 조직분류코드)</td>
        </tr>
        <tr>
            <td>codeLevel</td>
            <td>Number</td>
            <td>코드레벨</td>
        </tr>
        <tr>
            <td>upperClCode</td>
            <td>String</td>
            <td>상위분류코드</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Array  
> 계층형 공통코드에서 입력 레벨의 코드정보 Array 를 반환

***Example***

```html
<script>
var arrCnsltTyMlsfcCode = _UL.page.getStepCode('CONSL_CD', 2, 'C001');

// [
//     {'lrgeClCode': 'CONSL_CD', 'code': 'C001001', 'codeNm': '중분류코드1', ...},
//     {'lrgeClCode': 'CONSL_CD', 'code': 'C001002', 'codeNm': '중분류코드2', ...},
//     {'lrgeClCode': 'CONSL_CD', 'code': 'C001003', 'codeNm': '중분류코드3', ...}
// ]
</script>
```
<br />

### getCodeList

***Descrition***  
화면에서 사용되는 공통코드 목록을 반환합니다.  
공통코드는 JAVA `Controller` 에서 model 에 정의한 공통코드에 한하여 조회됩니다.

***Syntax***  
```js
_UL.page.getCodeList(code)
```

***Parameters***  

<table style="width:95%">
    <colgroup>
        <col style="width: 25%;"/>
        <col style="width: 15%;"/>
        <col style="*"/>
    </colgroup>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>code</td>
            <td>String</td>
            <td>공통코드 대분류</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Array  
> 공통코드 정보 Array 를 반환

***Example***

```html
<script>
var arrCode = _UL.page.getCodeList('KMS001');

// [
//     {'lrgeClCode': 'KMS001', 'code': 'MNL', 'codeNm': '상담지식', ...},
//     {'lrgeClCode': 'KMS001', 'code': 'FAQ', 'codeNm': 'FAQ', ...},
//     {'lrgeClCode': 'KMS001', 'code': 'CASE', 'codeNm': '사례', ...}
// ]
</script>
```
<br />
