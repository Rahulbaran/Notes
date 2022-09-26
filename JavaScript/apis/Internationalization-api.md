# [Intl](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl)

- `Intl` object is the namespace for the **ECMAScript Internationalization API**.

- It provides access to several constructors & functionality for doing things like number formatting, date & time formatting, language sensitive string comparison etc.

- `locale` is an identifier which refers to a set of user preferences such as:-
  - dates & times
  - numbers & currencies
  - mesaurement units
  - translated names of timezones, languages & countries
  - sort-order(collation)

## Constructor properties

### Intl.Collator()

### Intl.DateTimeFormat()

- It creates `Intl.DateTimeFormat` object that has `format()` method for formatting language-sensitive date & time.
- **Syntax**

```js
new Intl.DateTimeFormat();
new Intl.DateTimeFormat(locales);
new Intl.DateTimeFormat(locales, options);

Intl.DateTimeFormat();
Intl.DateTimeFormat(locales);
Intl.DateTimeFormat(locales, options);
```

- `Intl.DateTimeFormat()` can be called with without `new` and both creates a new `Intl.DateTimeFormat` instance, but there is one difference

#### Parameters

##### locales(_optional_)

- A string with a BCP 47 language tag or an array of such strings. Following unicode extension keys are allowed:
  - `nu` (Numbering System)
  - `ca` (Calender)
  - `hc` (Hour cycle - `"h11"`, `"h12"`, `"h23"`, `"h24"`)

##### options (_optional_)

- An object with some or all of the following properties:

  - `dateStyle` - Possible values are `"full"`,`"long"`,`"medium"`,`"short"`.
  - `timeStyle` - Possible values are `"full"`,`"long"`,`"medium"`,`"short"`.
  - `calender` - Possible values are `"indian"`,`"dangi"`, `"persian"`, `"japanese"` etc.
  - `dayPeriod` - Possible values are `"narrow"`, `"short"`, `"long"`.
  - `numberingSystem` - Possible values are `"guru"`, `"telu"`, `"tibt"`, `"bali"`, `"latn"` etc.
  - `timeZone` - Possible values are `"Asia/Shanghai"`, `"Asia/Kolkata"` etc.
  - `hour12` - It overrides `hc` language tag & the `hourCycle` option. Possible valus are `true` & `false`.
  - `hourCycle` - It overrides the `hc` language tag. Possible values are `"h11"`, `"h12"`, `"h23"` & `"h24"`.
  - `formatMatcher` - Format matching algorithm to use. Possible values are `"basic"` & `"best fit"`(default).
  - `weekday` - Possible values are `"long"`, `"short"` & `"narrow"`.
  - `era` - Possible values are `"long"`(`Anno Domini`), `"short"`(`AD`) & `"narrow"`(`A`).
  - `year` - Possible values are `"numeric"` & `"2-digit"`.
  - `month` - Possible values are `"numeric"`, `"2-digit"`, `"long"`, `"short"` & `"narrow"`.
  - `day` - Possible values are `"numeric"` & `"2-digit"`.
  - `hour` - Possible values are `"numeric"` & `"2-digit"`.
  - `minute` - Possible values are `"numeric"` & `"2-digit"`.
  - `second` - Possible values are `"numeric"` & `"2-digit"`.
  - `fractionalSecondDigits` - Possible values are `0`, `1`, `2`, `3`.
  - `timeZoneName` - Possible values are `"long"`, `"short"`, `"shortOffset"`, `"longOffset"`, `"shortGeneric"` & `"longGeneric"`.

- **Examples**

```js
const dateTimeFormat = (locale, options) =>
  new Intl.DateTimeFormat(locale, options);
const futureDate = new Date(2024, 9, 4, 11, 59, 59);

dateTimeFormat("hi", { dateStyle: "full" }).format(futureDate); // 'शुक्रवार, 4 अक्तूबर 2024'
dateTimeFormat("hi-u-hc-h24", {
  dateStyle: "long",
  timeStyle: "medium"
}).format(futureDate); // '4 अक्तूबर 2024 को 11:59:59'
dateTimeFormat(["hi-IN-u-ca-indian", "en-US-u-ca-dangi"], {
  dateStyle: "medium",
  timeStyle: "full"
}).format(futureDate); // '12 अश्विन 1946 शक, 11:59:59 am भारतीय मानक समय'
dateTimeFormat().format(futureDate); // '04/10/2024'
dateTimeFormat("hi-IN-u-nu-deva", {
  dateStyle: "short",
  timeStyle: "long"
}).format(futureDate); // '४/१०/२४, ११:५९:५९ am IST'
```

> **NOTES** > `dateStyle` can be used with `timeStyle` but not with other options (eg: `weekday`,`hour`,`month` etc.)
> `dayPeriod` has an effect only if a 12-hour clock is used.

### Intl.DisplayNames()

### Intl.ListFormat()

### Intl.Locale()

### Intl.NumberFormat()

### Intl.PluralRules()

### Intl.RelativeTimeFormat()

### Intl.Segmenter()

## Static Methods

### Intl.getCanonicalLocales()

### Intl.supportedValuesOf()
