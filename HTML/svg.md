# SVG(Scalable Vector Graphics)

- Possible shapes are circles, ellipses, lines, squares,rectangles, polylines, polygons & paths.

#### stroke-linecap

- An attributes which defines the shape to be used at the end of open subpaths when it is stroked.
- Possible values are `butt`, `round` & `square`.
- Used with following SVG elements:
  - `<altGlyph>`
  - `<path>`
  - `<line>`
  - `<polyline>`
  - `<text>`
  - `<textPath>`
  - `<tref>`
  - `<tspan>`

#### stroke-linejoin

#### stroke-mitrelimit

## circle

## ellipse

## rectangle

## polygon

## line

## polyline

## [path](https://css-tricks.com/svg-path-syntax-illustrated-guide/)

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
  - `s` & `S` --> It comes after `C/c` & only requires _two_ points where first bezier point is a reflection of the last bezier point from the last `S/C` Command.
  - `Q` & `q` (Quadratic Curve) --> It requires only _two_ points, Where starting & ending point share a single point .
  - `T` & `t` --> It comes after `Q/q` & only requires _single_ point(final) & control point is assumed to be a reflection of the previous one.
  - `A` & `a`

## marker

- `<marker>` element is used for drawing arrowheads or polymarkers on elements like `<path>`, `<line>`, `<polyline>` or `<polygon>` and it is stored in `<defs>` element to use for later time.
- markers are attached to shapes using `marker-start`, `marker-mid` & `marker-end` properties.

### Attributes

#### markerHeight

- Defines the height of the marker viewport & its value type is `<length>`.
- Default value: `3`
- Animatable: **yes**

#### markerWidth

- Defines the width of the marker viewport & its value type is `<length>`.
- Default value: `3`
- Animatable: **yes**

#### markerUnits

- Defines the coordinate system for `markerWidth`, `markerHeight` & the contents of the `<marker>`.
- Value type: `userSpaceOnUse|strokeWidth`;
- Default value: `strokeWidth`;
- Animatable: **yes**

#### orient

- Defines the orientation of the marker relative to shape it is attached to.
- Value type: `auto|auto-start-reverse|<angle>`;
- Default value: `0`;
- Animatable: **yes**

#### preserveAspectRatio

- Defines how the svg fragment must be deformed if it is embedded in a container with a different aspect ratio.
- Value type: `(none|xMinYMin|xMidYMin|xMaxYMin|xMinYMid|xMidYMid|xMaxYMid|xMinYMax|xMidYMax|xMaxYMax) (meet|slice)`
- Default value: `xMidYMid meet`;
- Animatable: **yes**

#### refX

- Defines the **x** coordinate for the reference point of the marker.
- Value type: `left|center|right|<coordinate>`;
- Default type: `0`;
- Animatable: **yes**

#### refY

- Defines the **y** coordinate for the reference point of the marker.
- Value type: `top|center|bottom|<coordinate>`;
- Default value: `0`;
- Animatable: **yes**

#### viewBox

- Defines the bound of the SVG viewport for the current SVG fragment.
- Value type: `<list-of-numbers>`;
- Default value:none;
- Animatable: **yes**
