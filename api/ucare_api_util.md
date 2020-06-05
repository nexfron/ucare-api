# UCARE API
UCARE API에 대한 설명입니다.  

---

## Util

Data 관련 API 목록입니다.

### isEmpty

***Descrition***  
Data 의 값이 blank 여부를 반환합니다.

***Syntax***  
```js
_UL.util.isEmpty(data)
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
            <td>data</td>
            <td>String</td>
            <td>입력 데이터</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : boolean  
> 입력 데이터의 blank 여부를 반환

***Example***

```js
_UL.util.isEmpty(undefined);
// true

_UL.util.isEmpty(null);
// true

_UL.util.isEmpty("");
// true

_UL.util.isEmpty([]);
// true

_UL.util.isEmpty({});
// true
```
<br />

### assign

***Descrition***  
대상 Object 에 소스 Object 의 property(속성)를 복사(merge)하여 반환합니다.  
동일한 property(속성) 있는 경우, 소스 Object 의 값으로 복사 됩니다.

***Syntax***  
```js
_UL.util.assign(target, source)
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
            <td>target</td>
            <td>Object</td>
            <td>대상 Object</td>
        </tr>
        <tr>
            <td>source</td>
            <td>Object</td>
            <td>소스 Object</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 대상 Object 에 다른 Object 의 property(속성)을 복사(merge)하여 반환

***Example***

```js
_UL.util.assign({'name': 'smith'}, {'name': 'jun', 'age': 25});
// {name: "jun", age: 25}
```
<br />

### merge

***Descrition***  
대상 Object 에 소스 Object 의 property(속성)를 복사(merge)하여 반환합니다.  
assign 과 차이점은 Key 에 값이 Object 인 경우, 재귀적으로 병합(merge) 합니다.

***Syntax***  
```js
_UL.util.merge(target, source)
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
            <td>target</td>
            <td>Object</td>
            <td>대상 Object</td>
        </tr>
        <tr>
            <td>source</td>
            <td>Object</td>
            <td>소스 Object</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 대상 Object 에 다른 Object 의 property(속성)을 병합(merge)하여 반환

***Example***

```js
var sourceObj ={'id': 'juniweb', 'age': 22, 'language': {'java': true, 'javascript': false, 'jsp': false}};

_UL.util.merge(sourceObj, {'language': {'java': false, 'db': false}});
// {
//     'id'  :'juniweb',
//     'age' :22,
//     'language' : {
//                     'java'       :false,
//                     'javascript' :false,
//                     'jsp'        :false,
//                     'db'         :false
//                  }
// }

_UL.util.assign(sourceObj, {'language': {'java': false, 'db': false}});
// {
//     'id'  :'juniweb',
//     'age' :22,
//     'language' : {
//                     'java'       :false,
//                     'db'         :false
//                  }
// }
```
<br />

### cloneObject

***Descrition***  
대상 Object 를 깊은 복사(Deep copy) 하여 반환합니다.  

***Syntax***  
```js
_UL.util.cloneObject(obj)
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
            <td>obj</td>
            <td>Object</td>
            <td>대상 Object</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 대상 Object 를 깊은 복사(Deep copy) 하여 반환

***Example***

```js
// 얕은 복사(shallow copy)
var obj = {'name': 'jun', 'age': 25}; 
var shallowObj = obj;
shallowObj.age = 33;

console.log(obj);
// {'name': 'jun', 'age': 33}

// 깊은 복사(deep copy)
var deepObj = _UL.util.cloneObject(obj);
deepObj.age = 33

console.log(obj);
// {'name': 'jun', 'age': 25}
```
<br />

### getNumber

***Descrition***  
Data 에서 숫자만 추출하여 반환합니다.

***Syntax***  
```js
_UL.util.getNumber(str)
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
            <td>str</td>
            <td>String</td>
            <td>입력 데이터</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 데이터에서 숫자만 추출하여 반환

***Example***

```js
_UL.util.getNumber("1a2b3c4d5e");
// 12345
```
<br />

### checkEnterKey

***Descrition***  
Key event keycode 가 `enter` 여부를 확인하여 callback 함수를 호출합니다. 

***Syntax***  
```js
_UL.util.checkEnterKey(cb)
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
            <td>cb</td>
            <td>Object</td>
            <td>enter 입력 시 호출할 callback 함수</td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```html
<input type="text" id="custNm" onkeypress="_UL.util.checkEnterKey(searchList)" />

<script>
function searchList() {
    ...
}
</script>
```
<br />

### getFileExtension

***Descrition***  
파일명에서 확장자를 반환합니다.

***Syntax***  
```js
_UL.util.getFileExtension(filename)
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
            <td>filename</td>
            <td>String</td>
            <td>파일명</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 파일명에서 확장자를 반환

***Example***

```js
_UL.util.getFileExtension("테스트.xlsx");
// xlsx
```
<br />

### getBytesToSize

***Descrition***  
파일 사이즈를 크기 단위로 반환합니다.

***Syntax***  
```js
_UL.util.getBytesToSize(bytes)
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
            <td>bytes</td>
            <td>Number</td>
            <td>파일사이즈 (bytes)</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 파일사이즈 (bytes) 를 크기 단위에 맞게 계산하여 반환

***Example***

```js
_UL.util.getBytesToSize(20000);
// 20 KB

_UL.util.getBytesToSize(300000000);
// 286 MB
```
<br />

### isFileType

***Descrition***  
파일 확장자가 체크 파일 타입에 맞는지 여부를 반환합니다.

***Syntax***  
```js
_UL.util.isFileType(fileType, fileName)
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
            <td>fileType</td>
            <td>String</td>
            <td>파일확장자 목록. 구분자 (|)</td>
        </tr>
        <tr>
            <td>fileName</td>
            <td>String</td>
            <td>파일명</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : boolean  
> 입력 파일명이 체크 대상 파일 확장자에 부합하는지 여부를 반환

***Example***

```js
_UL.util.isFileType("csv|xls", "test.csv");
// true

_UL.util.isFileType("xlsx|xls", "test.csv");
// false
```
<br />