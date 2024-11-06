# TomatOS
## Queue Items
stamp (image) (x) (y) (scale) (rotation) (ghost) stamps an image to the screen, costumes should be named app//image rgb (r) (g) (b) (a) sets the pen colour using RGBA (alpha channel currently does nothing) hex (hex) sets the pen colour using hex - do not include # or 0x width (width) sets pen width line (x1) (y1) (x2) (y2) draws a line between two points dot (x) (y) draws a dot/circle (depending on pen width) at a point rectangle_filled (x1) (y1) (x2) (y2) (rounding) draws a filled rectangle rectangle_outline (x1) (y1) (x2) (y2) (rounding) draws the outline of rectangle (may appear curved at high pen widths) curve (x1) (y1) (control point x) (control point y) (x2) (y2) draws a Bezier curve text (text) (x) (y) (size) (tracking x) (brightness) (bold) hitbox (x1) (y1) (x2) (y2) (broadcast) unlike other queue the hitbox does not actually render anything to the screen but rather broadcasts a command when the hitbox area has been clicked hitcircle (x) (y) (radius) (broadcast) like a hitbox but defined by an area toggle (x) (y) (variable)
## global broadcasts
all broadcasts start with app.
app.tick is broadcast every frame when the app is open - use this for app proccessing
app.render is also broadcast every frame when the app is open - use this to add items to the render queue
general.tick is run every frame, using this can cause problems and is not generally recommended
