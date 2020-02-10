# UCARE API
UCARE API에 대한 설명입니다.  

---

## page

Page 관련 API 목록입니다.

### get

***Descrition***  
설명

***Syntax***  
```js
_UL.page.get(id)
```

***Parameters***
> <span style="color:green; font-weight:bold;">id</span>  
> Type : String  
> id 의 값(value)을 반환

***Return***
> Type : String / Array  
> input, select, textarea, radio 는 String 을 반환, checkbox 는 Array 를 반환

***Example***

```html
<input type="text" data-format="DATET" data-enter="searchList" />
```
<br />
