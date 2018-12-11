# Promise File Reader

## ustage
```js
import PromiseFileReader, {
  FileReader,
  File,
  fileReader,
} from 'promise-file-reader'
```

## Objects

default export object is `PromiseFileReader`

#### PromiseFileReader
a `class` with methods `readAsArrayBuffer`, `readAsText`, `readAsDataURL`,
`readAsBinaryString` just as `window.FileReader` does, but returns `Promise`, resolve
with `FileReader.result` or reject with `FileReader.error`.

also explored as `window.PromiseFileReader`

```js
// import
import PromiseFileReader from 'promise-file-reader'
```

```js
// example
;(async file => {
  var pfr = new PromiseFileReader()
  console.log(await pfr.readAsText())
})(new File(['hello from pfr.txt'], 'pfr.txt'))
```

#### PromiseFileReader.FileReader
a reference of PromiseFileReader

```js
// import
import {FileReader as PromiseFileReader} from 'promise-file-reader'
```

#### PromiseFileReader.File
a `class` takes a `Blob` Object in constructor.
this also has 4 method as `window.FileReader`, but without `readAs` prefix

also explored as `window.PromiseFile`

```js
// import
import {File as PromiseFile} from 'promise-file-reader'
```

```js
// example
;(async file => {
  console.log(await new PromiseFile(file).arrayBuffer())
  console.log(await new PromiseFile(file).text())
  console.log(await new PromiseFile(file).dataURL())
  console.log(await new PromiseFile(file).binaryString())
})(new File(['hello from pfr.txt'], 'pfr.txt'))
```

#### PromiseFileReader.fileReader
a instance of `PromiseFileReader`.
unlike `window.FileReader`, `PromiseFileReader` don't need to listen `onload` or `onerror` event,
so the reader can be used easyly

also explored as `window.promiseFileReader`
```js
// import
import {fileReader as promiseFileReader} from 'promise-file-reader'
```

```js
// example
;(async file => {
  console.log(await promiseFileReader.readAsArrayBuffer())
  console.log(await promiseFileReader.readAsText())
  console.log(await promiseFileReader.readAsDataURL())
  console.log(await promiseFileReader.readAsBinaryString())
})(new File(['hello from pfr.txt'], 'pfr.txt'))
```

notice:
if you call more then one read method, at the same time.
don't use `promiseFileReader.result` and `promiseFileReader.error`
