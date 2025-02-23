# svg-sprite

[![npm version][npm-image]][npm-url] [![npm downloads][npm-downloads]][npm-url] [![Build Status][ci-image]][ci-url] [![Coverage Status][coveralls-image]][coveralls-url]

This file is part of the documentation of *svg-sprite* — a free low-level Node.js module that **takes a bunch of SVG files**, optimizes them and creates **SVG sprites** of several types. The package is [hosted on GitHub](https://github.com/svg-sprite/svg-sprite).


## Grunt & Gulp wrappers

This document aims to compare the use of *svg-sprite* via its [standard API](api.md) with the use of wrappers like the ones for Grunt and Gulp. The following examples are equivalent and have been simplified for the sake of clarity. Prerequisites like the necessary `require` calls or the construction of a [main configuration](configuration.md) object (`config`) have been omitted.

## Standard API

```js
const fs = require('fs');
// Create spriter instance
const spriter = new SVGSpriter(config);

// Add SVG source files — the manual way ...
spriter.add('assets/svg-1.svg', null, fs.readFileSync('assets/svg-1.svg', 'utf-8'));
spriter.add('assets/svg-2.svg', null, fs.readFileSync('assets/svg-2.svg', 'utf-8'));
/* ... */

// Compile sprite
spriter.compile((error, result) => {
    /* ... Write `result` files to disk or do whatever with them ... */
});
```

## Grunt task (using [grunt-svg-sprite](https://github.com/svg-sprite/svg-sprite))

```js
// svg-sprite Grunt task
grunt.initConfig({
    svg_sprite: {
        minimal: {
            src: ['assets/**/*.svg'],
            dest: 'out',
            options: config
        }
    }
});
```

## Gulp task (using [gulp-svg-sprite](https://github.com/svg-sprite/gulp-svg-sprite))

```js
// svg-sprite Gulp task
gulp.src('assets/*.svg')
    .pipe(svgSprite(config))
    .pipe(gulp.dest('out'));
```


[npm-url]: https://www.npmjs.com/package/svg-sprite
[npm-image]: https://img.shields.io/npm/v/svg-sprite
[npm-downloads]: https://img.shields.io/npm/dm/svg-sprite

[ci-url]: https://github.com/svg-sprite/svg-sprite/actions?query=workflow%3ATests+branch%3Amain
[ci-image]: https://img.shields.io/github/actions/workflow/status/svg-sprite/svg-sprite/test.yml?branch=main&label=CI&logo=github

[coveralls-url]: https://coveralls.io/github/svg-sprite/svg-sprite?branch=main
[coveralls-image]: https://img.shields.io/coveralls/github/svg-sprite/svg-sprite/main
