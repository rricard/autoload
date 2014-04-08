autoload
=========
[![Build Status](https://travis-ci.org/Neamar/autoload.png?branch=master)](https://travis-ci.org/Papiel/anyfetch-provider.js)
[![Dependency Status](https://gemnasium.com/Neamar/autoload.png)](https://gemnasium.com/Papiel/anyfetch-provider.js)
[![Coverage Status](https://coveralls.io/repos/Neamar/autoload/badge.png?branch=master)](https://coveralls.io/r/Papiel/anyfetch-provider?branch=master)
[![NPM version](https://badge.fury.io/js/Neamar/autoload.png)](http://badge.fury.io/js/anyfetch-provider)

`require()` all files in subfolder.

This will pre-load all files with require, and build an object.

For instance, given this tree:

```
├── 1.js
├── 2.js
├── 3
│   ├── 31.js
│   └── 32
│       └── 321.js
└── with-dash.js
```

Calling `autoload(__dirname)` will give:

```js
{
  '1': exportsFromFile,
  '2': exportsFromFile,
  'withDash': exportsFromFile,
  '3': {
    '31': exportsFromFile,
    '32': {
      '321': exportsFromFile
    }
  }
}
```

Where `exportsFromFile` is the value returned by the file `module.exports`.
