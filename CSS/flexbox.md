# FLEX LAYOUT (FLEXBOX)

-   Flex Container and Flex Items (Children)

-   `column` Property has no effect on it.

-   Two types of Flex-layout are:-

    1. **Inline Flex**
    2. **Flex**

-   There are two axes in **flex layout** which is used by the browser to align the flex items :-

    1. **Main Axis**
    2. **Cross Axis**

-   **main-start/main-end & main-size** - For **Main Axis**

-   **cross-start/cross-end & cross-size** - For **Cross Axis**

-   Both the axes positions are affected by **flex-direction** & **flex-wrap**.

### flex-direction

-   It is used to mention the position of **Main Axis** & **Cross Axis**.

-   `flex-direction` takes any of the following four values for letting the browser to figure out positions of both axes.

```bash
<selector name> {
    flex-direction: row | row-reverse | column | column-reverse;
}
```

### flex-wrap

-   It lets you decide either to wrap the **flex items** or not.

```bash
<selector> {
    flex-wrap: wrap | nowrap | wrap-reverse;
}
```

-   `flex-wrap:wrap-reverse;` changes the position of **CROSS AXIS**.

-   If we define a width for all the **flex items** then they will span upto the mentioned width if width of all these items is less/equal to **flex container**.

-   By default the width of **flex items** is equal to width of their contents and they don't wrap which means when total width of contents in **flex items** exceeds the container width then **horizontal scrollbar** will appear.

### flex-flow

-   It is a shorthand for `flex-direction` & `flex-wrap`.

-   It's default value is `row nowrap`.

```bash
flex-flow: <flex-direction> <flex-wrap>;
```

### order

-   It is used to change the position of individual **flex item**.

-   By default, order of each **flex item** is **0**.

-   **flex-items** are ordered based on lowest to highest value of `order` property.

-   `order` can also take **negative** value.

-   Using `order` may cause accessibility issues since the `order` property only changes the **visual apperance** of the **flex-item** but its **sequential navigation order** remains same which may confuse **screen reader**.

### justify-content

-   It tells how the items are aligned across **Main Axis** when there is extra space along that axis inside flex-container.

-   By default its value is `flex-start`.

-   `Jusitfy-Content` depends on `flex-direction`.

-   On **Main Axis**, Flexbox deals with **flex-items** content as a group.The amount of space required to layout the **flex-items** is calculated and the leftover space is then available for distribution, which means `justify-self` property does not make sense since we are moving the entire group of **flex-items** around.

```bash
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | left | right | start | end | baseline;
```

### align-items

-   It tells how the **flex-items** are aligned across **Cross Axis** in the **Current Line**.

-   It's default value is `stretch`.

-   Like `justify-content`, it also depends on `flex-direction`.

```bash
align-items: stretch | flex-start | flex-end | center | baseline;
```

-   `flex-direction` with either `row` or `row-reverse`, there must be some heights to center the **flex-items** along **Cross Axis** using `align-items`.

-   **baseline** align the **flex-items** based on bottom of text content in them.

### align-content

-   It is used to align the flex container's lines within it when there is extra space in **Cross-Axis**.

-   It will behave similar to `align-items` when flexbox has only a single line but if you use `align-content` for single flex line then `align-self` will have no effect on **individual flex item**.

-   It depends on `flex-wrap` property which must be set to `wrap` or `wrap-reverse`.

-   It's default value is `stretch`.

```bash
justify-content: flex-start | flex-end | center | space-between | space-around;
```

### align-self

-   It is used in individual **flex-item** to override `align-items` value.

-   It aligns the item on the **Cross Axis**.

-   default value is **stretch**.

-   It is ignored when **Cross Axis** margin is `auto`.

```bash
align-self: stretch | center | flex-start | flex-end | baseline;
```

### flex-grow

-   A sub-property which is used to fill the extra space remaining in **Main Axis**.

-   Applied to **flex-items**.

-   It's default value is 0(zero).

### flex-shrink

-   A sub-property which is used to shrink the **flex-items** if there is no extra space.

-   It's default value is 1.

-   **flex-items** will shrink below their width until there is enough space to fit the contents.

-   It shrink will not work when **flex-wrap:nowrap**.

### flex-basis

-   It specifies the **initial width** of **flex-item** before distribution of extra space according to flex factors.

-   If **flex-shrink** is given a value which is greater than 0 then **flex-item** will shrink below the width provided using **flex-basis** if it needs to shrink.

-   If it's value is not specified in **flex** shorthand then it's length is zero.

-   It's default value is **auto** which means **flex-item** is sized based on its size property.

### flex

-   Shorthand for **flex-grow**, **flex-shrink** & **flex-basis**.

-   Setting **flex** as 1 means **flex-grow:1**, **flex-shrink:1** & **flex-basis:auto**.

```bash
flex: <flex-grow> <flex-shrink> <flex-basis>;
```

# gap

-   Shorthand for **row-gap** & **column-gap** which is used to provide space between **flex-items**.

-   It applies that spacing only between items not on the outer edges.
