# typographic-rhythm

### Step 1

Choose your font(s). And define their characteristics and save them as variables.

I usually will decide on a heading and body font, but you may also have other fonts.

```
// Add typefaces here.
// Add weight and style details too.
// ! Set cap height to set to the baseline.
$bodytype: (
  font-family: 'Georgia, serif',
  regular: 400,
  bold: 700,
  italic: italic,
  cap-height: 0.66
) !default;

$headingtype: (
  font-family: 'Helvetica, sans-serif',
  regular: 400,
  bold: 700,
  cap-height: 0.66
) !default;

$monospacetype: (
  font-family: 'Menlo, monospace',
  regular: 400,
  cap-height: 0.68
) !default;
```

### Step 2

Select your root size. This should be the size of your main paragraph font in pixels. Typically set at 16px.
set the variable `$rootsize` to this value without any units, default is 16.

### Step 4
Add the rootsize mixin to the top level html attribute
```
html {
  @include rootsize;
}
```

### Step 3

Define your modular scale in a sass map using the pixel values. See http://www.modularscale.com/?16,28&px&1.25&web&table
Where H1 is alpha and the body paragrpah tag is zeta.
- H1 = Alpha
- H2 = Beta
- H3 = Gamma
- H4 = Delta
- H5 = epsilon
- P = zeta
- small = theta
- ? = iota

For example

```
$modular-scale: (
  alpha:   28.0,
  beta:    25.0,
  gamma:   22.4,
  delta:   20.0,
  epsilon: 17.9,
  zeta:    16.0,
  eta:     14.3,
  theta:   12.8,
  iota:    11.5
)
```
### Step 4

Set the site wide base styles on the `body` tag.
```
// Site-wide base styles.
body {
  font-family: unquote(map-get($bodytype, font-family));
  font-style: normal;
  font-weight: map-get($bodytype, regular);
  line-height: 2rem;
  @include fontsize(zeta);
}
```

### Step 5

Create base styles for each inline tag, including but not limited to: h1, h2, h3. h4, h5, h6, p, small
Remember to keep the the modular-scale mapped names, `alpha`, `beta` etc.

- - -

Sources:
- https://medium.com/written-in-code/aligning-type-to-baseline-the-right-way-using-sass-e258fce47a9b
- https://jakegiltsoff.co.uk/posts/sassline-v2-0
