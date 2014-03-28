##How to use gist-embed to spice up code snippets on your blog

#### Include jQuery and gist-embed src:

```html
  <head>
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
    <script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/gist-embed/1.6/gist-embed.min.js"></script>
  </head>
```

#### Add an HTML element to your page with a data attribute in the following format, where `<gist-id>` should be replaced with the id of your gist:

```html
  <code data-gist-id="<gist-id>"></code>
```

####Examples
See http://blairvanderhoof.com/gist-embed/ for all possible ways to use gist-embed:
* Including a single gist
* Including individual files from a gist
* Including specific line numbers from a gist
* Removing all line numbers from a gist
* Removing the footer from a gist
* Highlight lines from a gist

####FAQ
#### How do I configure line numbers?
* You can put a single number like `"1"`, a range like `"2-5"`, single line numbers separated with commas like `"11,20"`, or a mix of both like `"2-5,11,10-14,20"`

#### Why does my gist-embed have incorrect styling?
* It may be because the HTML element you are using has pre-existing styles either from the native browser or from a stylesheet include that you don't have control over.
* You can avoid this by using a generic HTML element such as `div` instead of `code` as version 1.4 now targets all elements that have a data-gist-id attribute regardless of their tag name.

#### How do I highlight line numbers?
* Use the same pattern for line numbers as data-gist-line, but use the attribute data-gist-highlight-line

###Change log

####Version 1.7 (March 28, 2014)
* Merged pull request https://github.com/blairvanderhoof/gist-embed/pull/20 to highlight lines first before filtering.  Thanks Microdog!

####Version 1.6 (Dec 22, 2013)
* Allow private gists by not checking the type of id passed in as private gists can start with letters or numbers
* Print error statement to html for easier debugging

####Version 1.5 (Dec 11, 2013)
* You can now highlight individual lines with the same syntax used in `data-gist-line` but now using the `data-gist-highlight-line` attribute
    * Merged and cleaned up https://github.com/blairvanderhoof/gist-embed/pull/16
    * Thanks https://github.com/luanmuniz !
* Added a test.html for easier testing
* Fixed some lingering issues with linting such as a global 'head' variable, and mixed double vs. single quotes.

####Version 1.4 (Dec 2, 2013)
* Changed to use `$("[data-gist-id]")` as a more general selector that works with any element, not just `code` tags. Performance should not be affected: http://jsperf.com/gist-embed

####Version 1.3 (July 17, 2013)
* Github changed their stylesheet property to be relative instead of absolute. Updated gist-embed accordingly to allow for these kinds of changes in the future.

####Version 1.2 (March 22, 2013)
* **Breaking change**:
  * Removed code elements with id attributes of `gist-` from being parsed.  You must use `data-gist-id` and specify an integer specifying the id of your gist.
  * Do not use `gist-` for the value of `data-gist-id`, only the value of the gist id is needed.
  * Rewrote the data attribute names.  Now all attributes are using a `data-gist-` namespace for all attributes. Please see example.html for options.
  * Do not point directly to gist-embed from github.  Host your own version so that if breaking changes are introduced, your websites won't be affected.

####Version 1.1 (March 20, 2013)
* **Breaking change**:
 * Using the id attribute of your code element to specify the gist id is **no longer accepted**.  You must now use a data attribute to specify the gist id.  See above for an example.
  * The reason for this change is that it is not proper HTML markup to have multiple DOM elements with the same id attribute on the same page and that it could lead to conflicts when including the same gist in multiple areas.
  * For the meantime, I will allow for both methods so anyone using this code from github directly won't have broken gists on their page.  I plan to deprecate this in the next month.
* Other changes:
 * Cleaned up example.html to include all possible ways to use gist-embed.
 * Thanks to https://github.com/kashif-umair for providing a way to remove the gist footer, remove all line numbers, and specify line number ranges.
