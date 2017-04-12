# squid.css
squis.css is a configurable, vw-based **squ**are gr**id** system written in Sass. Conventional grid system are one dimensional, that is they typically only define sizes along the x-axis. squid.css is two dimensional, meaning it allows you to define both the width and height of a "column".

squid.css does this by using `vw`  for width and height. This enables responsive proportional rectangles.

### Features
- Uses `vw` for responsive proportionality
- Built with Flexbox
- Highly configurable through Sass variables
- Mobile first

## Browser Support
squid requires support for `vw` and `display: flex`.
This means no **UC Browser for Android** and no **Opera Mini**, since they don't support `vw`.

## Installation
**Clone from GitHub**
`$ git clone git@github.com:madsfaerch/squid-css.git`
Use `squid.css` for development and `squid.min.css` for production
**NPM**
`$ npm install --save squid-css`
And then add `squid-css"` to your workflow. 

## Usage
I highly recommend you configure **squid.css** to suit your needs. Check out the configuration chapter to see what's available to you.

Since squid uses `vw `, and not percentages, putting grid-items in a container with a `width` or `max-width` will not stop the elements from growing, since their width is not based on the parent. Instead, use the variable `$squid-max-width` to set a maximum width on the grid.

### Containers
squid uses two types of containers:
```
.container
```
For larger sections. This keeps your content centered if you use squid with a maxmimum width.

```
.row
```
For rows of content. Use the modifier class `.row-vertical` for vertical rows.

### Width and height
To specify a rectangle's dimensions use `w-<size-value>` for width and `h-<size-value>` for height.

For example, add the classes `w-1` and `h-1` for a 1 by 1 square. By default squid uses 12-column system, so `w-1` and `h-1` will equate to a width and height of `8.333vw` (100vw/12 * 1).
 
```html
<div class="row">
  <div class="grid-item w-1 h-1">
    I'm a perfect square!
  </div>
</div>
```

Make rectangles with other proportions simply by changing the width or height class:
```html
<div class="row">
  <div class="grid-item w-2 h-1">
    I'm a 2 by 1 rectangle!
  </div>
</div>
```

Adding is just like any other grid:
```html
<div class="row">
  <div class="grid-item w-1 h-1">
    I'm a perfect square!
  </div>
  <div class="grid-item w-2 h-1">
    I'm a 2 by 1 rectangle!
  </div>
</div>
```


### Offsets
squid offsets content by using classes that add margin to the element.
By default these classes are named `t-<offset-value>`, `r-<offset-value>`, `b-<offset-value>` and `l-<offset-value>` corresponding to `margin-top`, `margin-right`, `margin-bottom` and `margin-left` respectively. 

For a 2 by 2 square that is left offset by 2:
```html
<div class="row">
  <div class="grid-item w-2 h-2 l-2">
    I'm offset by 2!
  </div>
</div>
```

### Media Queries
With squid you can add (and name) as many breakpoints as you would like. 
By default, squid ships with 3: `sm` , `md` and `lg`.

For a offset-by-1 10x4 rectangle that is offset-by-2 and 8x6 after the medium breakpoint:
```html
<div class="row">
  <div class="grid-item w-10 h-4 l-1 w-8-md h-4-md l-2-md">
    I change sizes!
  </div>
</div>
```
The offset classes include the `0` value for completely removing offsets at specific breakpoints. E.g. `class="l-2 l-0-md"` will remove the left offset after the medium breakpoint.

#### Show/hide on breakpoint
To show and hide elements at specific breakpoints you can utilise `show-<breakpoint>` and `hide-<breakpoint>`.

The `show`-classes will hide an element *before* the specified breakpoint.
The `hide`-classes will hide an element *after* the specified breakpoint.

```html
<div class="row">
  <div class="grid-item w-12 h-1 show-lg">
    I'm visible after the large breakpoint!
  </div>
  <div class="grid-item w-12 h-1 hide-lg">
    I'm visible before the large breakpoint!
  </div>
  <div class="grid-item w-12 h-1 show-sm hide-md">
    I'm visible between the small and medium breakpoint!
  </div>
</div>
```

### Helpers
By default squid ships with a set helpers that helps you layout quickly. They most change flexbox values and margins.
There are reasons not to include the helpers. Maybe you have your own or prefer to use less classes and write more CSS. 

To disable: `$compile-helpers: false`

| Class name               | Function                         |
|--------------------------|----------------------------------|
| .flex                    | `display: flex`                  |
| .align-start             | `margin-right: auto`             |
| .align-end               | `margin-left: auto`              |
| .center-self             | `margin-left: auto` `margin-right: auto` |
| .align-top               | `align-self: flex-start`         |
| .align-bottom            | `align-self: flex-end`           |
| .align-items-end         | `align-items: flex-end`          |
| .align-items-center      | `align-items: center`            |
| .justify-content-between | `justify-content: space-between` |
| .justify-content-end     | `justify-content: flex-end`      |
| .justify-content-center  | `justify-content: center`        | 
| .flex-wrap               | `flex-wrap: wrap`                |
