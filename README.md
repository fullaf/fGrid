# fGrid · Sass Responsive Grid System
[![Build Status](https://travis-ci.org/fullaf/fgrid.svg?branch=master)](https://travis-ci.org/fullaf/fgrid) [![Gitter](https://badges.gitter.im/Join Chat.svg)](https://gitter.im/fullaf/fgrid?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

fGrid is a responsive and customisable grid system for Sass styled websites. It's built to be flexible and small and is suitable for a wide range of projects.

Please Note: We're currently specifying and building fGrid, docs are sparse and there's probably some nasty bugs. If you spot issues please report them!

See http://fgrid.fullaf.com for more details.

## Dependencies
Some of the fancy bits of fGrid need [Bourbon](http://bourbon.io/), and frankly if you're using fGrid you should use Bourbon, it's awesome!

Ensure Bourbon is included in your Sass files before fGrid and everything should work.

## Usage

The easiest way to get fGrid is with [Bower](http://bower.io/), simply run `bower install fgrid` in your project directory and add `@import "bower_components/fgrid/fgrid"` below your bourbon include line.

Importing Bourbon is up to you. If you've installed fGrid using Bower putting this line above the fGrid import line will do the trick: `@import "bower_components/bourbon/dist/bourbon"`

So now your main Sass file looks like:

```
@import "bower_components/bourbon/dist/bourbon"
@import "bower_components/fgrid/fgrid"

# All your styling below here
```

## Testing

fGrid testing comprises installing dependencies and compiling the project to ensure building is successful. We use Travis for this.

## Documentation

Examples given will be in SASS, SCSS may be useful to add later. Converting to SCSS essentially means adding curly braces to selectors and semicolons at the end of lines.

### Introduction

The two main components of fGrid are the grid system and the responsive mixins. Bits we find useful when building fGrid powered sites are likely to be included as well.

fGrid can be customised by editing the _settings.sass file

### Responsive Mixins

fGrid defines six responsive breakpoints:

- `mob-port` Mobile portrait (320px)
- `mob-land` Mobile landscape (480px)
- `tab-port` Tablet portrait (768px)
- `tab-land` Tablet landscape (1024px)
- `med-desk` Medium desktop (1200px)
- `widescreen` Widescreen desktop (1490px)

The mobile and tablet breakpoints by default have no restriction on device they will activate on small desktop as for the enviroment this will likely give the best experience.

Three mixins are available for using these breakpoints:

- `@include respond-up(<BREAKPOINT>)` Will match this size and above
- `@include respond-down(<BREAKPOINT>)` Will match this size and below
- `@include respond-to(<BREAKPOINT>)` Will match this size only

If you are following a mobile first methodology you'll probably only want to use `respond-down` when adding mobile only styling.

#### Example
The following will give a multi-line nav on mobile and single-line on tab-port and above. When mob-land only we increase the font-size.

**SASS**
```
header
    li
        font-size: 16px
        @include respond-to(mob-land)
            font-size: 20px
        @include respond-up(tab-port)
            display: inline-block
```

