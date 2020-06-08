# UCARE API
UCARE API에 대한 설명입니다.  

---

## net

net 관련 API 목록입니다.

### post

***Descrition***  
서버에 `POST` 방식의 Request 요청을 합니다.  
Request 요청이 성공하면, callback 함수를 호출하고, 실패하면 error message 를 표시하고 callbakc 함수를 호출하지 않습니다.

***Syntax***  
```js
_UL.net.post(url, data, callback, options)
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
            <td>url</td>
            <td>String</td>
            <td>요청(request) URL</td>
        </tr>
        <tr>
            <td>data</td>
            <td>Object</td>
            <td>요청 데이터 Object (json)</td>
        </tr>
        <tr>
            <td>callback</td>
            <td>Object</td>
            <td>요청(request) 성공(success) 후, 호출할 callback 함수</td>
        </tr>
        <tr>
            <td>options</td>
            <td>Object</td>
            <td>ajax 호출 시, 처리하는 option 
                <ul>
                  <li>progress : Progress Bar 표시여부. (Default true) <br /> true: 표시, false: 미표시</li>
                  <li>dialog : 메시지 표시 방식. (Default false) <br /> true: alert 방식, false: div 방식</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```js
var url = "/sys/user/selectUser.do";
var param= {
    'userId' : 'john'
}

_UL.net.post(url, param, function(response) {
    console.log(response);
    ...
});
```
<br />

### upload

***Descrition***  
서버에 File Upload 를 위한 `multipart/form-data` Request 요청을 합니다.  
Request 요청이 성공하면, callback 함수를 호출하고, 실패하면 error message 를 표시하고 callbakc 함수를 호출하지 않습니다.

***Syntax***  
```js
_UL.net.fnUpload(url, data, callback, options)
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
            <td>url</td>
            <td>String</td>
            <td>요청(request) URL</td>
        </tr>
        <tr>
            <td>data</td>
            <td>Object</td>
            <td>요청 데이터 Object (FormData)</td>
        </tr>
        <tr>
            <td>callback</td>
            <td>Object</td>
            <td>요청(request) 성공(success) 후, 호출할 callback 함수</td>
        </tr>
        <tr>
            <td>options</td>
            <td>Object</td>
            <td>ajax 호출 시, 처리하는 option 
                <ul>
                  <li>progress : Progress Bar 표시여부. (Default true) <br /> true: 표시, false: 미표시</li>
                  <li>dialog : 메시지 표시 방식. (Default false) <br /> true: alert 방식, false: div 방식</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

***Return***

***Example***

```js
var formData = new FormData();
var url = "/kms/knwldg/saveKnwldg.do";
var param= {
    'knwldgTitle'  : '테스트 상담지식',
    'knwldgCnText' : '테스트 내용'
}

_upg.file.setFileListToFormData(formData, "atchFiles");

formData.append("data", JSON.stringify(param));
formData.append("atchFileInfoList", JSON.stringify(_upg.file.getFileList()));

_UL.net.upload(url, formData, function(response) {
    console.log(response);
});
```
<br />


## mssg

message 관련 API 목록입니다.

### alert

***Descrition***  
alert 메시지를 표시합니다.
`OK` 를 클릭하면 callback 함수를 호출합니다.

***Syntax***  
```js
_UL.mssg.alert(msg, cb)
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
            <td>msg</td>
            <td>String</td>
            <td>메시지</td>
        </tr>
        <tr>
            <td>cb</td>
            <td>String</td>
            <td>OK 버튼 클릭 후, 호출할 callback 함수</td>
        </tr>
    </tbody>
</table>

***Return***


***Example***

```js
_UL.mssg.alert("사용자명을 입력하세요", function(){
    _UL.page.setFocus("userNm");
});
```
<br />

### confirm

***Descrition***  
confirm 메시지를 표시합니다.  
`확인` 를 클릭하면 callback 함수를 호출합니다.

***Syntax***  
```js
_UL.mssg.confirm(msg, cb)
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
            <td>msg</td>
            <td>String</td>
            <td>메시지</td>
        </tr>
        <tr>
            <td>cb</td>
            <td>String</td>
            <td>OK 버튼 클릭 후, 호출할 callback 함수</td>
        </tr>
    </tbody>
</table>

***Return***


***Example***

```js
_UL.mssg.confirm("저장 하시겠습니까?", function(){
    var url = "/sys/user/insertUser.do";
    var param = {
        'userId' : 'smith',
        'userNm' : '홍길동'
    };
    _UL.net.post(url, param, function(response){
        console.log(response);
    });
});
```
<br />

### error

***Descrition***  
error 메시지를 표시합니다.
`OK` 를 클릭하면 callback 함수를 호출합니다.

***Syntax***  
```js
_UL.mssg.error(msg, cb)
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
            <td>msg</td>
            <td>String</td>
            <td>메시지</td>
        </tr>
        <tr>
            <td>cb</td>
            <td>String</td>
            <td>OK 버튼 클릭 후, 호출할 callback 함수</td>
        </tr>
    </tbody>
</table>

***Return***


***Example***

```js
_UL.mssg.error("사용자명을 입력하세요", function(){
    console.log("Error Message Callback");
});
```
<br />