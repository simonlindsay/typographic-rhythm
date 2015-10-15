# typographic-rhythm

### Step 1

Choose your font(s).

I usually will decide on a heading and body font, but you may also have other fonts.

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

Define your modular scale in a sass map. See http://www.modularscale.com/?16,28&px&1.25&web&table
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
