## Guide for SASS/CSS styles.

We are using SASS to manage our CSS and utility classes generation.

In the `sass/styles.scss` file, we have a object like this, that contains all of the colors available to us.

```scss
$colors: (
  // AQUA
  aqua-1: rgb(36, 180, 179),
  aqua-2: rgb(255, 255, 255),
  aqua-4: rgb(214, 255, 241),
  aqua-6: rgb(79, 204, 190),
  aqua-7: rgb(128, 225, 215),
  aqua-8: rgb(4, 98, 112),
  aqua-9: rgb(0, 70, 79),
  //   CORAL
  coral-1: rgb(255, 118, 113),
  coral-2: rgb(255, 236, 233),
  coral-4: rgb(255, 167, 150),
  coral-5: rgb(250, 137, 135),
  coral-6: rgb(232, 111, 111),
  coral-7: rgb(221, 77, 84),
  //   MUSTARD
  mustard-1: rgb(237, 191, 85),
  mustard-2: rgb(242, 223, 181),
  //   GRAY
  gray-1: rgb(233, 248, 248),
  gray-2: rgb(196, 211, 211),
  gray-3: rgb(141, 156, 156),
  gray-4: rgb(88, 103, 103),
  // COMMON
);
```


Now, we can run loops on this SASS Map and perform some action.

For example, to create Custom Properties (aka CSS Variables), we are using the below method.

```scss
:root {
  @each $name, $color in $colors {
    --#{$name}: #{$color};
  }
}
```

Here, we are generating custom properties by looping over all the items in `$colors` map.

Similarly, we are using `background-color` and `color` related utility styles using below function.

```scss
@each $name, $color in $colors {
  .bg-#{$name} {
    background-color: $color !important;
  }
}
```


```scss
@each $name, $color in $colors {
  .text-#{$name} {
    color: $color !important;
  }
}
```



After all, we have component specific styles for things like header and footer.


```scss
.zuno-header {
  background-color: #fff !important;
  color: var(--aqua-9) !important;
}

// Footer
.zuno-footer {
  background-color: var(--aqua-1) !important;
  color: #fff !important;
}
```



## Add/Remove or Edit the Colors

In case, you want to edit, add or remove any colors, simply do that in the `colors` map available on the top of the  `sass/styles.scss` file.


## Usage

we can use the generated classes on React/HTML elements/components to change the background color.

```html
 <button class="bg-aqua-9 text-gray-1">Example Button</button>
 ```

 ```html
  <footer class="zuno-footer" style="padding: 1.5rem 1rem; text-align: center;">
            Footer
  </footer>
```


## Available commands.

`npm run dev` - Use this command to test run the SCSS -> CSS conversion. CSS file will be updated on the file content changes inside `sass/styles.scss`.

`npm run build` - Use this command to build the minified CSS, that we can use in production through CDN.