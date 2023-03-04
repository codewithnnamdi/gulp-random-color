# gulp-random-color
To use this plugin, you can include it in your Gulpfile and call it with the gulp.src() method. Here's an example:

javascript

const gulp = require('gulp');
const randomColor = require('./gulp-random-color');

gulp.task('default', function() {
  return gulp.src('src/**/*.html')
    .pipe(randomColor({ placeholder: '__COLOR__' }))
    .pipe(gulp.dest('dist'));
});

In this example, we use the gulp.src() method to select all HTML files in the src/ directory and its subdirectories. We then pipe the files through our randomColor plugin, passing the placeholder option to specify the placeholder text to be replaced with the generated color. Finally, we write the transformed files to the dist/ directory using the gulp.dest() method.
