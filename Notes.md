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

