rem() is a Sass mixin for setting css properties in rems with fallback values in pixels for less-capable browsers.

## Signature

`@mixin rem($property, $values, [$use-px-fallbacks: $rem-with-px-fallbacks])`

## Usage

(Note that a version of this mixin will be included in an upcoming release of [Compass](http://compass-style.org).)

```scss
// Set configurable variables, if you want to change defaults
$base-font-size: 18px; // default: 16px, same as default browser font-size
$rem-with-px-fallbacks: true; // default: true;

// Import the rem partial
@import "my-partials-path/rem";

// Style a heading
h1 {
  @include rem(font-size, 2rem);
  @include rem(margin-bottom, 1.5rem)
}

// Output a border with width set in rems
.box {
  @include rem(border, 1px solid #bff);
}
```

The following CSS will be produced:

```css
h1 {
  font-size: 36px;
  font-size: 2rem;
  margin-bottom: 27px;
  margin-bottom: 1.5rem;
}

.box {
  border: 1px solid #bbffff;
  border: 0.063rem solid #bbffff;
}
```

There are no restrictions on the style property/ies you can pass in. Values that aren’t in px or rem pass through the mixin untouched. Therefore, you can mix units and still get correct results:

```scss
.crazy-units {
  @include rem(padding, .5rem 16pt 8px .5em);
}
```

## Controlling pixel fallbacks

You can use the mixin without supporting older browsers either one a case-by-case basis or globally.

To control fallbacks at the mixin level as-needed, pass `false` as a parameter after your values:

```scss
@include rem(margin, 21px auto, false);
```
To disable pixel fallbacks globally, set the global $rem-with-px-fallbacks to `false` before importing the partial:

```scss
$print-rem-px-fallbacks: false;

@import "path/to/rem";
```

Based on [the work](https://github.com/bitmanic/rem) of [Ray Brown](https://github.com/bitmanic) and [Adam Stacoviak](https://github.com/adamstac). Huge thanks to [Chris Eppstein](http://chriseppstein.github.com) and Nathan Weizenbaum for the awesomeness that is Compass and Sass.