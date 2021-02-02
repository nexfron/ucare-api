# UCARE API
UCARE API에 대한 설명입니다.  

---

## file

File Upload 관련 API 목록입니다.

### render

***Descrition***
Dom에 File Element를 렌더링하고 파일 정보 배열을 반환한다.

***Syntax***
```js
_UL.file.render(name)
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
            <td>대상 element name</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object Array
> 해당 name Element의 Dataset 정보를 Object Array로 반환

***Example***
```html
<table>
    <tr>
        <th>WBS</th>
        <td colspan="3">
            <input type="hidden" id="atchmnflMangeNo_wbs" name="atchmnflMangeNo_wbs" value="">
            <div id="wbs" name="fileForm" data-id="wbs" data-readonly="false" data-multiple="true" data-size="${ uploadSize }" data-exts="${ uploadExt }" data-updateAtchFile="0"/>
        </td>
    </tr>
    <tr>
        <th>RFP</th>
        <td colspan="3">
            <input type="hidden" id="atchmnflMangeNo_rfp" name="atchmnflMangeNo_rfp" value="">
            <div id="rfp" name="fileForm" data-id="rfp" data-readonly="false" data-multiple="true" data-size="${ uploadSize }" data-exts="${ uploadExt }" data-updateAtchFile="0"/>
        </td>
    </tr>
    <tr>
        <th>ERD</th>
        <td colspan="3">
            <input type="hidden" id="atchmnflMangeNo_erd" name="atchmnflMangeNo_erd" value="">
            <div id="erd" name="fileForm" data-id="erd" data-readonly="false" data-multiple="true" data-size="${ uploadSize }" data-exts="${ uploadExt }" data-updateAtchFile="0"/>
        </td>
    </tr>
</table>

<script>
_upg.fileFormOptions = [];

_upg.fileFormOptions = _UL.file.render('fileForm');

<!--
    _upg.fileFormOptions = [
        {id: "wbs",readonly: "false",multiple: "true",size: "10",exts: "",updateatchfile: "0"},
        {id: "rfp",readonly: "false",multiple: "true",size: "10",exts: "",updateatchfile: "0"},
        {id: "erd",readonly: "false",multiple: "true",size: "10",exts: "",updateatchfile: "0"}
    ];
-->
</script>
```
<img src="https://user-images.githubusercontent.com/53248875/106558253-c5879a00-6566-11eb-8e29-a544ce37ae58.PNG" width="100" height="100">

### clearFileList

***Descrition***
File 정보 및 파일 목록을 삭제합니다.

***Syntax***
```js
_UL.file.clearFileList(id)
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
            <td>대상 element dataset id</td>
        </tr>
    </tbody>
</table>

***Example***
```html
<div id="wbs" name="fileForm" data-id="wbs" data-readonly="false" data-multiple="true" data-size="10" data-exts="" data-updateAtchFile="0"/>

<script>
_UL.file.clearFileList('wbs');
</script>
```

### setFileList

***Description***
파일 목록에 Upload File 추가합니다.

***Syntax***
```js
_UL.file.setFileList(id, fileList);
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
            <td>대상 element dataset id</td>
        </tr>
        <tr>
            <td>fileList</td>
            <td>Object Array</td>
            <td>파일 정보 Object 배열</td>
        </tr>
    </tbody>
</table>

***Example***
```html
<table>
    <tr>
        <th>WBS</th>
        <td colspan="3">
            <input type="hidden" id="atchmnflMangeNo_wbs" name="atchmnflMangeNo_wbs" value="">
            <div id="wbs" name="fileForm" data-id="wbs" data-readonly="false" data-multiple="true" data-size="${ uploadSize }" data-exts="${ uploadExt }" data-updateAtchFile="0"/>
        </td>
    </tr>
    <tr>
        <th>RFP</th>
        <td colspan="3">
            <input type="hidden" id="atchmnflMangeNo_rfp" name="atchmnflMangeNo_rfp" value="">
            <div id="rfp" name="fileForm" data-id="rfp" data-readonly="false" data-multiple="true" data-size="${ uploadSize }" data-exts="${ uploadExt }" data-updateAtchFile="0"/>
        </td>
    </tr>
    <tr>
        <th>ERD</th>
        <td colspan="3">
            <input type="hidden" id="atchmnflMangeNo_erd" name="atchmnflMangeNo_erd" value="">
            <div id="erd" name="fileForm" data-id="erd" data-readonly="false" data-multiple="true" data-size="${ uploadSize }" data-exts="${ uploadExt }" data-updateAtchFile="0"/>
        </td>
    </tr>
</table>

<script>
_UL.net.post("/smp/file/smpFileSrch.do", param, function(response) {
    
    var resultData = response.result.data;

    // 첨부파일 Setting
    if (!_UL.util.isEmpty(resultData.formFiles)) {
        _.map(resultData.formFiles, function(value, key){
            if(Array.isArray(value)) {
                _UL.page.set("atchmnflManageNo_"+ key, resultData['atchmnflManageNo_'+ key]);
                _UL.file.setFileList(key, value); // 첨부파일 목록 Set
            } else {
                _UL.file.clearFileList(key);
            }
        });
    }
});
</script>
```

### getFormData

***Description***
Upload 할 파일 정보를 FormData 객체에 담아 반환한다.

***Syntax***
```js
_UL.file.getFormData(fileOptions, formData);
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
            <td>fileOptions</td>
            <td>Object Array</td>
            <td>File Dataset Array</td>
        </tr>
        <tr>
            <td>formData</td>
            <td>Object</td>
            <td>FormData 객체</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object
> 파일 업로드를 위해 업로드 대상 파일 정보를 FormData에 담아 반환.

***Example***
```html
<script>
function fnSaveData(){
    var formData = new FormData();

    // 파일 정보 FormData에 담기
    formData = _UL.file.getFormData(_upg.fileFormOptions, formData);
    formData.append('fileFormOption', JSON.stringify(_upg.fileFormOptions));

    _UL.net.upload('/smp/file/smpFileSave.do', formData, function(response) {
        console.log(">> smpFile.fnSaveData ", response);
        _UL.mssg.alert(UCG.MSG.Success);
        fnInit();
    },{'progress': false});
}
</script>
```