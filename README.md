# Bootstrap Margin Grid

### Installation
- Add `bootstrap-margin-grid.css` to your project and use classes.
- Or add `bootstrap-margin-grid.scss` to your project and generate columns based on simple fractions on-the-fly.

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

Want background color on rows?

```css
.my-row:before {
  background: tomato;
}
```

Don't want to use `:before` trickery? Wrap your row in a superfluous element and apply bg color to it.

```html
<div class="container">
  <div class="my-background-color">
    <div class="row">
      <div class="col-4">...</div>
      <div class="col-4">...</div>
      <div class="col-4">...</div>
    </div>
  </div>
</div>
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
  <div class="row">
    <div class="col-6">1</div>
    <div class="col-6">
      <div class="row">
        <div class="col-6">1a</div>
        <div class="col-6">1b</div>
      </div>
    </div>
  </div>
</div>
```

https://youtu.be/ueZ6tvqhk8U?t=18

### Why hasn't Bootstrap fixed this?
Objectively margin-based grids are better, but the assumption is their userbase won't be able to figure out how to upgrade, or this "minor" upgrade isn't worth the fundamental change. And @mdo personally likes padding-based grids because they just make more sense to him.

Try out this grid and when you realize it's Just Better™ pester the Bootstrap people (Issues, Tweets, etc.) into officially changing their grid (Foundation and such will follow the leader) or at least offering a real counter argument to it.

### You seem salty?
A little bit. I've had to work with Bootstrap and Foundation for many years on various projects. This always bugged me and I don't think the reasons not to change are good enough.
