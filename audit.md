# The audit documentation

This documents documents the audit

## Table of Contents
- [Settings & Tools](#setting-&-tools)
	- [Settings](#settings)
	- [Browser](#browser)
	- [Tools](#tools)
- [First snapshot](#first-snapshot)
- [](#)

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
- 19 requests
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





[b-summary]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/summary.png
[b-perf]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/perf.png
[b-opp]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/opp.png
[b-network]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/network.png
[b-details]: https://github.com/kyunwang/performance-matters/blob/master/docs/images/before/details.png
[.]: .
