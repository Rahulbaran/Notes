# Canvas Tutorial

- Canvas API uses `<canvas>` element and scripting(`JavaScript`) to draw **2d Graphics**.
- Default Size of Canvas --- 300px \* 150px
- Custom `width` and `height` can be defined using HTML or CSS
- Uses JavaScript Context Object **getContext('2d')** to setup canvas envrironment
- For older browser some descriptions can be provided in `<canvas>`
- `<canvas>` requires the closing tag `</canvas>` unlike the `<img>` tag.
- Defining JS Context will return an object **CanvasRenderingContext2D**.
- Drawing occurs in the canvas grid or **coordinate space** and its origin is _top left corner_ (Normally 1 unit in grid corresponds to 1 pixel on the canvas).
- All the elements are placed relative to the origin.

##### Three functions to draw rectangle

    * fillRect(x, y, width, height) - draws a solid rectangle
    * strokeRect(x,y,width,height) - draws a rectangular outline
    * clearRect(x,y,width,height) - Makes area of rectangle fully transparent

- Path is a list of points, connected by segments of lines.
- There are following functions used to create a path:-

  - beginPath() - Begining of the path
  - moveTo() - Moves the starting point of a new sub-path to (x,y) coordinates
  - lineTo() - Connects the last point in current sub-path to specified (x, y)
  - bezierCurveTo() - To add a cubic bezier curve to current path
  - quadraticCurveTo() - Adds a quardatic Bezier Curve to current path
  - arc() - Adds a circular arc to current path
  - arcTo() - Adds an arc to current path with given control points & radius
  - ellipse() - Adds an elliptical arc to the current path
  - rect() - Creates a path for a rectangle at position(x,y)
  - closePath() - Adds a staright line to the path, going to start of the current sub-path.
  - stroke() - draws the shape by stroking outline
  - fill() - draws a solid shape by filling the path's content area.

- After beginPath() first path command is treated as a **moveTo()** regardless of what it actually is, that's why you should always mention **moveTo()**.
- **moveTo()** sets a position from where drawing paths are allowed.
