# purescript-numeric-hierarchy-guide

Sources for <http://purescript-numeric-hierarchy.harry.garrood.me/>.

Compiled using Sphinx. I have been developing on Ubuntu using the default version from the Ubuntu repositories; install like this:

```
$ sudo apt install python3-sphinx
```

At the time of writing, on Ubuntu 16.04, this gets you Sphinx v1.3.6. The
hosting is done by Read The Docs; I'm not sure what version of Sphinx they're
using, but it seems to work fine between both environments.

To rebuild, change to the project directory and run:

```
$ make html
```

The html will be written to the `_build` directory; I recommend spinning up a
simple HTTP server in there to use whilst developing. The npm package `serve`
can provide this.
