**A scratch rendering system and operating system making creating beautiful fast pen based apps easy.**
# Global Broadcasts

> all broadcasts start with app.

**app.tick** is **broadcast every frame when the app is open**
use this for app **processing**

**app.render** is also **broadcast every frame when the app is open**
use this to **add items to the render queue**

**general.tick** is run **every frame**
using this **can interfere with system functions** and is **not generally recommended**
# Queue Items

> items are added to the render by adding the item and all arguments separately to the RENDER list

## Stamp
 stamps an image to the screen
```
stamp image x y scale rotation ghost
```
assets should be named app//image
 > example: appname//image.png 0 0 1 0 0
## RGB
 sets the pen colour using RGB
```
rgb r g b a
```
 > example: rgb 255 230 0

## Hex
sets the pen colour using hex 
```
hex hex
```
do not include # or 0x
> example: hex ffff00

## Width
sets pen width
```
width width
```
> example: width 5

## Line
draws a line between two points
```
line x1 y1 x2 y2
```
depends on pen color and width
> example: line -100 0 100 0

## Dot
draws a dot/circle  at a point
```
dot x y
```
depends on pen color and width
> example: dot 0 0

## Rectangle Filled
draws a filled rectangle
```
rectangle_filled x1 y1 x2 y2 rounding
```
> example: rectangle_filled -100 -100 100 100 5 

## Rectangle Outlined
draws the outline of rectangle
```
rectangle_outline x1 y1 x2 y2 rounding
```
depends on pen colour and width
corners may appear curved at high pen widths
> example: rectangle_outlined -100 -100 100 100 5

## Bezier Curve
draws a Bezier curve
```
curve x1 y1 control point x control point y x2 y2
```
depends on pen colour and width
> example: curve -100 -100 0 100 100 -100
## Text
draws text using a stamping based engine
```
text text x y size alignment tracking brightness bold
```
tracking is the distance between letters, 1 is default
alignment can be C, L, or R, for centered left or right. No justified… yet
brightness 0 means the text renders black and 1 means it renders white
> example: text ‘hello world’ 0 0 1 1 0 0
## Hitbox
unlike other queue items the hitbox does not actually render anything to the screen but rather sends a broadcast when the hitbox area has been clicked
```
hitbox x1 y1 x2 y2 broadcast
```
> example: hitbox -100 -100 100 100 button_clicked
## Hit Circle
like a hitbox but defined a circle
```
hitcircle x y radius broadcast
```
> example: hitcircle 0 0 50 button_clicked

## Toggle
creates a toggle
```
toggle x y variable
```
changes the variable defined between ‘true’ and ‘false’
depends on theme colours
> example: toggle 0 0 toggle

## Button
creates a button with a hitbox and click effect
```
button text x y alignment style broadcast
```
sends a broadcast on click
x width changes depending on text length
style can either be ‘p’ for primary ‘s’ for secondary or ‘d’ for disabled
depends on theme colours
alignment can be ‘c’ for centered or ‘l’ for left. This is where it aligns the button to the x y coordinates
> example: button ‘click me’ 0 0 c p button_clicked
