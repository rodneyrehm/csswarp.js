# Notes On Fixing Things #

Issues with the project itself:

* Use [SemVer](http://semver.org/) to tag releases - currently not a single tag is available
* Unit test the math components
* Provide online docs and demos using `gh-pages` - as addition to [http://csswarp.eleqtriq.com/](http://csswarp.eleqtriq.com/)
* link to everything in the README.md
* See [Github Flavored Markdown](http://github.github.com/github-flavored-markdown/) to see how inline code examples should be formatted

Issues with the code:

* See FIXME comments `src/csswarp.0.6.js` 
* focus on making code testable
* group / chunk DOM access to avoid major reflow chains (see chrome web inspector for details)
* reduce garbage collection overhead

Restructure code into managable components:

* `WarpMachine` performs basic configuration stuff, controlling the following modules
* `TextShadow` parse and mutate `text-shadow`, split into DOM-read / write groups
* `TextMetrics` split text into letter DOM elements and identify their metrics (dimensions, actually), actual DOM output handle
* `WarpCircle` performs position (angle, skew) calculation on `TextMetrics` to place letters on a circle (math only)
* `WarpBezier` performs position (angle, skew) calculation on `TextMetrics` to place letters on a bezier curve /(math only)

the goal is to break up the code into smaller chunks of related functions. The functions identifying and calculating something (DOM-read) are to be seperated from those that write to the dom. If a function needs to write to the dom in order to read from it, it must first loop all writers, then reads, then resets. That way reflows can be reduced to 2 per run (instead of 2 * letters).

