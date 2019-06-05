# Occo SCSS

A modular and atomic SCSS library for all your basic SCSS needs.

## Usage

Install:

```bash
npm install occo
```

Import:

```scss
@import 'occo';
```

Import specific modules only:

```scss
@import 'occo/scss/core/index';
@import 'occo/scss/modules/some-module';
```

##


## Modules

Each module is split into at most four parts (in order of dependency):

1. Variables.
2. Functions.
3. Mixins.
4. Classes.

This package is meant to be as generic and non-intrusive as possible. All variables are prefixed with `occo-`, and can be overridden.

Mixins and classes generally overlap in terms of functionality. This allows you to use either of these in your codebase, depending on preference. E.g., you can use:

```scss
.my-rounded-class {
  @extends .is-round;
}

.my-other-rounded-class {
  @include round;
}
```

### Core

This isn't really a module. The `core` folder contains definitions used by the other modules. It does not contain any CSS rules.

#### Variables

`$occo-sides`

A list of all sides (`top, bottom, left, right`).

`$occo-directions`

Horizontal and vertical directions (`h, v`).

#### Functions

`opposite($side)`

Returns the opposite of a side. E.g. `left` => `right`.

`tangent($side)`

Returns a tangent of a side. Only returns `top` or `left`. E.g. `top` => `left`.

`direction-begin($direction)`

Returns the begin side of a direction. E.g. `v` => `top`.

`direction-end($direction)`

Returns the end side of a direction. E.g. `v` => `bottom`.

`direction-dimension($direction)`

Returns the dimension corresponding to a direction. E.g. `v` => `height`.

### Appearance

Vanity stuff.

#### Variables

`$occo-radius`

The default border-radius of rounded items. Defaults to `4px`.

`$occo-cursors`

All possible cursor values.

`$occo-overflows`

All possible overflow values.

#### Mixins

`radius`

Applies the default border-radius.

`rounded`

Applies a border-radius of `9999px`, making the corners of the element rounded.

`round`

Applies a border-radius of `100%`, making it circular or oval.

#### Classes

`.has-cursor-#{$cursor}`

Applies a certain cursor.

`.has-overflow-#{$overflow}`, `.has-overflow-#{$overflow}-x`, `.has-overflow-#{$overflow}-y`

Applies a certain overflow. Optionally only in x- or y-direction.

`has-radius`

Applies the default border-radius.

`is-rounded`

Applies a border-radius of `9999px`, making the corners of the element rounded.

`is-round`

Applies a border-radius of `100%`, making it circular or oval.

### Colors

Define your completely custom color palette and apply it through classes and mixins. We don't enforce a specific set of color names at all, you're free to name your own colors.

#### Variables

`$occo-colors`

Contains a library of brand colors, flat design colors, and material design colors.

`$occo-palette`

Your custom palette. Empty, but intended to be overridden. You can name your colors any way you want. For examples below, we'll assume it contains a color named `primary`.

`$occo-darken-factor`

Factor used for darkening. Defaults to `10%`.

`$occo-lighten-factor`

Factor used for lightening. Defaults to `10%`.

`$occo-saturate-factor`

Factor used for saturation. Defaults to `20%`.

`$occo-desaturate-factor`

Factor used for desaturation. Defaults to `20%`.

#### Functions

`color($family, $name, $shade: 500)`

Returns a color from the library.

`palette($name)`

Returns a color from your custom palette. E.g. `color(primary)`.

`default-darken($color)`

Darken a color with the default darken factor.

`default-lighten($color)`

Lighten a color with the default lighten factor.

`default-saturate($color)`

Saturate a color with the default saturate factor.

`default-desaturate($color)`

Desaturate a color with the default desaturate factor.

#### Mixins

`background-color($name)`

Applies a background color from the palette.

`text-color($name)`

Applies a text color from the palette.

#### Classes

`.has-bg-#{$name}`

Applies a background color from the palette.

`.has-text-#{$name}`

Applies a text color from the palette.

### Space

Margin, padding and positioning.

#### Variables

`$occo-space`

A map of named distance values.

`$occo-positions`

All possible position values.

`$occo-displays`

All possible display values.

#### Functions

`space($name)`

Returns a value from the `$occo-space` map. E.g. `space(medium)`.

#### Mixins

`float($side)`

Applies a float to a side. E.g. `float(left)`.

`clearfix`

Applies a simple clear fix.

`padding($size, $side: null)`

Applies a size from the `sizes` map as padding to a side. If `$side` is left as `null`, the padding is applied to all sides.

`margin($size, $side: null)`

Applies a size from the `sizes` map as margin to a side. If `$side` is left as `null`, the margin is applied to all sides.

`no-padding($side: null)`

Removes padding for one or all sides using `!important`.

`no-margin($side: null)`

Removes margin for one or all sides using `!important`.

`spaced($size, $direction: null)`

Spaces sibling elements by applying margins. The first and last elements lack margin on the sides touching the container, so the group of siblings does not have any margin around it.

#### Classes

`.is-float-left`

Applies `float: left`.

`.is-float-right`

Applies `float: right`.

`.is-clearfix`

Applies a simple clear fix.

`.has-padding-#{$side}-#{$name}`

Applies a padding of a named size to a side.

`.has-padding-#{$name}`

Applies a padding of a named size to all sides.

`.has-no-padding-#{$side}`

Removes padding from a side.

`.has-no-padding`

Removes padding from all sides.

`.has-margin-#{$side}-#{$name}`

Applies a margin of a named size to a side.

`.has-margin-#{$name}`

Applies a margin of a named size to all sides.

`.has-no-margin-#{$side}`

Removes margin from a side.

`.has-no-margin`

Removes margin from all sides.

`.is-spaced-#{$direction}-#{$name}`

Applies a spacing of a named size in a direction.

`.is-spaced-#{$name}`

Applies a spacing of a named size to each direction.

### Typography

Font and text rules.

#### Variables

`$occo-font-sizes`

A map containing a basic set of font sizes (`small: 0.75rem, base:  1.00rem, large: 1.25rem`).

`$occo-font-weights`

A map containing a basic set of font weights.

`$occo-text-alignments`

All possible text-align values.

`$occo-text-transforms`

All possible text-transform values.

`$occo-text-overflows`

All possible text-overflow values.

#### Mixins

`font-size($name)`

Applies a named font size.

`font-weight($name)`

Applies a named font weight.

`one-line`

Forces the text on one line, using `whitespace: nowrap`.

#### Classes

`.has-text-#{$name}`

Applies a named font size.

`.has-text-#{$alignment}`

Applies a text-align.

`.has-text-#{$transform}`

Applies a text-transform.

`.has-text-#{$name}`

Applies a named font weight.

`.has-text-overflow-#{$overflow}`

Applies a text-overflow.

### Utility

Assorted utility variables and functions.

#### Variables

`$occo-input-types`

All possible input types (`text`, `password`, etc.).

`$occo-heading-tags`

All possible heading tags (`h1`, `h2`, etc.).

#### Functions

`text-input-selectors($types: (), $modifier: '')`

Returns a CSS selector for a set of input types (all if left empty), with an optional modifier selector.

`heading-selectors($tags: (), $modifier: '')`

Returns a CSS selector for a set of headings (all if left empty), with an optional modifier selector.
