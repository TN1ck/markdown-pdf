markdown-pdf [![Dependency Status](https://david-dm.org/alanshaw/markdown-pdf.png)](https://david-dm.org/alanshaw/markdown-pdf)
===

Node module that converts Markdown files to PDFs.

The PDF looks great because it is styled by HTML5 Boilerplate. What? - Yes! Your Markdown is first converted to HTML, then pushed into the HTML5 Boilerplate `index.html`. Phantomjs renders the page and saves it to a PDF. You can even customise the style of the PDF by passing an optional path to your CSS.

Getting started
---

    npm install markdown-pdf

Example Usage
---

Pass markdown-pdf a path to a markdown document or an array of paths and you'll be given back an array of paths to temporary files that contain your converted PDFs.

```javascript
var markdownpdf = require("markdown-pdf")
  , fs = require("fs")

markdownpdf("/path/to/document.md", function (er, pdfs) {
  if (er) return console.error(er)
  
  // Move the pdf from the tmp path to where you want it
  fs.rename(pdfs[0], "/path/to/document.pdf", function() {
    console.log("done")
  })
})
```

### Options

Pass options to markdown-pdf like so:

```javascript
var markdownpdf = require("markdown-pdf")
  , opts = {/* options */}

markdownpdf("/path/to/document.md", opts, function (er, pdfs) {})
```

#### options.phantomPath
Type: `String`
Default value: `Path provided by phantomjs module`

Path to phantom binary

#### options.cssPath
Type: `String`
Default value: `../pdf.css`

Path to custom CSS file, relative to the html5bp directory

#### options.paperFormat
Type: `String`
Default value: `A4`

'A3', 'A4', 'A5', 'Legal', 'Letter' or 'Tabloid'

#### options.paperOrientation
Type: `String`
Default value: `portrait`

'portrait' or 'landscape'

#### options.paperBorder
Type: `String`
Default value: `1cm`

Supported dimension units are: 'mm', 'cm', 'in', 'px'

#### options.renderDelay
Type: `Number`
Default value: `1000`

Delay in millis before rendering the PDF (give HTML and CSS a chance to load)
