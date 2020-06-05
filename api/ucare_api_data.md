# UCARE API
UCARE API에 대한 설명입니다.  

---

## Data

Data 관련 API 목록입니다.

### mask

***Descrition***  
Data 를 Format 맞게 mask 처리 하여 반환합니다.

***Syntax***  
```js
_UL.data.mask(data, maskType)
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
        <tr>
            <td>maskType</td>
            <td>String</td>
            <td>format 타입
                <ul>
                  <li>DATE : 년월일 (8자리 또는 14자리 - YYYY-MM-DD) 또는 년월일 (6자리 - YYYY-MM) 형식 반환</li>
                  <li>DATETIME : 년월일시분초 (YYYY-MM-DD HH:mm:ss) 형식 반환</li>
                  <li>SEC : 초 (Seconds) 를 계산하여 시분초 (HH:mm:ss) 형식 반환</li>
                  <li>TEL : 전화번호 (010-0000-0000) 형식 반환</li>
                  <li>MONEY : 금액 (comma) 형식 반황</li>
                  <li>SSN : 주민등록번호(000000-0******) 형식 반환. 뒤 6자리 * 처리</li>
                  <li>TIME : 시분초 (6자리 - HH:mm:ss) 또는 시분 (4자리 - HH:mm) 형식 반환</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 데이터를  format 형식에 맞게  masking 처리하여 반환

***Example***

```js
_UL.data.mask("20200605", "DATE");
// 2020-06-05
_UL.data.mask("20200605121314", "DATE");
// 2020-06-05
_UL.data.mask("202006", "DATE");
// 2020-06
_UL.data.mask("20200605121314", "DATETIME");
// 2020-06-05 12:13:14
_UL.data.mask("115", "SEC");
// 00:01:55
_UL.data.mask("0212345678", "TEL");
// 02-1234-5678
_UL.data.mask("01012345678", "TEL");
// 010-1234-5678
_UL.data.mask("1234567", "MONEY");
// 1,234,567
_UL.data.mask("1234567890123", "SSN");
// 123456-7******
_UL.data.mask("121314", "TIME");
// 12:13
_UL.data.mask("1213", "TIME");
// 12:13:14
```
<br />

### removeMask

***Descrition***  
Data 에서 특수문자를 제거하여 반환합니다.

***Syntax***  
```js
_UL.data.removeMask(data)
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
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 데이터에서 특수문자를  제거하여 반환

***Example***

```js
_UL.data.removeMask("1!2@3#4$5%6^7&8*9(0)1-2=a[b]c");
// 123456789012abc
```
<br />

### removeTag

***Descrition***  
데이터의 HTML Tag를 제외한 내용을 반환합니다.

***Syntax***  
```js
_UL.data.removeTag(data)
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
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 데이터 의 HTML Tag를 제외한 내용을 반환

***Example***

```js
_UL.data.removeTag("<span>테스트</span><p>테스트2</p>");
// "테스트테스트2"
```
<br />

### decodeHTML

***Descrition***  
데이터의 HTML 코드를 decode 하여 반환합니다.

***Syntax***  
```js
_UL.data.decodeHTML(data)
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
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 데이터 의 HTML 코드를 Decode 하여 반환

***Example***

```js
_UL.data.decodeHTML("&lt;span&gt;테스트&lt;&sol;span&gt;");
// <span>테스트</span>
```
<br />

### isTermDate

***Descrition***  
두 날짜의 Validation 을 체크하여 반환합니다.

***Syntax***  
```js
_UL.data.isTermDate(fromDate, toDate, dateFormat)
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
            <td>fromDate</td>
            <td>String</td>
            <td>시작일자</td>
        </tr>
        <tr>
            <td>toDate</td>
            <td>String</td>
            <td>종료일자</td>
        </tr>
        <tr>
            <td>dateFormat</td>
            <td>String</td>
            <td>날짜 format (Default YYYYMMDD)</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : boolean  
> 두 날짜(시작일자, 종료일자) 의 Validaion 을 체크하여 반환 (true: valid, false: invalid)

***Example***

```js
_UL.data.isTermDate('20200501', '20200507');
// true

_UL.data.isTermDate('20200507', '20200501');
// false
```
<br />

### checkTermDate

***Descrition***  
두 시간 데이터의 Validation 을 체크하여 반환합니다.

***Syntax***  
```js
_UL.data.checkTermDate(fromDateId, toDateId, direction)
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
            <td>fromDateId</td>
            <td>String</td>
            <td>시작 Date element id</td>
        </tr>
        <tr>
            <td>toDateId</td>
            <td>String</td>
            <td>종료 Date element id</td>
        </tr>
        <tr>
            <td>direction</td>
            <td>String</td>
            <td>입력 날짜 단위 (Default D)
                <ul>
                  <li>Y : 년도 (Year)</li>
                  <li>M : 월 (Month)</li>
                  <li>D : 일자 (Day)</li>
                  <li>T : 시간 (Time)</li>
                </ul>            
            </td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 두 시간 데이터(시작, 종료) 의 Validaion 을 체크하여 반환 (true: valid, false: invalid)

***Example***

```js
<input id="startDay" type="text" class="datepicker-here" data-cmp-type="CLND" data-format="DATE" value="20200507" />
~
<input id="endDay" type="text" class="datepicker-here" data-cmp-type="CLND" data-format="DATE" value="20200501" />

<script>
_UL.data.checkTermDate('startDay', 'endDay', 'D')
// false
</script>

```
<br />

### isValid

***Descrition***  
Element 그룹의 데이터 값의 필수 값을 체크하여 반환합니다.  
`data-required` 값이 true 인 element 만 Validation 을 체크합니다.

***Syntax***  
```js
_UL.data.isValid(id)
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
            <td>대상 그룹 id</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : boolean  
> 그룹 element (input, hidden, select, textarea, radio, checkbox) 의 값의 Validation 을 체크하여 반환 (true: valid, false: invalid)

***Example***

```js
<input type="text" id="userNm" value="" data-group-id="gpDtl" data-required="true" data-requirednm="사용자명" />

<script>
_UL.data.isValid('gpDtl');
// false
</script>
```
<br />

### defaultString

***Descrition***  
Data 의 값이 null 인 경우, default 값을 반환합니다.

***Syntax***  
```js
_UL.data.defaultString(data, defalutValue)
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
        <tr>
            <td>defalutValue</td>
            <td>String</td>
            <td>Default 값</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 데이터가 빈값(''), null, undefined 인 경우, default 값을 반환

***Example***

```js
var data1 = ''; // blank
_UL.data.defaultString(data1,'TEST');
// TEST
var data2 = null; // null
_UL.data.defaultString(data2,'TEST');
// TEST
var data3; // undefined
_UL.data.defaultString(data3,'TEST');
// TEST
```
<br />

### getByteLengthOfUtf8

***Descrition***  
데이터의 byte length 를 계산하여 반환합니다.
한글 `3` byte (UTF-8) 로 계산합니다.

***Syntax***  
```js
_UL.data.getByteLengthOfUtf8(str)
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
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> UTF-8 인코딩에서 한글 `3` 바이트로 계산하여 문자열의 길이를 반환

***Example***

```js
_UL.data.getByteLengthOfUtf8('abcde');
// 5
_UL.data.getByteLengthOfUtf8('가나다라마');
// 15
```
<br />

### getByteLengthOfEuckr

***Descrition***  
데이터의 byte length 를 계산하여 반환합니다.
한글 `2` byte (EUC-KR) 로 계산합니다.

***Syntax***  
```js
_UL.data.getByteLengthOfEuckr(str)
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
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> EUC-KR 인코딩에서 한글 `2` 바이트로 계산하여 문자열의 길이를 반환

***Example***

```js
_UL.data.getByteLengthOfEuckr('abcde');
// 5
_UL.data.getByteLengthOfEuckr('가나다라마');
// 10
```
<br />
