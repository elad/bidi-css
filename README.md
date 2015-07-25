# Bidirectional CSS

A bunch of notes to self about implementing bidirectional CSS.

## Objective

One CSS file, whether created by hand or generated from [less](http://lesscss.org/) or such, that supports both left-to-right and right-to-left languages.

## Implementation

### Explicit

The "explicit" implementation assumes an `html` tag explicitly specifies a direction attribute with either `ltr` or `rtl`:

```css
/* This applies to all h1 tags: */
h1 { text-decoration: underline; }

/* Left-to-right only: */
html[dir=ltr] h1 { color: red; }

/* Right-to-left only: */
html[dir=rtl] h1 { color: blue; }
```

### Implicit

The "implicit" implementation assumes an `html` tag with a non-rtl direction is ltr:

```css
/* This applies to all h1 tags: */
h1 { text-decoration: underline; }

/* Left-to-right only: */
html:not([dir=rtl]) h1 { color: red; }

/* Right-to-left only: */
html[dir=rtl] h1 { color: blue; }
```

This is useful for compatibility with code that either doesn't specify rtl unless needed or simply does not support it altogether.
