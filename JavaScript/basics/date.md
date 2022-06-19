# [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

- `Date` object is used to get time which is calculated since _1 January 1970 UTC_ (in milliseconds).

## Constructor

##### Date()

- When it is called as a **function** then it returns a string representation of the current date & time.
- Any argument passed in it, is ignored.
- It is same as executing `new Date().toString()`.

##### new Date()

- When `Date()` is called as **constructor** then a new `Date` object is returned.
- **Syntax**

```js
new Date();
new Date(value); // value - An integer representing no. of milliseconds
new Date(dateString); // dateString - A string representing a date
new Date(dateObject); // dateObject - An existing `Date` object

new Date(year, monthIndex, day, hours, minutes, seconds, milliseconds);
```

- **Example**

```js
const today = new Date(); // Fri Jun 10 2022 07:26:10 GMT+0530 (India Standard Time)
const marriageDay = new Date("Dec 10 2022 05:10:23"); // Sat Dec 10 2022 05:10:23 GMT+0530 (India Standard Time)
const birthDay = new Date("1996-04-05T09:10:15"); // Fri Apr 05 1996 09:10:15 GMT+0530 (India Standard Time)
const departureDay = new Date(2022, 08, 15, 10, 15, 40, 10); // Thu Sep 15 2022 10:15:40 GMT+0530 (India Standard Time)
const arrivalDay = new Date(1222404299415); // Fri Sep 26 2008 10:15:26 GMT+0530 (India Standard Time)
```

## Static Methods

##### Date.now()

- Returns no. of milliseconds elapsed since _January 1, 1970 00:00:00 UTC_ with leap seconds ignored.

```js
Date.now(); // 1654823595085
```

##### Date.parse()

- Parses a string representation of a date & returns the number of milliseconds since _1 January 1970, 00:00:00 UTC_ with leap seconds ignored.
- Due to browser inconsistencies, It is strongly discouraged to parse date string with `Date.parse`.

##### Date.UTC()

- It accepts parameters similar to `Date` Constructor(i.e. 2 to 7) but **treats them as UTC** and returns number of milliseconds since _January 1 1970, 00:00:00 UTC_ with leap seconds ignored.
- **Syntax**

```js
Date.UTC(year);
Date.UTC(year, month);
Date.UTC(year, month, day);
Date.UTC(year, month, day, hour);
Date.UTC(year, month, day, hour, minute);
Date.UTC(year, month, day, hour, minute, second);
Date.UTC(year, month, day, hour, minute, second, millisecond);
```

- **Example**

```js
Date.UTC(2011, 10, 14); // 1321228800000
```

## Instance Methods

##### Date.prototype.getDate()

- Returns the day of the month for the specifed date according to _local time_.
- **Example**

```js
new Date().getDate(); // 10
```

##### Date.prototype.getDay()

- Returns the day of week as index(`0`-`6`) according to _local time_, where `0` represents **Sunday**.
- **Example**

```js
const vacantDate = new Date(`Jan 25 2022 14:10:45`);
vacantDate.getDay(); // 2 ---> Tuesday
```

##### Date.prototype.getFullYear()

- Returns the year of the specified date according to _local time_.
- **Example**

```js
const birthYear = new Date("5 April 1996 15:10:59").getFullYear(); // 1996
```

##### Date.prototype.getMonth()

- Returns the month(`0`-`11`) in the specified date according to _local time_.
- **Example**

```js
const birthMonth = new Date(1996, 3, 05).getMonth(); // 3
```

##### Date.prototype.getHours()

- Returns the hour (`0`-`23`) in the specified date according to _local time_.
- **Example**

```js
const currentHour = new Date().getHours(); // 10
```

##### Date.prototype.getMinutes()

- Returns the minutes(`0`-`59`) in the specified date according to _local time_.
- **Example**

```js
const examDate = new Date("June 20 2021 11:00:00.423");
birthDate.getMinutes(); // 0
```

##### Date.prototype.getMilliseconds()

- Returns the milliseconds (`0`-`999`) in the specified date according to _local time_.
- **Example**

```js
const curDate = new Date();
curDate.getMilliseconds(); // 854
```

##### Date.prototype.getSeconds()

- Returns the seconds(`0`-`59`) in the specified date according to _local time_.
- **Example**

```js
const date = new Date();
date.getSeconds(); // 42
```

##### Date.prototype.getTime()

- Returns the numeric value of the specified date as the number of milliseconds since _Jan 1 1970, 00:00:00 UTC_.
- If specified date is before _Jan 1 1970_ then negative values are returned in milliseconds.
- **Example**

```js
const curTimeInMs = new Date().getTime(); // 1654849848644
```

##### Date.prototype.getTimezoneOffset()

- Returns the difference between a date evaluated in UTC timezone & the same date evaluated in local timezone, in minutes.
- number of minutes is positive if UTC timezone is behind local timezone and if it is ahead of local timezone then value is negative.

##### Date.prototype.getUTCDate(), Date.prototype.getUTCDay(), Date.prototype.getUTCFullYear(), Date.prototype.getUTCMonth(), Date.prototype.getUTCHours(), Date.prototype.getUTCMinutes(), Date.prototype.getUTCSeconds(), Date.prototype.getUTCMilliSeconds()

> In all the above _UTC based_ `Date` object methods, returned values are based on universal date.

##### Date.prototype.setDate()

- Sets the day of the month for a specified date according to _local time_.
- **Example**

```js
const curDate = new Date();

const futureDate = new Date(curDate.setDate(20)); // Mon Jun 20 2022 14:27:59 GMT+0530 (IST)
```

##### Date.prototype.setFullYear()

- Sets the full year for a specified date according to _local time_.
- **Example**

```js
const curTime = new Date();
const birthYear = new Date(curTime.setFullYear(1996)).getFullYear(); // 1996
```

##### Date.prototype.setMonth()

- Sets the month for a specified date according to _local time_.
- **Example**

```js
const setMonthFunc = date => {
  return date.setMonth(4);
};
setMonthFunc(new Date()); // 1657593298030
```

##### Date.prototype.setHours()

- Sets the hours for a specifed date according to _local time_.
- **Example**

```js
const setOwnHours = new Date().setHours(10); // 1655008670759
```

##### Date.prototype.setMinutes()

- Sets the minutes for a specified date according to _local time_.
- **Example**

```js
const setOwnMinutes = new Date().setMinutes(49); // 1655003970138
```

##### Date.prototype.setSeconds()

- Sets the seconds for a specified date according to _local time_.
- **Example**

```js
const setOwnSeconds = new Date().setSeconds(32); // 1655001890032
```

##### Date.prototype.setMilliSeconds()

- Sets the milliseconds for a specified date according to _local time_.
- **Example**

```js
const setMilliSec = new Date().setMilliSeconds(300); // 1655029890400
```

##### Date.prototype.setTime()

- Takes `Date` object as argument and sets a time represented in milliseconds since _January 1, 1970, 00:00:00 UTC_.
- **Example**

```js
const futureTime = new Date().setTime(Date.UTC(2024, 10, 23, 21, 54, 23, 545)); // 1732398863545
```

##### Date.prototype.setUTCDate(), Date.prototype.setUTCFullYear(), Date.prototype.setUTCMonth(), Date.prototype.setUTCHours(), Date.prototype.setUTCMinutes(), Date.prototype.setUTCSeconds(), Date.prototype.setUTCMilliseconds()

- These all methods set the time based on _UTC time_.

##### Date.prototype.toDateString()

- Returns the _date_ protion of the `Date` as a human-readable string.
- **Example**

```js
const openingDate = new Date(2022, 06, 05, 12, 45, 23);
openingDate.toDateString(); // 'Tue Jul 05 2022'
```

##### Date.prototype.toTimeString()

- Returns the _time_ portion of the `Date` as a human-readable string.
- **Example**

```js
const startDate = new Date(2022, 06, 15, 8, 13, 10);
startDate.toTimeString(); // '08:13:10 GMT+0530 (India Standard Time)'
```

##### Date.prototype.toString()

- Returns a string representing the specified `Date` object.
- **Example**

```js
const giveawayDate = new Date(2023, 0, 14, 23, 59, 0);
giveawayDate.toString(); // 'Sat Jan 14 2023 23:59:00 GMT+0530 (India Standard Time)'
```

##### Date.prototype.toUTCString()

- Returns a string representing `Date` object in _UTC timezone_.
- **Example**

```js
const date = new Date();
date.toUTCString(); // 'Tue, 14 Jun 2022 08:25:16 GMT'
```

##### Date.prototype.toISOString()

- Converts a date to a string following the _ISO 8601_ Extended Format.
- **Example**

```js
const date = new Date(2022, 06, 04, 16, 34, 45);
date.toISOString(); // '2022-07-04T11:04:45.000Z'
```

##### Date.prototype.toJSON()

- Returns a string representing the `Date` using `toISOString()`.
- It is intended for use by `JSON.stringify()`.
- **Example**

```js
const newDate = new Date();
newDate.toJSON(); // '2022-06-14T08:46:42.826Z'
```

##### Date.prototype.toGMTString()

- Returns a string representing the `Date` based on _GMT (UTC) timezone_.
- **Example**

```js
const curDate = new Date();
curDate.toGMTString(); // 'Tue, 14 Jun 2022 08:49:50 GMT'
```

##### Date.prototype.toLocaleDateString()

- Returns a string containing date portion of `Date` object based on system settings (_locality-sensitive representation_).
- **Example**

```js
const newDate = new Date("Jun 25 2022 15:45:34.524");
newDate.toLocaleDateString(); // '6/25/2022'
```

##### Date.prototype.toLocaleTimeString()

- Returns a string containing time portion of `Date` object based on system settings (_locality-sensitive representation_).
- **Example**

```js
const travelDate = new Date("21 Aug 2023 05:15:43");
travelDate.toLocaleTimeString(); // '5:15:43 AM'
```

##### Date.prototype.toLocaleString()

- Returns a string containing `Date` based on system settings (_locality-sensitive representation_).
- **Example**

```js
const futureDate = new Date("Jun 25 2022 15:45:34.524");
futureDate.toLocaleString(); // '6/18/2022, 2:52:52 AM'
```

##### Date.prototype.valueOf()

- Returns the primitive value(numerical value) of a `Date` object.
- **Example**

```js
const currentDate = new Date(2023, 10, 05, 5, 10, 43, 453);
currentDate.valueOf(); // 1699141243453
```

> To create & get dates between the years `0` & `99`, we can use `setFullYear()` & `getFullYear()`.
