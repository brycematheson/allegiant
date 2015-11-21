+++
title = "I love to Grunt and Gulp"
date = "2015-02-14T18:50:20-07:00"
+++
(Happy Valentine's Day, ya'll. Get off the computer and go buy something nice for your woman.)

Sometimes I like to pretend that I know stuff, when I really don't. Gulp is one of those things. :)

I need to get better at finding solutions to a lot of the repetitive tasks that I do on a daily basis. Up until now, let's say I was about to push some production code to the web. Of course I needed to minify the CSS first. So I would copy the code, hit up <a href="http://cssminifier.com/" target="_blank">CSS Minifier</a>, paste the code back into my CSS file, and then rename the file, `styles.min.css`. This wouldn't be that big of an issue if I only did it once upon completion of a site. But it never really worked out that way. I'd forget to change a specific style last minute, and then I'd have to copy all of my code into CSS Minifier and do it all again.

Wouldn't it be great if there were a service that did all of this for you, automatically? You're in luck! They're called &#8220;Task Runners&#8221;. I'm going to be focusing on &#8220;Gulp&#8221;, which is a JavaScript task runner, built off of Node.js.

Now, to many of you, you've probably been using a task runner of some sort for years. For a long time, Grunt has been the big name in the game. Not too long ago, Gulp emerged and has been hogging the spotlight. It's not only faster at rendering, but it also has an easier-to-read syntax.

Now, I'm too lazy to reinvent the wheel and write a tutorial on how to install and run gulp. <a href="http://travismaynard.com/writing/getting-started-with-gulp" target="_blank">This guy</a> does a much better job than I could do, anyway.

But I did at least want to post my gulpfile and say how freaking awesome it is. By simply running the `gulp` command, in less than second, I can minify my CSS, JS, and HTML, concatenate multiple files into one, rename them automatically, add in browser prefixes, and then reload the browser window. In less than a second. Boom. Pretty nifty, huh? Additionally, my gulpfile will watch for any changes to those files, and rerun all of those tanks without me doing anything. Dope.

~~~js
var gulp = require('gulp'); 

/**********************************************
****************** Modules ********************
***********************************************/
var sass = require('gulp-ruby-sass'); //Compiles SASS
var autoprefix = require('gulp-autoprefixer'); //Automatically throws in browser prefixes
var minifycss = require('gulp-minify-css'); //Minifies CSS
var rename = require("gulp-rename"); //Renames files to .min after minifying
var minifyhtml = require('gulp-minify-html'); //Minifies the HTML
var concat = require('gulp-concat'); //Concatenates all source files into one file
var uglify = require('gulp-uglify'); //Removes whitespaces from JavaScript
var imagemin = require('gulp-imagemin'); //Compresses images
var livereload = require('gulp-livereload'); //Live reload
var plumber = require('gulp-plumber'); //Error handling

/**********************************************
****************** Functions ********************
***********************************************/

// css auto-prefix, minify, and rename
gulp.task('styles', function() {
    return sass('src/styles/', {style:'expanded'}).on('error', function(handleError){ console.log('Error: There\'s a problem with your SASS, stupid. Fix that shiz.'); })
         .pipe(autoprefix('last 2 versions'))
             .pipe(minifycss())
                .pipe(rename({suffix:'.min'}))
                  .pipe(gulp.dest('build/styles/'))
                      .pipe(livereload());
});

// minify new images
gulp.task('imagemin', function() {
      gulp.src('src/images/*.jpg').on('error', function(handleError){ console.log('Error: There\'s a problem with your images, stupid. Fix that shiz.'); })
          .pipe(imagemin())
              .pipe(gulp.dest('build/images/'));
});

// minify new or changed HTML pages
gulp.task('html', function() {
        gulp.src('src/*.html')
            .pipe(minifyhtml())
                .pipe(gulp.dest('build/'))
                .pipe(livereload());
});

// JS concat, strip debugging and minify
gulp.task('scripts', function() {
        gulp.src('src/scripts/*.js')
            .pipe(concat('script.js'))
                .pipe(uglify())
                    .pipe(rename({suffix:'.min'}))
                        .pipe(gulp.dest('build/scripts/'))
                    .pipe(livereload());
});

/**********************************************
************ Watch & Build Tasks **************
***********************************************/
gulp.task('default', ['styles', 'html', 'scripts', 'imagemin'], function() {
        // watch for CSS changes & minify
        gulp.watch('./src/styles/*.scss', function() {
          livereload.listen();
                 gulp.run('styles');
                 });

        // watch for html &amp; minify
        gulp.watch('./src/*.html', function() {
          livereload.listen();
            gulp.run('html');
                });

        // watch for JS changes
        gulp.watch('./src/scripts/*.js', function() {
          livereload.listen();
            gulp.run('scripts');
                });

        // watch for new images
        gulp.watch('./src/images/*.jpg', function() {
            gulp.run('imagemin');
              });
});
~~~

This isn't even the tip of the iceberg. There are hundreds of gulp plugins, and I have yet to play with the majority of them. But these seem to be the most basic/common plugins, and so far, they've proved invaluable.