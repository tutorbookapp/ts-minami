# Minami

A clean, responsive documentation template theme for
[TypeDoc](https://typedoc.org) (adapted from our [original Minami
template](https://github.com/tutorbookapp/minami) for [JSDoc
3](https://jsdoc.app)). Currently used for the [COVID Tutoring Initiative's open 
source documentation](https://covidtutoring.org/docs/). Originally forked from 
[this repository](https://github.com/Nijikokun/minami).

![Minami Screenshot](https://i.imgur.com/rPCIFqT.png)

## Uses

- [Taffy Database](https://taffydb.com/)
- [Underscore Template](https://underscorejs.org/#template)
- [Montserrat](https://fonts.google.com/specimen/Montserrat) & Helvetica Neue

## Install

```bash
$ npm install --save-dev @tutorbook/ts-minami
```

## Usage

Clone repository to your designated `jsdoc` template directory. First make sure
that you update (or remove) our [Algolia
Docsearch](https://docsearch.algolia.com) key and app ID from `tmpl/layout.tmpl`
. Then run:

```bash
$ jsdoc entry-file.js -t path/to/ts-minami
```

### Node.js Dependency

In your projects `package.json` file add a generate script:

```json
"scripts": {
  "generate-docs": "node_modules/.bin/jsdoc --configure .jsdoc.json --verbose"
}
```

In your `.jsdoc.json` file, add a template option.

```json
"opts": {
  "template": "node_modules/@tutorbook/ts-minami"
}
```

## License

Licensed under the Apache2 license.
