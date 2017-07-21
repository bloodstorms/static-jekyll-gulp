static-jekyll-gulp
==================

**Features:**

+ Jekyll
+ Gulp
+ SCSS + PostCSS
+ LostGrid &amp; Autoprefixer (PostCSS)
+ Asset compilation (images, svg, javascripts, stylesheets)

**Requirements:**

+ Ruby
+ Node.js
+ Yarn
+ Gulp

### Where things go

Place all of your assets in `_assets`:

`$ tree _assets`

```
_assets/
├── images
│   └── sample.jpg
├── js
│   └── application.js
├── scss
│   └── application.scss
└── svg
    └── sample.svg
```

Files with matching extensions will be watched and compiled into `assets` so Jekyll will make them available in the final build and keep compiled versions out of source control.

### How would you add Bootstrap?

Add Bootstrap to the include paths in `gulpfile.babel.js`. 

`$ yarn add bootstrap@4.0.0-alpha.6 tether jquery --dev`

```
const includePaths = {
  js: [
    './node_modules/jquery/dist/jquery.js',
    './node_modules/tether/dist/js/tether.js',
    './node_modules/bootstrap/dist/js/bootstrap.js'
  ],
  stylesheets: [
    './node_modules/bootstrap/scss/'
  ]
}
```

1. This will automatically include any referenced javascript files in application.min.js.
2. This will only add SCSS paths into the `@import` mixin. You will need to import any referenced files in application.scss.

### Commands

**`yarn start`**  
Start jekyll and gulp.  

**`yarn gulp:watch`**  
Start gulp.  

**`yarn gulp:js`**  
Compile and watch js files.  

**`yarn gulp:sass`**  
Compile and watch scss files.  

**`yarn gulp:svg`**  
Compile and watch svg files.  

**`yarn gulp:images`**  
Compile and watch image files.  

**`yarn jekyll:serve`**  
Start jekyll.  

**`yarn jekyll:build`**  
Run jekyll build with current assets.  

**`yarn build`**  
Build for production.  


### Known bugs

Gulp/filesystem watcher doesn't recongize new files and you must restart gulp/jekyll.
