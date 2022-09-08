# SVG(Scalable Vector Graphics)

- Possible shapes are circles, ellipses, lines, squares,rectangles, polylines, polygons & paths.

## Shapes

### circle

### ellipse

### rectangle

### polygon

### line

### polyline

### [path](https://css-tricks.com/svg-path-syntax-illustrated-guide/)

- `<path>` tag is used to create path.
- `d` attribute is used to mention various commands for a path.
- **UPPERCASE** commands denote _absolute values_ where **LOWERCASE** commands denote _relative values_.
- There are various commands used for drawing a path:-
  - `M` & `m` (starting location)
  - `H` & `h` (Horizontal Line Coordinate)
  - `V` & `v` (Vertical Line Coordinate)
  - `L` & `l` (Straight Line Coordinate)
  - `z` & `Z` (Closing Path)
  - `C` & `c` (Bezier Curve) --> It requires _three_ points where first two points define the location of two bezier curve handles.
  - `s` & `S` --> It comes after `C/c` & only requires _two_ points where first bezier point is a reflection of the last bezier point from the last `S/C` command.
  - `Q` & `q` (Quadratic Curve) --> It requires only _two_ points, Where starting & ending point share a single point.
  - `T` & `t` --> It comes after `Q/q` & only requires _single_ point(final) & control point is assumed to be a reflection of the previous one.
  - `A` & `a`

### marker

- `<marker>` element is used for drawing arrowheads or polymarkers on elements like `<path>`, `<line>`, `<polyline>` or `<polygon>` and it is stored in `<defs>` element for later reuse.
- markers are attached to shapes using `marker-start`, `marker-mid` & `marker-end` properties.

#### Attributes

##### markerHeight

- Defines the height of the marker viewport & its value type is `<length>`.
- Default value: `3`
- Animatable: **yes**

##### markerWidth

- Defines the width of the marker viewport & its value type is `<length>`.
- Default value: `3`
- Animatable: **yes**

##### markerUnits

- Defines the coordinate system for `markerWidth`, `markerHeight` & the contents of the `<marker>`.
- Value type: `userSpaceOnUse|strokeWidth`;
- Default value: `strokeWidth`;
- Animatable: **yes**

##### orient

- Defines the orientation of the marker relative to shape it is attached to.
- Value type: `auto|auto-start-reverse|<angle>`;
- Default value: `0`;
- Animatable: **yes**

##### preserveAspectRatio

- Defines how the svg fragment must be deformed if it is embedded in a container with a different aspect ratio.
- Value type: `(none|xMinYMin|xMidYMin|xMaxYMin|xMinYMid|xMidYMid|xMaxYMid|xMinYMax|xMidYMax|xMaxYMax) (meet|slice)`
- Default value: `xMidYMid meet`;
- Animatable: **yes**

##### refX

- Defines the **x** coordinate for the reference point of the marker.
- Value type: `left|center|right|<coordinate>`;
- Default type: `0`;
- Animatable: **yes**

##### refY

- Defines the **y** coordinate for the reference point of the marker.
- Value type: `top|center|bottom|<coordinate>`;
- Default value: `0`;
- Animatable: **yes**

##### viewBox

- Defines the bound of the SVG viewport for the current SVG fragment.
- Value type: `<list-of-numbers>`;
- Default value: none;
- Animatable: **yes**

### g Element

- Used to group shapes together and the whole group behaves as single shape.
- Applying any style to `g` will affect the whole group since all the shapes inherit from it.
- **Example**

```html
<svg xmlns="http://www.w3.org/2000/svg">
  <g>
    <line x1="10" y1="10" x2="85" y2="10" style="stroke: #006600;" />
    <rect
      x="10"
      y="20"
      height="50"
      width="75"
      style="stroke: #006600; fill: #006600"
    />
    <text x="10" y="90" style="stroke: #660000; fill: #660000">
      Text grouped with shapes
    </text>
  </g>
</svg>
```

> It does not have x & y attributes.

### clipPath

- Used to clip part of an image/text.
- Anything outside of the clip-path will not be displayed.

## Painting Options

#### fill

- Fills the color of any SVG shape.
- Can take any CSS color value(`hex()`, `hwb()`, `hsl()`, `rgb()`).

#### fill-opacity

- Used to set opacity of the paint server(color, gradient, pattern etc.) specified in `fill`.
- Takes value in range of `0` to `1` or `0%` to `100%`.

#### fill-rule

- An attribute which defines the algorithm to use to determine the _inside_ part of a shape.
- It has two values `nonzero` & `evenodd`.
- Used with SVG elements such as `<altGlyph>`, `<path>`, `<line>`,`<polyline>`, `<text>`, `<textPath>`, `<tref>` & `<tspan>`.

#### stroke

#### stroke-width

#### stroke-linecap

- An attribute which defines the shape to be used at the end of open subpaths when it is stroked.
- Possible values are `butt`, `round` & `square`.
- Used with SVG elements such as `<altGlyph>`, `<path>`, `<line>`,`<polyline>`, `<text>`, `<textPath>`, `<tref>` & `<tspan>`.

#### stroke-linejoin

- It defines the shape to be used between two segments drawn.
- Possible values are `round`, `miter`, `miter-clip`, `arcs` & `bevel`.

> `miter-clip`&`arcs`don't have cross browsers support(introduced in SVG2).

#### stroke-mitrelimit

#### stroke-opacity

- Defines opacity of the paint server(color, gradient, pattern etc) specified in `stroke`.
- Default value - `1`
- Takes value in range of either `0` to `1` or `0%` to `100%`.

#### stroke-dasharray

#### stroke-dashoffset

## Gradients in SVG

### Linear Gradient

- `<linearGradient>` element is used to define linear gradients to apply on other SVG element.

```js
<svg viewBox="0 0 10 10" xmlns="http://www.w3.org/2000/svg"
     xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <linearGradient id="myGradient" gradientTransform="rotate(90)">
      <stop offset="5%"  stop-color="gold" />
      <stop offset="95%" stop-color="red" />
    </linearGradient>
  </defs>

  <!-- using my linear gradient -->
  <circle cx="5" cy="5" r="4" fill="url('#myGradient')" />
</svg>
```

#### Attributes

> All these attributes are animatable.

##### gradientUnits

- It defines coordinate system used for the attributes `x1`, `y1`, `x2` & `y2`.

|                   |                                        |
| ----------------- | -------------------------------------- |
| **Value**         | `userSpaceOnUse` / `objectBoundingBox` |
| **Default Value** | `objectBoundingBox`                    |

##### gradientTransform

- Contains transform-list(`rotate()`, `skew()`, `scale()`, `translate()`, `matrix()` etc).

##### href

- It defines a reference to another `<linearGradient>` element that will be used as template.

##### spreadMethod

- It indicates how gradient behaves if it starts/ends inside the bounds of the shape containing the gradient.
- **Value** - `pad`(default)|`reflect`|`repeat`

##### x1

- Defines the x coordinate of the **starting point** of the vector gradient along which the linear gradient is drawn.

##### x2

- Defines the x coordinate of the **ending point** of the vector gradient along which the linear gradient is drawn.

##### y1

##### y2
