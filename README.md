# Minami

A clean, responsive documentation template theme for
[TypeDoc](https://typedoc.org) (adapted from our [original Minami
template](https://github.com/tutorbookapp/minami) for [JSDoc
3](https://jsdoc.app)). Currently used for the [COVID Tutoring Initiative's open 
source documentation](https://covidtutoring.org/docs/). Originally forked from 
[this repository](https://github.com/Nijikokun/minami).

![Minami Screenshot](https://i.imgur.com/rPCIFqT.png)

## Developing

This project has been put on the back-burner for now (we just decided to use the
[default Typedoc theme](https://github.com/TypeStrong/typedoc-default-themes)
for now (even though it looks a lot worse than this Minami theme)).

But, we **will** be picking it back up again sooner or later, so here's some
practical advice on how to move forward (and documentation that the [Typedoc
website](https://typedoc.org/docs) seems to be missing).

### Impromptu Roadmap

Stuff that still needs to get done:
- Implement a `theme.js` file that follows the Typedoc theme specifications (see
  below).
- Adapt that theme class (contained in `theme.js`) to work with our Minami
  template.
- Add support for multiple method signatures (right now, we just show one in the
  title of the method specification section).

Stuff that'd be nice to have done:
- Add configurable support (i.e. no need to change the source code) for
  Intercom, Google Analytics, and Algolia Docsearch.
- Build custom Slack bot that searches that configured Algolia Docsearch index;
  such a bot could be used to search and reference documentation from within
  Slack.

### Theme Specifications

From the doc comments in `typedoc/src/lib/output/theme.ts`:

A theme defines the logical and graphical output of a documentation. Themes are
directories containing a `theme.js` file defining a [[BaseTheme]] subclass and a
series of subdirectories containing templates and assets. You can select a theme
through the `--theme <path/to/theme>` commandline argument.

The theme class controls which files will be created through the [[BaseTheme.getUrls]]
function. It returns an array of [[UrlMapping]] instances defining the target files, models
and templates to use. Additionally themes can subscribe to the events emitted by
[[Renderer]] to control and manipulate the output process.

The default file structure of a theme looks like this:
- `/assets/`<br>
  Contains static assets like stylesheets, images or javascript files used by the theme.
  The [[AssetsPlugin]] will deep copy this directory to the output directory.
- `/layouts/`<br>
  Contains layout templates that the [[LayoutPlugin]] wraps around the output of the
  page template. Currently only one `default.hbs` layout is supported. Layout templates
  receive the current [[PageEvent]] instance as their handlebars context. Place the
  `{{{contents}}}` variable to render the actual body of the document within this template.
- `/partials/`<br>
  Contains partial templates that can be used by other templates using handlebars partial
  syntax `{{> partial-name}}`. The [[PartialsPlugin]] loads all files in this directory
  and combines them with the partials of the default theme.
- `/templates/`<br>
  Contains the main templates of the theme. The theme maps models to these templates through
  the [[BaseTheme.getUrls]] function. If the [[Renderer.getTemplate]] function cannot find a
  given template within this directory, it will try to find it in the default theme
  `/templates/` directory. Templates receive the current [[PageEvent]] instance as
  their handlebars context. You can access the target model through the `{{model}}` variable.
- `/theme.js`<br>
  A javascript file that returns the definition of a [[BaseTheme]] subclass. This file will
  be executed within the context of TypeDoc, one may directly access all classes and functions
  of TypeDoc. If this file is not present, an instance of [[DefaultTheme]] will be used to render
  this theme.
