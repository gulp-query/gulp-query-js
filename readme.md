## gulp-query-js
JS plugin for [gulp-query](https://github.com/gulp-query/gulp-query)

Uses [babel](http://babeljs.io/) and [uglify](https://www.npmjs.com/package/gulp-uglify)
```
npm install gulp-query gulp-query-js
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , js = require('gulp-query-js')
;
cocktail(function (query) {
    query.plugins([js])
      .js('src/js/app.js','js/','app')
    
      // Rename and own babel config
      .js('src/js/admin.js','js/undercover.js',{
        babel: {
          presets: ['env']
        }
      })
    
      // Config as object
      .js({
        from: 'src/js/main.js',
        to: 'js/',
        name: 'main'
      })
      
      // Multiple files
      .js(['src/js/app.js','src/js/main.js'],'js/')
      
      // Multiple files and concat
      .js(['src/js/app.js','src/js/main.js'],'js/concat.js')
    ;
});
```
And feel the freedom
```
gulp
gulp --production // For production
gulp watch // Wathing change
gulp js // Only for js
gulp js:app // Only for app.js
gulp js:admin js:main watch // Wathcing change only for admin.js and main.js
...
```

### Options
```javascript
.js({
    name: "new_name", // For gulp js:new_name 
    from: "src/js/app.js", // ["src/js/f1.js", "src/js/f2.js"]
    to: "js/", // set filename "js/concat.js" -- for concat or rename
    source_map: true,
    source_map_type: 'inline',
    full: false, // if set true is without compress in prod
    babel: {
      presets: ['env']
    }
})
```