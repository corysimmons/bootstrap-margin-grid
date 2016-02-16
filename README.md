# Bootstrap Margin Grid

### Installation
- Add `bootstrap-margin-grid.css` to your project and use classes.
- Or add `bootstrap-margin-grid.scss` to your project and generate columns based on simple fractions on-the-fly.

### Bower
- `bower i bootstrap-margin-grid`

### Usage
Works with same markup as Bootstrap:

```html
<div class="container">
  <div class="row">
    <div class="col-4">...</div>
    <div class="col-4">...</div>
    <div class="col-4">...</div>
  </div>
</div>
```

...except it produces margins instead of padding.

Want background color on rows? Wrap your row in an element and apply bg color to it. This sucks but is still better than nesting a superfluous element inside of every single column.

```html
<div class="container">
  <div class="bg">
    <div class="row">
      <div class="col-4">...</div>
      <div class="col-4">...</div>
      <div class="col-4">...</div>
    </div>
  </div>
</div>
```

```css
.bg {
  background: tomato;
}
```

### SCSS Usage
\* If this gets any attention I'll match these to Bootstrap's mixins.

```scss
.custom-container {
  @include container($max-width: 0, $padding: $grid-gutter-width);
}

.custom-row {
  @include row();
}

.custom-column {
  @include column(1, 2); // produces a column that takes up 1/2 its row
}
```

### Why?
With padding-based grids (Boostrap, Foundation, etc.) if you want background color on rows, you need to nest an element inside each column.

This bloats markup quickly, especially when you need nested grids. For instance, a 2-column grid with a 2-column grid inside of one of the columns (not a crazy thing to want) looks like this with Bootstrap's grid:

```html
<div class="container">
  <div class="row">
    <div class="col-sm-6">
      <div>1</div>
    </div>
    <div class="col-sm-6">
      <div>
        <div class="row">
          <div class="col-sm-6">
            <div>1a</div>
          </div>
          <div class="col-sm-6">
            <div>1b</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

Notice all the superfluous `<div>`s. This also still leaves row's overhanging their parent.

Can you imagine how insane this gets when you have real world project?

Here's a margin-based approach.

```html
<div class="container">
  <div class="bg">
    <div class="row">
      <div class="col-6">1</div>
      <div class="col-6">
        <div class="bg">
          <div class="row">
            <div class="col-6">1a</div>
            <div class="col-6">1b</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

https://youtu.be/ueZ6tvqhk8U?t=18

Less markup, better results, same markup scheme. There's no reason Bootstrap shouldn't switch over to margin grids.

### Caveats
I haven't tested to see if this is a drop-in replacement to Bootstrap's grid system. In fact, I'm pretty sure it's not.
If this project gets popular I'll match all this stuff to Bootstrap perfectly so you actually can drop-in replace
(assuming Bootstrap isn't heavily coupled to their padding-based grid -- lemme know if it is).
