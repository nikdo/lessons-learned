# Sketch Cheat Sheet

## Moving Around

* ⌘ + 1 = zoom to fit all
* ⌘ + 2 = zoom to fit selection
* ⌘ + 3 = center selection

* Space + drag = drag the canvas

* ⌃ + R = rules
* ⌃ + G = grid
* ⌃ + P = pixels

* ⌘ + . = presentation mode

* ⌘ + ⇧ + / = open help

↵ or double click = edit symbol / group / vector / shape / text

Position objects outside of artboard to compose or test stuff before moving it to artboard.

## Selecting

* ⇧ + click = add or remove from selection
* ⌥ + click = select object behind front object
* right click → Select Layer = select layers beneath
* ⌥ + select = Select only fully contained objects

## Moving

* ⌥ + ⌘ + drag = drag selected by clicking anywhere

* select → ⌥ + hover = distance \(then move\)

* ⇧ + move = stay straight
* arrow = change position by 1px
* ⇧ + arrow = change position by 10px

* ⌥ + move = copy and move object

* ⌘ + D = duplicate object

## Resizing

* handle = resize
* ⌥ + handle = resize from center
* ⇧ + handle = keep proportions
* ⌘ + arrow = resize by 1px
* ⌘ + ⇧ + arrow = resize by 10px

* ↑ or ↓ in number input = increase or decrease by 1

* ⇧ + ↑ or ⇧ + ↓ in input = increase or decrease by 10
* number inputs accepts calculations

Locked proportions → no need to hold ⇧ to keep proportions.

## Rotating

* ⌘ + handle = rotate
* ⇧ + ⌘ + handle = rotate with constraints

Use flatten to reset bounding box.

## Layers

* ⌘ + R = rename

* ⌘ + ⇧ + H = toggle hide layer

* ⌘ + ⇧ + L = toggle lock layer

It is sometimes useful to create multiple states of an UI element above each other, hiding one of them. There is no need to create a separate artboard for that.

* ⌘ + ⌥ + ↑ = bring forward
* ⌘ + ⌥ + ↓ = send backward
* ⌘ + ⌥ + ⌃ + ↑ = bring to front
* ⌘ + ⌥ + ⌃ + ↓ = send to back

## Groups

* ⌘ + G = group
* ⌘ + ⇧ + G = ungroup
* ⌘ + click = select within a group

Create click-through groups to stay organized with many layers. Grouping for sanity instead of grouping for manipulation.

## Shapes

* A = Artboard
* R = Rectangle
* 0 - Oval
* L - Line

* ⌥ + create = resize from center

* ⇧ + create = equal w & h + locked aspect ratio

* ⌥ + ⌘ + U = Union

* ⌥ + ⌘ + S = Substract
* ⌥ + ⌘ + I = Intersect

## Vectors

* V = vector \(bezier curves\)
* P = pencil tool \(drawing converted to vector\)
* ↵ on shape = edit as vector

* ⇧ = constraint line

* ⌘ + direction handle = create disconnected point

* double click point = toggle straight & mirrored

* ⇧ + click = add or remove point from selection
* click on line = add point
* ⌘ + line = bend line

* ⇧ + ⌘ + O = convert to outlines \(useful for borders, lines and text\)

Vector points can be moved the same way as objects.

Radius can be set for straight points.

## Style

* ⌃ + C = pick color

Drag over H S B letters in color picker to adjust hue, saturation and brightness separately.

* ⌥ + ⌘ + C = copy style
* ⌥ + ⌘ + V = paste style

Use layer styles to keep style of multiple elements consistent.

## Text

* T = Text
* esc after text mode = style the whole text

Use text styles to keep design consistent and aligned with changing brand guidelines.

## Symbols

Group symbols by using / in the name.

## Exporting

* ⌘ + ⇧ + E = export
* S = slice tool

Use slices instead of exporting layers:

1. When you need to export multiple states of the same UI element with different bounding box sizes.
2. When you need to export things as they look. For example multiple artboards in one image.

Organize exported assets into folders by using / in the name of exported layer or slice.

## Design Observations

Subtle is good.

1px sharp low-opacity shadow adds shapes slightly material look.

Aligning shapes mathematically does not to have produce visually appealing results. Shape can have more weight on a certain side. For example directional icons like triangle can be slightly offset to the direction to look better.

