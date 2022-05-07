# CELSIUS TO FARENHEIT

Utility script to build HTML documents - Appends scripts and styles, removes debug parts, append HTML partials, template options, etc.

## Installation

Install this script as a dev dependency

```bash
$ npm install html-build --save-dev
```

## Usage

### CLI

Add your build script to your `package.json` `scripts`:

```json
{
  "scripts": {
    "build-html": "html-build -c config.js index.html samples/"
  }
}
```

Create a configuration file ([more informations][doc-options]):

```javascript
module.exports = {
  beautify: true,
  prefix: "//some-cdn",
  relative: true,
  basePath: false,
  scripts: {
    bundle: ["scripts/*.js", "!**/main.js"],
    main: "scripts/main.js",
  },
  styles: {
    bundle: ["css/libs.css", "css/dev.css"],
    test: "css/inline.css",
  },
  sections: {
    views: "views/**/*.html",
    templates: "templates/**/*.html",
    layout: {
      header: "layout/header.html",
      footer: "layout/footer.html",
    },
  },
  data: {
    // Data to pass to templates
    version: "0.1.0",
    title: "test",
  },
};
```

Then run your script:

```bash
$ npm run build-html
```

### Programmatically

```javascript
var htmlBuild = require("html-build");
htmlBuild.build("index.html", "samples/", {
  /* config */
});
```
