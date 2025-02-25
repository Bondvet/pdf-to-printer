# Node.js PDF printing

[![Build Status](https://api.cirrus-ci.com/github/artiebits/pdf-to-printer.svg)](https://cirrus-ci.com/github/artiebits/pdf-to-printer) [![codecov](https://codecov.io/gh/artiebits/pdf-to-printer/branch/master/graph/badge.svg)](https://codecov.io/gh/artiebits/pdf-to-printer)

A utility to print PDF files from Node.js and Electron.

* ✅ Works on Windows and Unix-like operating systems.
* ✅ Supports label printers such as [Rollo](https://www.rolloprinter.com/) and [Zebra](https://www.zebra.com/us/en/products/printers.html).

## Getting Started

Install using [`yarn`](https://yarnpkg.com/):

```bash
yarn add pdf-to-printer
```

Or [`npm`](https://www.npmjs.com/):

```bash
npm install --save pdf-to-printer
```

## Basic Usage

Print a PDF file to the default printer:

```javascript
import printer from "pdf-to-printer";

printer
  .print("assets/pdf-sample.pdf")
  .then(console.log)
  .catch(console.error);
```

## API

### `.print(pdf[, options]) => Promise<void>`

#### Arguments

1. `pdf` (`string`): PDF file to print. Will throw an error if no PDF specified.
2. `options` (`Object` [optional]):
   - `options.printer`: (`string` [optional]): Print to the specified printer. Will print to the default printer if name not specified. If the printer name mistyped or specified printer does not exist, nothing will print.

##### UNIX only:

On UNIX systems you can add more options to the `options` object. Some examples are:

```javascript
const options = {
  printer: "Zebra",
  "fit-to-page": true,
  landscape: true,
  media: "A4"
);
  
printer
  .print("assets/pdf-sample.pdf", options)
  .then(console.log)
  .catch(console.error);
```

Please checkout [Command-line Printing and Options](https://www.cups.org/doc/options.html) or `man lp` to get all available options.

#### Returns

`Promise<void>`.

#### Examples

To print a PDF file to the default printer:

```javascript
printer
  .print("assets/pdf-sample.pdf")
  .then(console.log)
  .catch(console.error);
```

To print to a specific printer, add the name of the printer to options:

```javascript
const options = {
  printer: "Zebra"
};

printer
  .print("assets/pdf-sample.pdf", options)
  .then(console.log)
  .catch(console.error);
```

### `.list() => Promise<string[]>`

#### Returns

`Promise<string[]>`: List of available printers.

#### Examples

```javascript
printer
  .list()
  .then(console.log)
  .catch(console.error);
```

## Examples

We have a few examples in the [source code](/examples).

## Contact

Please do not hesitate to report a bug or suggest an idea. You can do it [here](https://github.com/artiebits/pdf-to-printer/issues/new/choose), or email me at artur.khusaenov at gmail dot com.

## License

[MIT](LICENSE)
