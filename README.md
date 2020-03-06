# Minami

A clean, responsive documentation template theme for JSDoc 3. Currently used for
[Tutorbook's open source documentation](https://tutorbook.app/docs). Forked from
[this repository](https://github.com/Nijikokun/minami).

![Minami Screenshot](https://i.imgur.com/rPCIFqT.png)


## Uses

- [Taffy Database](https://taffydb.com/)
- [Underscore Template](https://underscorejs.org/#template)
- [Montserrat](https://fonts.google.com/specimen/Montserrat) & Helvetica Neue


## Install

```bash
$ npm install --save-dev @tutorbook/minami
```


## Usage

Clone repository to your designated `jsdoc` template directory. First make sure
that you update (or remove) our [Algolia
Docsearch](https://docsearch.algolia.com) key and app ID from `tmpl/layout.tmpl`
. Then run:

```bash
$ jsdoc entry-file.js -t path/to/minami
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
  "template": "node_modules/@tutorbook/minami"
}
```


### Example JSDoc Config

```json
{
    "tags": {
        "allowUnknownTags": true,
        "dictionaries": ["jsdoc"]
    },
    "source": {
        "include": ["lib", "package.json", "README.md"],
        "includePattern": ".js$",
        "excludePattern": "(node_modules/|docs)"
    },
    "plugins": [
        "plugins/markdown"
    ],
    "templates": {
        "cleverLinks": false,
        "monospaceLinks": true,
        "useLongnameInNav": false,
        "showInheritedInNav": true
    },
    "opts": {
        "destination": "./docs/",
        "encoding": "utf8",
        "private": true,
        "recurse": true,
        "template": "./node_modules/@tutorbook/minami"
    }
}
```

Specifying a number for `useLongnameInNav` it will be the max number of path
elements to show in nav (starting from Class).


## License

Licensed under the Apache2 license.
