# Sequencer
> A fast fullscreen image-sequence player

This project is forked from ertdfgcvb/Sequence. The aim is to improve the entire library, 
addding new features and a better performance. Dev branch is not safe for production. Master is the latest
release. 

## Demo:
https://baezor.github.io/sequencer

## How to use:
The minimum paramters are two filenames of an image sequence.
The parser tries to figure out if there are leading zeroes:

```javascript

const s1 = Sequencer.make({
        from : 'pics/pig/DSC04701.JPG',
        to   : 'pics/pig/DSC04775.JPG',
    });

    ...or just a plain numerical sequence:

    const s2 = Sequencer.make({
        from : 'pics/dog/1.png',
        to   : 'pics/dog/100.png',
    });

    All options:

    const opts = {
        canvas           : null,        // a valid canvas element (will be created if null)
        from             : '1.jpg',     // first file of the sequence
        to               : '10.jpg',    // last file of the sequence
        step             : 1,           // increment: to load only even images use 2, etc.
        scaleMode        : 'cover',     // can be: auto, cover, contain as in CSS3,
        direction        : 'x',         // can be: x, -x, y, -y
                                        // and determines the pointer direction,
                                        // applies only if playMode is drag or hover
        playMode         : 'drag',      // can be: none, drag, hover, auto
        loop             : 'loop',      // can be: loop, pong, none
        interval         : 10,          // interval in milliseconds between each frame,
                                        // applies only if playMode is auto,
                                        // if set to zero tries to update at every frame event
        autoLoad         : 'all',       // can be: all, first, none,
                                        // if first or none is used the loading
                                        // needs to be triggered manually with load().
        fitFirstImage    : false,       // resizes the canvas to the size of
                                        // the first loaded image in the sequence
        showLoadedImages : false,       // show images while loading the sequence, 
                                        // may be jumpy because of async laoding <- not a typo
        dragAmount       : 10,          // distance (in pixels) to trigger nextImage(),
                                        // can be < 1, but must be > 0
        hiDPI            : true,        // use HDPI if present
        imageLoad        : function     // callback for each image load
        queueComplete    : function     // callback for queue complete
    };
     };

```
   


## Changelog:

### 2.1
- update to ECMAScript 2015 (aka ES6)
- script is now an ES6 module (may need transpiling for legacy support) and loaded as such in the examples

### 2.0
- multiple instances   
- better parser (automatic leading zeroes detection)
- canvas only (2d)
- incremental drag
- removed default loader (a custom one can be implemented via callback)
- cover frame

## Todo:
- remove 'loop' option (merge with playMode)
- transpiled version for ES5 support
- area hovering     
- accept an image array as parameter
- accept a spritesheet as parameter
- WebGL support
- better touch support

--------------------------------------------------------------------------------
### Author:
- Original: Andreas Gysin | @andreasgysin (twitter)
- Forked repo: Angel Baez
