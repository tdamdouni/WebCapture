# Box Alignment Cheatsheet

_Captured: 2017-04-06 at 01:11 from [rachelandrew.co.uk](https://rachelandrew.co.uk/css/cheatsheets/box-alignment?utm_content=buffera19d3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The [box alignment specification](https://drafts.csswg.org/css-align/) details how items are aligned in the various layout methods. As different layout methods pose different constraints in terms of alignment, some of the behaviour of Box Alignment is layout method dependent. This cheatsheet compares alignment in CSS Grid Layout and Flexbox.

## Key concepts of the Box Alignment specification

When you align an item, you do so within an **alignment container**. This is the rectangle you are aligning the item or items inside, usually the containing block. The item you are aligning inside that block is the **alignment subject**.

The specification defines three types of alignment:

  * [Positional alignment](https://drafts.csswg.org/css-align/#positional-values) \- keywords such as start, end, center
  * [Baseline alignment](https://drafts.csswg.org/css-align/#baseline-values) \- baseline, last baseline, first baseline
  * [Distributed alignment](https://drafts.csswg.org/css-align/#distribution-values) \- includes space-between and space-around

Most of these keyword values work in reference to the writing mode of the document. Therefore `start` may be the left-hand line of a grid container when working in English, but the right-hand line when working in a right-to-left language.

## Block and Inline Axis

You will find the Block and Inline Axis referred to in various ways. The Block Axis, is referred to as the **Column Axis** in the Grid specification and in Flexbox as the **Cross Axis** as it runs across the **Main Axis**.

The Inline Axis is referred to as the **Row Axis** in the Grid specification and in Flexbox as the **Main Axis**.

Alignment on these Axes is easier to understand in Grid as we always have strict rows and columns, in flexbox we also have to consider the ability to change the direction of the main axis from row to column.

## align-self / align-items

Align an item / a group of items on the Block Axis

alignment container
    the grid area
default behaviour
    Acts as if the value is `stretch`, other than for items with an intrinsic aspect ratio, these behave as `start`.
possible values
    auto, normal, start, end, center, stretch, baseline, first baseline, last baseline
works on
    **block axis** / column axis 

#### Example

The default for `align-self` acts like `stretch`. Setting `align-items` to start on the grid container will cause all items to align to the start on the Block axis.

#### Initial value

![](https://rachelandrew.co.uk/images/examples/align-items-grid-default.svg)

> _align-items: start_

![](https://rachelandrew.co.uk/images/examples/align-items-grid-start.svg)

alignment container
    the flex line the item is in
default behavior
    Acts as `stretch`
possible values
    auto, normal, flex-start, flex-end, center, stretch, baseline, first baseline, last baseline
works on
    **cross axis** / block axis

#### Example

The default for `align-self` is `stretch`. Causing the items to stretch to the height of the flex container if `flex-direction: row`, and to the width if `flex-direction: column`.

#### direction: row

![](https://rachelandrew.co.uk/images/examples/align-flex-row-align-items.svg)

> _Direction: column_

![](https://rachelandrew.co.uk/images/examples/align-flex-column-align-items.svg)

#### flex-start

![](https://rachelandrew.co.uk/images/examples/align-items-row-flex-start.svg)

> _flex-start_

![](https://rachelandrew.co.uk/images/examples/align-items-column-flex-start.svg)

## justify-self / justify-items

Justify an item / a group of items on the Inline Axis

## align-content

Control alignment of items within their content box on the Block Axis

![](https://rachelandrew.co.uk/images/examples/flex-align-content-row-default.svg)

> _space-between_

![](https://rachelandrew.co.uk/images/examples/flex-align-content-row-space-between.svg)

> _column default_

![](https://rachelandrew.co.uk/images/examples/flex-align-content-column-default.svg)

> _space-between_

![](https://rachelandrew.co.uk/images/examples/flex-align-content-column-space-between.svg)

## justify-content

Control alignment of items within their content box on the Inline Axis
