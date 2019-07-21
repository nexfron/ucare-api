# Grid
Grid 생성 및 속성을 설명입니다.

---

## Grid Div 생성

Grid Container 가 생성될 위치에 아래와 같은 div Tag 를 작성합니다.<br/>
`data-codes` 는 Option 이며, Grid 에 Combo 가 포함될 경우, JSON Object 로 정의합니다.


```html
<div id="GridId" data-codes="코드 Object"></div>
```
  - **id** : Grid 객체 Id
  - **data-codes (_Option_)** : Combo 생성 코드 Object. 공통코드 를 Object key 로 정의 합니다.

***Example***

```html
<div id="UCBIZ005S" data-codes="{'TST001':${TST001},'TST002':${TST002}}"></div>
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

  - **gridId** : Grid 생성 Id
  - **gridOption** : Grid 생성 옵션
    - **gridOption[Cfg] (Option)** : Grid 에 기본 속성을 설정.
    - **gridOption[HeaderMode] (Option)** : Grid 의 Header 속성을 설정.
    - **gridOption[Cols]** : Grid 컬럼 속성을 설정.
    - **gridOption[width] (Option)**: Grid 의 너비를 설정. (Default 100%)
    - **gridOption[height]** : Grid 의 높이를 설정. (Default 300px)
    - **gridOption[event] (Option)** : Grid 에서 사용하는 Event 사용여부. Grid 의 Event 중 `OnClick`, `OnDblClick`, `OnAfterEdit` 만 지원합니다.

***Grid Default 설정***
```js
{
    'Cfg'			: {
        'SelectionRowsMode'		: 1,
        'MergeSheet'			: 8,				// msHeaderOnly + msFixedMerge
        'SearchMode'			: 4,
        'AutoFitColWidth'		: 'search|resize',
        'Alternate'				: 1,
        'ExportMode'			: 2,
        'DeferredVScroll'		: 1,
        'UseHeaderActionMenu'	: 1,
        'UseHeaderActionMode'	: 1,
        'MaxSort'				: 1,
    },
    'HeaderMode'	: {
        'ColMove'		:1,
        'HeaderCheck'	:1,
        'Sort'			:1,		// Sort 기능 사용
        'ColResize'		:1
    },
    'width'			: '100%',
    'height'		: '300px',
    'event'		: {
        'click'     : false,
        'dbclick'   : false,
        'afteredit' : false,
    },                
    'options'	: {
        'page'	: {
            'use'			  : true,
            'pagingPosition'  : 1,
            'countPosition'	  : 4
        },

    }                
}
```

***Example***

```javascript
function init()
{

	var gridInfo = {
		'Cfg'			: {
			'SearchMode': 2,
			'MergeSheet': 5			
		},
		'Cols'		: [
			{'Type': 'Seq',		'SaveName': 'no',				  'Width': 60,	'Header': 'NO'},
			{'Type': 'Text',	'SaveName': 'todo_type',	'Width': 0,		'Header': '히든',			'Hidden': true} ,
			{'Type': 'Text',	'SaveName': 'user_id',		'Width': 50,	'Header': '텍스트'} ,
			{'Type': 'Text',	'SaveName': 'reg_datet',	'Width': 150,	'Header': '년월일시분초',	'Format': 'yyyy-MM-dd HH:mm:ss'} ,
			{'Type': 'Text',	'SaveName': 'reg_dt',			'Width': 100,	'Header': '년월일',			'Format': 'yyyy-MM-dd'} ,
			{'Type': 'Text',	'SaveName': 'reg_month',	'Width': 80,	'Header': '년월',			'Format': 'yyyy-MM'} ,
			{'Type': 'Text',	'SaveName': 'reg_hms',		'Width': 80,	'Header': '시분초',			'Format': 'Hms'} ,
			{'Type': 'Text',	'SaveName': 'reg_hm',			'Width': 80,	'Header': '시분',			'Format': 'Hm'} ,
			{'Type': 'Combo',	'SaveName': 'todo_type',	'Width': 100,	'Header': '콤보1',			'Edit': true,	'ComboCode': _UL.comp.getComboCodes('UCSMP012S', 'TST001', 'cd'),	'ComboText': _UL.comp.getComboCodes('UCSMP012S', 'TST001', 'cd_nm')} ,
			{'Type': 'Combo',	'SaveName': 'status',			'Width': 100,	'Header': '콤보2',			'Edit': true,	'ComboCode': _UL.comp.getComboCodes('UCSMP012S', 'TST002', 'cd'),	'ComboText': _UL.comp.getComboCodes('UCSMP012S', 'TST002', 'cd_nm')} ,
			{'Type': 'Image',	'SaveName': 'img_index',	'Width': 50,	'Header': '이미지'},
			{'Type': 'Text',	'SaveName': 'random1',		'Width': 100,	'Header': '랜덤1', 'AutoSum': true, 'SumType': 'Sum', 'Format': '#,##0'} ,
			{'Type': 'Text',	'SaveName': 'random2',		'Width': 100,	'Header': '랜덤2', 'AutoSum': true, 'SumType': 'Avg', 'Format': '#,##0'} ,
		],
		'height'	: '430px',
		'event'		: {
			'click' : true
		}
	};

	_UL.comp.createGrid('UCSMP012S', gridInfo);
}
```

## Grid 컬럼 표시 방법 및 기타 설정

### 번호

Grid 의 번호 컬럼은 `Cols` 에 다음과 같이 정의합니다.

```javascript
  'Cols' : [
    {'Type': 'Seq', 'SaveName': 'no', 'Width': 60,  'Header': 'NO'},
    ...
  ]
```

### Checkbox

Grid 의 Checkbox 컬럼은 `Cols` 에 다음과 같이 정의합니다.

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
    {'Type': 'Combo', 'SaveName': 'todo_type',  'Width': 100, 'Header': '콤보1',  'Edit': true, 'ComboCode': _UL.comp.getComboCodes('UCSMP012S', 'TST001', 'cd'),	'ComboText': _UL.comp.getComboCodes('UCSMP012S', 'TST001', 'cd_nm')} ,
    ...
  ]
```

Combo 컬럼을 생성하기 위한 `ComboCode`, `ComboText` 는 공통 Function 을 이용하여 정의합니다.

```javascript
_UL.comp.getComboCodes(gridId, code, key)
```
  - **gridId** : Grid Id
  - **code** : 공통코드
  - **key** : Object에서 가져올 key

> Combo 컬럼을 정의하기 위해서는 Grid 의 `div` 에서 **data-codes** 는 **필수** 입니다. 

***Example***

```javascript
_UL.comp.getComboCodes('UCSMP012S', 'TST001', 'cd')
```
예제의 경우, id 가 `UCSMP012S` 를 가지는 **div** 의 **data-codes** 의 Object 에서 `TST001` Object 의 `cd` 를 가져옵니다.

### Image

Grid 의 Image 컬럼은 `Cols` 에 다음과 같이 정의합니다.

```javascript
  'Cols' : [
    {'Type': 'Image', 'SaveName': 'img_index',  'Width': 50,  'Header': '이미지'},
    ...
  ]
```

Image 컬럼은 다음과 같이 IBShhet 의 Function 을 호출하여, 이미지에 대한 경로를 설정합니다.

```javascript
    gridView[gridId].SetImageList(index, path);
```
  - **gridId** : Grid Id
  - **index** : 이미지 Index
  - **path** : 이미지 Path

****Example****

```javascript
  gridView['UCSMP012S'].SetImageList(0,'/images/icon/help.gif');
  gridView['UCSMP012S'].SetImageList(1,'/images/icon/icon_play.gif');
  gridView['UCSMP012S'].SetImageList(2,'/images/icon/icon_save.gif');	
```

### Page
Grid 의 Page 표시는 기본으로 표시됩니다. (좌측: 페이지 Navigation, 우측: 페이지 Count) <br />
페이지 표시여부 또는 페이지 표시 위치 변경은 아래와 같이 변경합니다. 

```js
'options'	: {
    'page'	: {
        'use'			  : 페이지 사용여부,
        'pagingPosition'  : 페이지 내비게이션 출력 위치,
        'countPosition'	  : 건수정보 출력위치
    },
}
```

***Example***
```js
'options'	: {
    'page'	: {
        'use'			  : true,
        'pagingPosition'  : 2,
        'countPosition'	  : 3
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
위의 경우 좌측에서 2개의 컬럼이 고정 처리됩니다.
