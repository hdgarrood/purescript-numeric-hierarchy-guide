# purescript-numeric-hierarchy-guide

Sources for <https://a-guide-to-the-purescript-numeric-hierarchy.readthedocs.io/en/latest/>.

## Status

This guide is currently in a pre-alpha stage. In particular, it is very
incomplete. If you would like to provide feedback at this stage I'd be very
grateful to receive it.

Please don't start sharing links to this publicly yet, though; I'd prefer to
wait until it's more complete.

ReadTheDocs builds the HTML from what's in the `published` branch; the `master`
branch will often be slightly ahead of `published`, containing material that
I feel is not quite ready to be published yet.

If you read through an earlier version of this guide and want to see what has
changed in the meantime, GitHub has a [compare
view](https://help.github.com/articles/comparing-commits-across-time/) which
you can use. For example, [this page compares what's in the `published` branch now with what
`published` looked like 2 days ago](https://github.com/hdgarrood/purescript-numeric-hierarchy-guide/compare/published@%7B2day%7D...published).

## Contributions

I am very happy to receive feedback to help improve this guide - so please feel
free to email me or open issues.

However, please **do not send me pull requests**. I have decided to not accept
contributions because I would like to retain full copyright ownership of this
work, in case I ever want to publish it as a book or anything like that.

## License

[![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

This work is licensed under [CC BY-NC-SA 4.0][] — that is, the Creative Commons
Attribution-NonCommercial-ShareAlike 4.0 International License. This means you
are free to copy and redistribute it as well as make changes, but you must give
credit, link to the license, and indicate if changes were made. The license
also forbids commercial use.

Note that the work is not necessarily exclusively licensed under CC BY-NC-SA
4.0. In particular, if you're worried about whether your use of it counts as a
commercial use please contact me and we'll probably be able to sort something
out.

[CC BY-NC-SA 4.0]: https://creativecommons.org/licenses/by-nc-sa/4.0/

## Working on this locally

*this is really just a note for me, please see the above paragraph re:
contributions*

Compiled using Sphinx. I have been developing on Ubuntu using the default
version from the Ubuntu repositories; install like this:

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
