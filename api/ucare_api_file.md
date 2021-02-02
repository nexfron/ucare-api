# UCARE API
UCARE API에 대한 설명입니다.  

---

## file

File Upload 관련 API 목록입니다.

### render

***Descrition***
Dom에 File Element를 렌더링합니다.

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