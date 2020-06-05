# UCARE API
UCARE API에 대한 설명입니다.  

---

## Date

Date 관련 API 목록입니다.

### getDate

***Descrition***  
기준 날짜를 format 형태로 반환합니다.

***Syntax***  
```js
_UL.date.getDate(outformat, data, informat)
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
            <td>outformat</td>
            <td>String</td>
            <td>output 날짜 format (Default YYYYMMDD)</td>
        </tr>
        <tr>
            <td>data</td>
            <td>String</td>
            <td>입력 날짜 데이터 (Default 현재 시간)</td>
        </tr>
        <tr>
            <td>informat</td>
            <td>String</td>
            <td>input 날짜 format</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 날짜를 output format 형태로 반환

***Example***

```js
_UL.date.getDate();
// 20200505

_UL.date.getDate('YYYY-MM-DD');
// 2020-05-05

_UL.date.getDate('YYYY-MM-DD HH:mm:ss');
// 2020-06-05 14:52:19

_UL.date.getDate('HH:mm:ss');
// 14:52:27

_UL.date.getDate('YYYY-MM-DD', '20200501', 'YYYYMMDD');
// 2020-05-01
```
<br />

### addDate

***Descrition***  
기준 날짜에서 날짜를 계산하여 format 형태로 반환합니다.

***Syntax***  
```js
_UL.date.addDate(outformat, value, direction, data, informat)
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
            <td>outformat</td>
            <td>String</td>
            <td>output 날짜 format (Default YYYYMMDD)</td>
        </tr>
        <tr>
            <td>value</td>
            <td>String</td>
            <td>계산할 값</td>
        </tr>
        <tr>
            <td>direction</td>
            <td>String</td>
            <td>날짜 단위
                <ul>
                  <li>Y : 년 (Year)</li>
                  <li>M : 월 (Month)</li>
                  <li>d : 일 (Day)</li>
                  <li>h : 시 (Hour)</li>
                  <li>m : 분 (Minute)</li>
                  <li>s : 초 (Second)</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>data</td>
            <td>String</td>
            <td>입력 날짜 데이터 (Default 현재 시간)</td>
        </tr>
        <tr>
            <td>informat</td>
            <td>String</td>
            <td>input 날짜 format</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 기준 날짜에서 추가 날짜를 계산하여 format 형태로 반환합니다.

***Example***
```js
_UL.date.getDate('YYYY-MM-DD HH:mm:ss');
// 2020-05-05 15:00:30

_UL.date.addDate('YYYY-MM-DD HH:mm:ss', 2, 'D');
// 2020-05-07 15:00:30

_UL.date.addDate('YYYY-MM-DD HH:mm:ss', 2, 'M');
// 2020-07-05 15:00:30

_UL.date.addDate('YYYY-MM-DD HH:mm:ss', 2, 'M');
// 2020-07-05 15:00:30

_UL.date.addDate('YYYY-MM-DD HH:mm:ss', 2, 'M', '20200507121314', 'YYYYMMDDHHmmss');
// 2020-07-07 12:13:14
```
<br />

### getDay

***Descrition***  
기준 날짜의 요일을 반환합니다.

***Syntax***  
```js
_UL.date.getDay(data, informat)
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
            <td>입력 날짜 데이터 (Default 현재 시간)</td>
        </tr>
        <tr>
            <td>informat</td>
            <td>String</td>
            <td>input 날짜 format</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Number  
> 날짜를 요일을 숫자로 반환   
> 일(0), 월(1), 화(2), 수(3), 목(4), 금(5), 토(6) 

***Example***

```js
_UL.data.getDay();
// 2 (2020-05-05)

_UL.date.getDay('20200508','YYYYMMDD');
// 5 (2020-05-08)
```
<br />

### getDayKo

***Descrition***  
기준 날짜의 요일을 한글명으로 반환합니다.

***Syntax***  
```js
_UL.date.getDayKo(data, informat)
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
            <td>입력 날짜 데이터 (Default 현재 시간)</td>
        </tr>
        <tr>
            <td>informat</td>
            <td>String</td>
            <td>input 날짜 format</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Number  
> 날짜를 요일을 한글명(short)으로 반환   

***Example***

```js
_UL.data.getDayKo();
// 화 (2020-05-05)

_UL.date.getDay('20200508','YYYYMMDD');
// 금 (2020-05-08)
```
<br />

### getDaysInMonth

***Descrition***  
기준 날짜의 달력(Month)에서 마지막 일자를 반환합니다.

***Syntax***  
```js
_UL.date.getDaysInMonth(data, informat)
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
            <td>입력 날짜 데이터 (Default 현재 시간)</td>
        </tr>
        <tr>
            <td>informat</td>
            <td>String</td>
            <td>input 날짜 format</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 날짜의 월(Month) 에서 마지막 일을 반환

***Example***

```js
UL.date.getDaysInMonth();
// 31

UL.date.getDaysInMonth('20200603','YYYYMMDD');
// 30
```
<br />

### getDateAndDay

***Descrition***  
기준 날짜의 일자와 요일을 반환합니다.  
입력 data(일자) 는 8자리 (YYYYMMMDD) 형태를 가지고 있어야 합니다. 
8자리가 아닌 경우, 현재일자를 반환합니다.

***Syntax***  
```js
_UL.date.getDateAndDay(data)
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
            <td>입력 날짜 데이터 (Default 현재 시간)</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 날짜의 일자와 요일을 반환

***Example***

```js
_UL.data.getDateAndDay();
// 2020-05-05 (화)

_UL.data.getDateAndDay('20200507');
// 2020-05-07 (목)
```
<br />

### diffDate

***Descrition***  
두 날짜의 차이를 계산하여 반환합니다.

***Syntax***  
```js
_UL.date.diffDate(toDate, toFormat, fromDate, fromFormat, direction)
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
            <td>toDate</td>
            <td>String</td>
            <td>종료 날짜 데이터</td>
        </tr>
        <tr>
            <td>toFormat</td>
            <td>String</td>
            <td>종료 날짜 format (Default YYYYMMDD)</td>
        </tr>
        <tr>
            <td>fromDate</td>
            <td>String</td>
            <td>시작 날짜 데이터</td>
        </tr>
        <tr>
            <td>fromFormat</td>
            <td>String</td>
            <td>시작 날짜 format (Default YYYYMMDD)</td>
        </tr>
        <tr>
            <td>direction</td>
            <td>String</td>
            <td>날짜 단위 (Default days)
                <ul>
                  <li>years : 년 (Year)</li>
                  <li>months : 월 (Month)</li>
                  <li>weeks : 주 (Week)</li>
                  <li>days : 일 (Day)</li>
                  <li>hours : 시 (Hour)</li>
                  <li>minutes : 분 (Minute)</li>
                  <li>seconds : 초 (Second)</li>
                </ul>
            </td>
        </tr>        
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Number  
> 두 날짜의 차이를 날짜단위(direction)로 계산하여 반환

***Example***

```js
_UL.date.diffDate('20200508','YYYYMMDD','20200501','YYYYMMDD');
// 7

_UL.date.diffDate('20200611','YYYYMMDD','20200505','YYYYMMDD', 'months');
// 1

_UL.date.diffDate('20200611','YYYYMMDD','20200505','YYYYMMDD', 'weeks');
// 5

_UL.date.diffDate('20200611','YYYYMMDD','20200505','YYYYMMDD', 'weeks');
// 5

_UL.date.diffDate('2020051111213','YYYYMMDDHHmmss','20200507171213','YYYYMMDDHHmmss', 'hours');
// 90
```
<br />

### getTimeBySeconds

***Descrition***  
초(Seconds) 를 시분초(hh:mm:ss) format 으로 변환

***Syntax***  
```js
_UL.date.getTimeBySeconds(seconds)
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
            <td>seconds</td>
            <td>Number</td>
            <td>입력 데이터(Seconds)</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : String  
> 입력 초(Seconds) 를 계산하여 시분초(HH:mm:ss) format 형태로 반환

***Example***

```js
_UL.date.getTimeBySeconds(765);
// 00:12:45
```
<br />

### getSecondsByTime

***Descrition***  
시분초(hh:mm:ss) format 을 초(Seconds) 로 변환

***Syntax***  
```js
_UL.date.getSecondsByTime(time)
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
            <td>time</td>
            <td>String</td>
            <td>시분초 (HH:mm:ss)</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 시분초(HH:mm:ss) format 형태 데이터를 계산하여 초(Seconds) 로 반환

***Example***

```js
_UL.date.getSecondsByTime("00:12:45");
// 765
```
<br />

### getTimeByMinutes

***Descrition***  
분(minutes) 을 시분(hh:mm) format 으로 변환

***Syntax***  
```js
_UL.date.getTimeByMinutes(time)
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
            <td>minutes</td>
            <td>String</td>
            <td>분 (Minutes)</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 분 (Minutes) 데이터를 계산하여 시분(HH:mm) format 형태로 반환

***Example***

```js
UL.date.getTimeByMinutes(100);
// 01:40
```
<br />

### getDateByTime

***Descrition***  
시분(hhmm) format 의 데이터로 Date 객체를 변환  
입력 데이터(hhmm) 는 4자리 이며, blank 경우 현재 시간의 Date 객체를 반환

***Syntax***  
```js
_UL.date.getDateByTime(time)
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
            <td>time</td>
            <td>String</td>
            <td>시분 (HHmm)</td>
        </tr>
    </tbody>
</table>

***Return***
> <span style="color:green; font-weight:bold;">Type</span> : Object  
> 시분초(HHmm) format 형태 데이터로 Date 객체를 생성하여 반환

***Example***

```js
_UL.date.getDateByTime();
// Fri Jun 05 2020 16:13:00 GMT+0900 (대한민국 표준시)

_UL.date.getDateByTime("1545");
// Fri Jun 05 2020 15:45:00 GMT+0900 (대한민국 표준시)

```
<br />
