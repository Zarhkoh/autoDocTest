# Guide

Un module Node.js pour charger récursivement un répertoire de fichiers YAML, JSON et Markdown dans un objet JavaScript.

## Installation

```
npm install @github-docs/data-directory
```

## Usage

Étant donné l'arborescence de fichiers suivante:

```
$ tree data
data
├── bar.yaml
├── foo.json
└── nested
    └── baz.md
```

et le contenu suivant dans chaque dossier:

```
$ cat foo.json
{"meaningOfLife": 42}

$ cat bar.yaml
another_markup_language: 'yes'

$ cat nested/baz.md
I am markdown!
```

puis exécution de ce code:

```js
const path = require('path')
const dataDirectory = require('@github-docs/data-directory')
const data = dataDirectory(path.join(__dirname, 'data'))
```

rendra cet objet:

```js
{
  bar: { another_markup_language: 'yes' },
  foo: { meaningOfLife: 42 },
  nested: { baz: 'I am markdown!' }
}
```
