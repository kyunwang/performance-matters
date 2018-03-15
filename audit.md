# The audit documentation

This documents documents the audit

## Table of Contents
- [Settings & Tools](#setting-&-tools)
	- [Settings](#settings)
	- [Browser](#browser)
	- [Tools](#tools)
- [First snapshot](#first-snapshot)
- [Process](#process)
	- [Images](#images)
	- [Minifying](#minifying)
	- [Critical Css](#critical-css)
	- [Font loading](#font-loading)
- [Result](#result)

## Settings & Tools
The used settings and tools:

### Settings
- Disable cache 
- Throttle: 3G Slow
- 

### Browser
- Google Chrome

### Tools
- Google Chrome Devtools
	- Network
	- Timeline
	- Audits

- Using ImageOptim to compress images (not the most optimal but pretty good one0)


## First snapshot

Snapshot on from the homepage.

**Stats:**

Network tab
- 19 Requests
- 1.2 MB Transfered
- Finish: 30.95s
- DOMContentLoaded: 14.02s
- Load: 30.96s

![before summary][b-summary]

![before performance][b-perf]

![before opportunity][b-opp]

![before network][b-network]

![before details][b-details]

![][]

The biggest issues are the **images** and **fonts**

The Jpegs and Fonts take around 15 to 18 seconds each to get downloaded.

CSS and JS can be minified (uglified too)

- First paint happens around 12125ms.
- Load of first content around 15050ms
- The first font around 22775ms
- The second font around 23375ms

**Waterfall**

The loading sequence:
- HTML
- CSS
- JS
- Images
- Fonts
- Images

### Font loading

### Process
Here the process will be documented.

I started with making a back up after the first audit of the not optimised state in branch `first-snap`. Each optimisation will be based on this state and be merged toghether in the `master` branch.

#### Images
The images are one of the biggest bottlenecks so they will be compressed by using the program `ImageOptim` on mac.

Said images reside in `src/assets/img`.

Using `ImageOptim` didn't seem to shave off any size. I reckon that they have already gone throught the same compression technology. That being said, I will be using [compressjpeg.org](http://compressjpeg.com/) and [http://compresspng.com/](http://compresspng.com/) because in my experience they have always exceeded the performance of `ImageOptim`.

Average saved 50% from jpeg and 25% from png files.

**Stats**
Network tab
- 17 Requests
- 879 KB Transfered
- Finish: 22.98s
- DOMContentLoaded: 13.30s
- Load: 22.98s

Compressing the images saved around *7seconds* from the total loadtime.

### Minifying

Minifying the CSS and JS files:

CSS:
- fonts.css
- docs.css
- bootstrap.css

JS:
- bootstrap.js
- ie10-viewport-bug-workaround.js

**Stats:**

Network tab
- 17 requests
- 1.2 MB Transfered
- Finish: 29.86s
- DOMContentLoaded: 15.59s
- Load: 29.87s

Only a one second save won.

### Critical Css

Applied critical css suping the npm package `Critical` and running it through `Gulp`.
Why `Gulp`? Because the `CLI` documentation lacks and misses some options.

The `Critical` plugin has been run over `_base/layout1.html` to `_base/layout.html`.

I am using `layout1.html` as a base as it is the original file.

Do not forget to import the `loadcss.js` file

**NOTE**: 
The output will create an error in the for the template engine.

Change

```
// This
<body {%="" block="" body_attributes="" %}{%="" endblock="" %}="">

// To this
<body {% block body_attributes %}{% endblock %}>
```

Network tab
- 17 requests
- 825 kb Transfered
- Finish: 22.13s
- DOMContentLoaded: 16.79s
- Load: 22.13s

Around 9 seconds have been won.

### Font loading

Adding font-swap and a script using FontFaceObserver to asynchronously load in fonts.

Network tab
- 17 requests
- 1.2 mb Transfered
- Finish: 30.02s
- DOMContentLoaded: 15.77s
- Load: 30.02s

Almost saved 1 second


## Result

The result till now after merging all the changes:

Network tab
- 19 requests
- 833 kb Transfered
- Finish: 21.60s
- DOMContentLoaded: 12.14s
- Load: 21.61s

![after summary][a-summary]

![after performance][a-perf]

![after opportunity][a-opp]

![after network][a-network]




<!-- - [x] critical css -->
<!-- - [] font loading -->
<!-- - [x] image optimalisaties -->
<!-- - [] asynchroon laden van assets -->




[b-summary]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/summary.png
[b-perf]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/perf.png
[b-opp]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/opp.png
[b-network]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/network.png
[b-details]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/details.png

[a-summary]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/after/summary.png
[a-perf]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/after/perf.png
[a-opp]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/after/opp.png
[a-network]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/after/network.png
[.]: .
