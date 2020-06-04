# UCARE API
UCARE API에 대한 설명입니다.  

---

## page

Page 관련 API 목록입니다.

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
            <td>id 의 값(value)을 반환</td>
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
