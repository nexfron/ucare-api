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
_UL.page.attr('userNm', "required");
// false

// set 샘플
_UL.page.attr('userNm', "required", "true");
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
    <button type="button" id="btnTest" class="btn blue" onclick="function() {.....}"></button>
</div>
 -->
```
<br />

### appendTag

***Descrition***  
대상 Element 에 DOM 를 생성하여 추가합니다.

***Syntax***  
```js
_UL.page.createElement(parentEl, tagInfo)
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
            <td>element Tag</td>
        </tr>
        <tr>
            <td>attrs</td>
            <td>Object</td>
            <td>element 속성</td>
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
    <button type="button" id="btnTest" class="btn blue" onclick="function() {.....}"></button>
</div>
 -->
```
<br />

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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

### name

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