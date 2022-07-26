# CSS Properties

## `mask`

- It hides an element(partially/fully) by masking or clipping the image at specific points.
- It is a shorthand of following properties:-

  - `mask-clip`
  - `mask-composite`
  - `nask-image`
  - `mask-mode`
  - `mask-origin`
  - `mask-position`
  - `mask-repeat`
  - `mask-size`

- If only one `<geometry-box>` value is given then both `mask-origin` & `mask-clip` are set. If two `<geometry-box>` values are present, then the first sets `mask-origin` & the seconds sets `mask-clip`.

#### `mask-clip`

- It is used for determining the area which is affected by a mask.
- The painted content of an element must be restriced to this area.
- Default value is `border-box`.
- We can use multiple values separated by _comma_.
- **Syntax**

```css
/* <geometry-box> value */
mask-clip: content-box|padding-box|border-box|margin-box|fill-box|stroke-box|view-box|no-clip;

/* Global values */
mask-clip: inherit|initial|revert|revert-layer|unset;
```

#### `mask-composite`

- When we use more than one mask layer then `mask-composite` is used for applying compositing operation on the current mask layer with mask layers below it.
- Default value is `add`.
- **Syntax**

```css
/* Keyword Values */
mask-composite: add|subtract|intersect|exclude;

/* Global Values */
mask-composite: inherit|initial|revert|revert-layer|unset;
```

#### `mask-image`

- Sets the image which is used as mask layer for an element.
- **Syntax**

```css
mask-image: url(mask.svg#mask1) |url(mask.png) |gradient;
```

#### `mask-mode`

- Sets whether the mask reference defined by `mask-image` is treated as a luminance/alpha mask.
- Default value is `match-source`.
- **Syntax**

```css
mask-mode: luminance|alpha|match-source;
```

#### `mask-origin`

- Sets the origin of a mask.
- Default value is `border-box`.
- **Syntax**

```css
mask-origin: content-box|padding-box|border-box|margin-box|fill-box|stroke-box|view-box|no-clip;
```

#### `mask-position`

- Sets the initial position relative to the mask position layer set by `mask-origin`.
- Default value is `center`.
- **Syntax**

```css
mask-position: top|bottom|left|right|center|<length-percentage>|x-start|x-end|y-start|y-end;
```

#### `mask-repeat`

- Sets how mask images are repeated.
- **Syntax**

```css
mask-repeat: repeat-x|repeat-y|repeat|space|round|no-repeat;
```

#### `mask-size`

- Specifies the size of the mask image.
- Default value is `auto`.
- **Syntax**

```css
/* Width value (height set to auto) */
mask-size: cover|contain|auto|<length-percentage>;

/* Width & Height Values */
mask-size: <length-percentage> auto|auto auto|<length-percentage>
  <length-percentage>;
```
