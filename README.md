<div align="center">

<img src="assets/vura.svg" alt="Vura logo" width="128" height="128">

# Vura Docs

**Documentation site for the Vura programming language.**

![Version](https://img.shields.io/badge/version-0.1.0-5980a6?style=flat-square)
![Status](https://img.shields.io/badge/status-WIP-d14a08?style=flat-square)
![License](https://img.shields.io/badge/license-Unlicense-lightgrey?style=flat-square)
![JavaScript](https://img.shields.io/badge/vanilla-JavaScript-f7df1e?style=flat-square&logo=javascript&logoColor=black)
![Target](https://img.shields.io/badge/target-LLVM-262d3a?style=flat-square&logo=llvm&logoColor=white)

[Read the docs](holzfa.github.io/Vura-Docs/) · [Report an issue](../../issues)

</div>

---

## About

Vura is a statically typed, natively compiled language with Kotlin-style syntax, but no virtual machine or garbage collector. This repository holds its documentation site.

The site is a static renderer. All content lives in JSON files, and the page is built in the browser from templates, with no dependencies or build needed. You can re-use the source for this site anywhere and without permission.

## Features

- **JSON driven**: every document is a JSON file, the site just renders it
- **Template based**: one HTML template per block type
- **Search**: full text search across all documents and sections
- **Syntax highlighting**: built in highlighter for Vura code blocks
- **Variables**: define a variable once, use `{{name}}` everywhere
- **Link validation**: dead links and duplicate ids are reported in the console
- **Responsive**: collapsible navigation on small screens

## Project structure

```
.
├── index.html            # initial html to load the scripts
├── site.json             # manifest: title, icon, variables, document list
├── content/              # one JSON file per document
├── templates/            # one HTML template per block type; the template name is inferred from the file name
├── src/
│   ├── app.js            # routing, navigation, search wiring
│   ├── parser.js         # JSON in, document tree out (no DOM)
│   ├── render.js         # tree plus templates in, HTML out
│   ├── search.js         # index and ranking
│   └── highlight.js      # Vura syntax highlighting
├── css/style.css
├── assets/               # logo and file icons
└── specifications/       # site format or other specs for this site
```

## Writing content

Documents are described by the format in [`DOC_CONTENT.md`](specifications/DOC_CONTENT.md). A minimal section looks like this:

```json
{
  "id": "#hello-world",
  "title": "Hello, Vura",
  "content": [
    "Every program starts at a function called <code>main</code>."
  ]
}
```

To add a document, create a file in `content/` and register it in `site.json`:

```json
{ "file": "content/guide.json", "title": "Guide" }
```

## Deployment

Pushes to `main` are deployed to GitHub Pages by [`.github/workflows/static.yml`](.github/workflows/static.yml). The whole repository is uploaded as is.

## License

Released into the public domain under the [Unlicense](LICENSE).
