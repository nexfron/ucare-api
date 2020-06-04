# Grid
UI 구성을 위한 Grid 생성 및 속성에 대한 설명입니다.
---

## Grid Div Element 생성

Grid Container 가 생성될 위치에 아래와 같은 div Tag 를 작성합니다.<br/>

```html
<div id="Grid Id"></div>
```

***Example***

```html
<div id="grdSample"></div>
```
<br />

## Grid 생성 공통 Function 호출 

문서가 Load 되었을 때, Grid 생성 공통 Function 을 호출합니다.<br/>
`gridOption` 는 Grid 생성을 위한 환경 및 컬럼 등의 속성을 포함하는 Object 입니다.<br/>

gridOption 의 `Cols`, `height` 는 필수 입력 값이며, gridOption 의 `Cfg`, `Cols` 는 IBSheet 의 속성을 사용합니다.<br/>
<br />
<br />
`gridOption` 의 각 항목별 IBSheet 의 API는 아래 URL 링크를 참조하십시요.

  - IBSheet 의 Config 속성 참조 - [SetConfig - IBSheet](https://www.ibsheet.com/docs/ibsheet/IBSheet.init.html#SetConfig)
  - IBSheet 의 Column 속성 참조 - [InitColumns - IBSheet](https://www.ibsheet.com/docs/ibsheet/IBSheet.init.html#InitColumns)
  - IBSheet 의 Header 속성 참조 - [InitHeaders - IBSheet](https://www.ibsheet.com/docs/ibsheet/IBSheet.init.html#InitHeaders)
  - IBSheet 의 Event 참조 - [event - IBSheet](https://www.ibsheet.com/docs/ibsheet/IBSheet.event.html)

```javascript
_UL.comp.createGrid(gridId, gridOption);
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
            <td>gridId</td>
            <td>String</td>
            <td>Grid 생성 Id</td>
        </tr>
        <tr>
            <td>gridOption</td>
            <td>Object</td>
            <td>Grid 생성 옵션
                <ul>
                  <li>Cfg : Grid 에 기본 속성을 설정</li>
                  <li>HeaderMode : Grid 의 Header 속성을 설정</li>
                  <li>Cols : Grid 컬럼 속성을 설정</li>
                  <li>width : Grid 의 너비를 설정. (Default 100%)</li>
                  <li>height : Grid 의 높이를 설정. (Default 300px)</li>
                  <li>options : Grid 기타 속성을 설정</li>
                </ul>            
            </td>
        </tr>
    </tbody>
</table>

***Grid Default 설정***
```js
{
    'Cfg'       : {
        'SelectionRowsMode'   : 1,    // GetSelectionRows 시 포커스행 포함 여부
        'MergeSheet'          : 8,	// msHeaderOnly + msFixedMerge
        'SearchMode'          : 4,    // 조회 처리 방법(실시간 서버 처리 페이징 모드)
        'AutoFitColWidth'     : 'init|search|resize',
        'Alternate'           : 1,
        'ExportMode'          : 2,
        'DeferredVScroll'     : 1,
        'UseHeaderActionMenu' : 1,
        'UseHeaderActionMode' : 1,
        'MaxSort'             : 1
    },
    'HeaderMode' : {
        'ColMove'     :1,
        'HeaderCheck' :1,
        'Sort'        :1,		// Sort 기능 사용
        'ColResize'   :1
    },
    'width'   : '100%',
    'height'  : '300px',
    'options' : {
        'page'  : {
            'use'            : false,
            'pageSize'       : 50,
            'pagingPosition' : 1,  // 0(사용 안함), 1(좌측), 2(우측)
            'countPosition'  : 4   // 0(사용 안함), 1(좌측상단), 2(우측상단), 3(좌측하단), 2(우측하단)
        }        
    }                
}
```

***Example***

```javascript
var grdFormatOption = {
    'Cols'  : [
        {'Type': 'Seq',   'SaveName': 'no',           'Width': 60,  'Header': 'NO'},
        {'Type': 'Text',  'SaveName': 'ctiLoginId',   'Width': 0,   'Header': '히든',     'Hidden': true} ,
        {'Type': 'Text',  'SaveName': 'userId',       'Width': 100, 'Header': '텍스트'} ,
        {'Type': 'Text',  'SaveName': 'userNm',       'Width': 100, 'Header': '히든2',    'Hidden': true} ,
        {'Type': 'Text',  'SaveName': 'formatYmdhms', 'Width': 150, 'Header': '년월일시분초', 'Format': 'yyyy-MM-dd HH:mm:ss'} ,
        {'Type': 'Text',  'SaveName': 'formatYmd',    'Width': 100, 'Header': '년월일',   'Format': 'yyyy-MM-dd'} ,
        {'Type': 'Text',  'SaveName': 'formatYm',     'Width': 80,  'Header': '년월',     'Format': 'yyyy-MM'} ,
        {'Type': 'Text',  'SaveName': 'formatHms',    'Width': 80,  'Header': '시분초',   'Format': 'Hms'} ,
        {'Type': 'Text',  'SaveName': 'formatHm',     'Width': 80,  'Header': '시분',     'Format': 'Hm'} ,
        {'Type': 'Text',  'SaveName': 'formatTel',    'Width': 80,  'Header': '전화번호', 'Format': 'PhoneNo'} ,
        {'Type': 'Int',   'SaveName': 'formatMoney',  'Width': 80,  'Header': '금액', 'AutoSum': true, 'SumType': 'Avg', 'Format': '#,##0'} ,
        {'Type': 'Text',  'SaveName': 'formatSecTime', 'Width': 80, 'Header': '초변환'} ,
        {'Type': 'Combo', 'SaveName': 'gradCode',     'Width': 100, 'Header': '콤보1', 'Edit': false, 'ComboCode': _UL.comp.getComboCodes('SYS007', 'code'), 'ComboText': _UL.comp.getComboCodes('SYS007', 'codeNm')} ,
        {'Type': 'Combo', 'SaveName': 'usePosblYn',   'Width': 100, 'Header': '콤보2', 'Edit': true, 'ComboCode': _UL.comp.getComboCodes('COM002', 'code', ['']), 'ComboText': _UL.comp.getComboCodes('COM002', 'codeNm', ['선택'])} ,
        {'Type': 'Image', 'SaveName': 'imgIndex',     'Width': 50,   'Header': '이미지'},
        {'Type': 'Int',   'SaveName': 'random1',      'Width': 100,  'Header': '랜덤1', 'AutoSum': true, 'SumType': 'Sum', 'Format': '#,##0'} ,
        {'Type': 'Int',   'SaveName': 'random2',      'Width': 100,  'Header': '랜덤2', 'AutoSum': true, 'SumType': 'Avg', 'Format': '#,##0'} ,
    ],
    'height'    : '330px',
    'options'    : {
        'page'    : {
            'use' : true,
            'pageSize' : 5
        }
    }        
};

_UL.comp.createGrid('grdFormat', grdFormatOption, true);

grdFormat.SetImageList(0,'/static/images/icon/help.gif');
grdFormat.SetImageList(1,'/static/images/icon/icon_play.gif');
grdFormat.SetImageList(2,'/static/images/icon/icon_save.gif');   
```

## Grid 컬럼 표시 방법 및 기타 설정

### 번호

Grid 의 번호 컬럼은 `Cols` 에 다음과 같이 정의합니다.

***Example***
```javascript
  'Cols' : [
    {'Type': 'Seq', 'SaveName': 'no', 'Width': 60,  'Header': 'NO'},
    ...
  ]
```

### Checkbox

Grid 의 Checkbox 컬럼은 `Cols` 에 다음과 같이 정의합니다.

***Example***
```javascript
  'Cols' : [
    {'Type': 'CheckBox', 'SaveName': 'chk', 'Width': 60,  'Header': ''},
    ...
  ]
```

### Combobox

Grid 의 Combobox 컬럼은 `Cols` 에 다음과 같이 정의합니다.

***Example***
```javascript
  'Cols' : [
    {'Type': 'Combo', 'SaveName': 'gradCode',  'Width': 100, 'Header': '콤보1',  'Edit': true, 'ComboCode': _UL.comp.getComboCodes('SYS007', 'code'),	'ComboText': _UL.comp.getComboCodes('SYS007', 'codeNm')} ,
    ...
  ]
```

Combo 컬럼을 생성하기 위한 `ComboCode`, `ComboText` 는 공통 Function 을 이용하여 정의합니다.

```javascript
_UL.comp.getComboCodes(clCode, col, addValue)
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
            <td>clCode</td>
            <td>String</td>
            <td>공통코드</td>
        </tr>
        <tr>
            <td>col</td>
            <td>String</td>
            <td>공통코드 목록에서 갸져올 컬럼 name (code: 코드값, codeNm: 코드명)</td>
        </tr>
        <tr>
            <td>addValue</td>
            <td>Array</td>
            <td>Combo 추가 데이터</td>
        </tr>
    </tbody>
</table>


***Example***

```javascript
_UL.comp.getComboCodes('SYS007', 'code')
_UL.comp.getComboCodes('SYS007', 'codeNm')

_UL.comp.getComboCodes('COM002', 'code', [''])
_UL.comp.getComboCodes('COM002', 'codeNm', ['선택'])
```

### Image

Grid 의 Image 컬럼은 `Cols` 에 다음과 같이 정의합니다.

```javascript
  'Cols' : [
    {'Type': 'Image', 'SaveName': 'imgIndex',  'Width': 50,  'Header': '이미지'},
    ...
  ]
```

Image 컬럼은 다음과 같이 IBShhet 의 [SetImageList](https://www.ibsheet.com/docs/ibsheet/IBSheet.html#SetImageList) Method 을 호출하여, 이미지에 대한 경로를 설정합니다.

```javascript
    Grid객체.SetImageList(index, path);
```

****Example****

```javascript
  grdFormat.SetImageList(0,'/static/images/icon/help.gif');
  grdFormat.SetImageList(1,'/static/images/icon/icon_play.gif');
  grdFormat.SetImageList(2,'/static/images/icon/icon_save.gif');
```

### Paging
Grid 의 Page 표시 설정을 합니다.<br />
페이지 표시여부 또는 페이지 표시 위치 변경은 아래와 같이 변경합니다. 

```js
'options'	: {
    'page'	: 페이지 설정 정보
}
```

***Property***  

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
            <td>use</td>
            <td>boolean</td>
            <td>페이지 사용여부 (Default false)</td>
        </tr>
        <tr>
            <td>pageSize</td>
            <td>Number</td>
            <td>페이지 사이즈 (Default 50)</td>
        </tr>
        <tr>
            <td>pagingPosition</td>
            <td>Number</td>
            <td>페이지 내비게이션 출력 위치 (Default 1)
              <ul>
                <li>0 (사용 안함)</li>
                <li>1 (좌측)</li>
                <li>2 (우측)</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td>countPosition</td>
            <td>Number</td>
            <td>건수정보 출력위치 (Default 4)
              <ul>
                <li>0 (사용 안함)</li>
                <li>1 (좌측상단)</li>
                <li>2 (우측상단)</li>
                <li>3 (좌측하단)</li>
                <li>4 (우측하단)</li>
              </ul>            
            </td>
        </tr>
    </tbody>
</table>

***Example***
```js
'options'	: {
    'page'	: {
        'use'            : true,
        'pageSize'       : 30,
        'pagingPosition' : 2,
        'countPosition'  : 3
    },
}
```

### Column Fix

Grid 에서 좌측 고정컬럼 처리를 위해 다음과 같이 설정합니다.

```js
'options'	: {
    'fixedCol'	: 고정컬럼 설정할 컬럼 개수
}
```

***Example***
```
'options'	: {
    'fixedCol'	: 2
}
```
