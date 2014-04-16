# template-epub
## About
Template-epub is a bare-bones template for EPUB3. It uses CodeKit's .kit extension to allow easier editing of the OPF file and updating of shared components.

## Requirements
To use the template you will need the following tools and libraries:

### Required
* [CodeKit](http://incident57.com/codekit/)
* [SASS](http://sass-lang.com)

### Optional
* [Bourbon](http://bourbon.io)

## Getting started

### Adding metadata
Edit `_metadata-master.kit` to set up your default metadata for the ebook. Some of this will import into your package.opf.

If you want to add features such as external fonts, media, etc you can edit the relevant metadata .kit file, then @import them to package.kit.

### content-01.xhtml

This is a test page compiled from content-01.kit and content-01.md.

### Creating a new page
If you're unfamiliar with CodeKit's .kit language, [read this first](http://incident57.com/codekit/kit.php).

1. In *CodeKit > html, create a new .kit file. Say we want to end up with default.xhtml, we create default.kit.
2. (Optional) In *CodeKit > content, create a markdown file for the content of the page. Compile it to *CodeKit > html > content-default.html
3. Import content-default.html into default.kit.

#### Example
Add the following .kit variables and imports. Optionally, you can add local variables to override the master variables in `_metadata-master`.

```html
<!-- $page-id = page-default-html -->
<!-- $page-title = Default HTML -->
<!-- @import metadata-master.kit, 01-header.kit, default.kit, 02-close.kit -->
```
* `$page-id` – added to `<body>` as an id and `<title>`
* @import – creates the document using the .kit or html files you specify. In this example, the page contains:
** metadata-master.kit - global metadata variables
** 01-header.kit – the doctype, `<html>`, `<head>` and opening `<body>` tags
** default.kit - the body content
** 02-close.kit – closing `</body>` and `</html>` tags

### stylesheet.scss
`stylesheet.scss` imports the following files:

#### Local
* `_fonts.scss` – add your @font-face rules here, then add `font-family` names to `_variables.scss`
* `_layout.scss` – base layout styles
* `_variables.scss` – base variables for fonts, colour schemes, etc.

#### External

* `bourbon.scss` (optional) – this automatically imports [Bourbon](http://bourbon.io)

This template also uses the following files from [benmanley/framework-base](https://github.com/benmanley/framework-base)
* `reset.scss` – a bare-bones reset.
* `mixins.scss` – mixins for golden ratios, fonts, properties that use rems but fall back to pixels, plus cross browser support for various properties.
