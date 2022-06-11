# vfile-reporter-json

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

[vfile][] utility to create a report in machine readable JSON.

## Contents

*   [What is this?](#what-is-this)
*   [When should I use this?](#when-should-i-use-this)
*   [Install](#install)
*   [Use](#use)
*   [API](#api)
    *   [`reporter(files[, options])`](#reporterfiles-options)
*   [Types](#types)
*   [Compatibility](#compatibility)
*   [Contribute](#contribute)
*   [License](#license)

## What is this?

This package is like [`vfile-reporter`][vfile-reporter] but it outputs machine
readable JSON.

## When should I use this?

You can use this when you need to serialize lint results for machines, use
`vfile-reporter` itself for humans.

## Install

This package is [ESM only][esm].
In Node.js (version 12.20+, 14.14+, or 16.0+), install with [npm][]:

```sh
npm install vfile-reporter-json
```

In Deno with [`esm.sh`][esmsh]:

```js
import {reporterJson} from 'https://esm.sh/vfile-reporter-json@3'
```

In browsers with [`esm.sh`][esmsh]:

```html
<script type="module">
  import {reporterJson} from 'https://esm.sh/vfile-reporter-json@3?bundle'
</script>
```

## Use

```js
import {VFile} from 'vfile'
import {reporterJson} from 'vfile-reporter-json'

const one = new VFile({path: 'test/fixture/1.js'})
const two = new VFile({path: 'test/fixture/2.js'})

one.message('Warning!', {line: 2, column: 4})

console.log(reporterJson([one, two]))
```

Yields:

```json
[{"path":"test/fixture/1.js","cwd":"/Users/tilde/projects/oss/vfile-reporter-json","history":["test/fixture/1.js"],"messages":[{"reason":"Warning!","line":2,"column":4,"position":{"start":{"line":2,"column":4},"end":{"line":null,"column":null}},"ruleId":null,"source":null,"fatal":false,"stack":null}]},{"path":"test/fixture/2.js","cwd":"/Users/tilde/projects/oss/vfile-reporter-json","history":["test/fixture/2.js"],"messages":[]}]
```

## API

This package exports the identifier `reporterJson`.
That identifier is also the default export.

### `reporter(files[, options])`

Generate **stringified** JSON for `files` ([`VFile`][vfile] or `Array.<VFile>`).

###### `options.quiet`

Do not output anything for a file which has no warnings or errors (`boolean`,
default: `false`).
The default behavior is to show a success message.

###### `options.silent`

Do not output messages without `fatal` set to true (`boolean`, default:
`false`).
Also sets `quiet` to `true`.

###### `options.pretty`

Given as `space` to [`JSON.stringify()`][json-stringify] (`boolean`, `number`,
or `string`, default: `0`).
When `true`, defaults to `2`.

## Types

This package is fully typed with [TypeScript][].
It exports the additional type `Options`.

## Compatibility

Projects maintained by the unified collective are compatible with all maintained
versions of Node.js.
As of now, that is Node.js 12.20+, 14.14+, 16.0+, and 18.0+.
Our projects sometimes work with older versions, but this is not guaranteed.

## Contribute

See [`contributing.md`][contributing] in [`vfile/.github`][health] for ways to
get started.
See [`support.md`][support] for ways to get help.

This project has a [code of conduct][coc].
By interacting with this repository, organization, or community you agree to
abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]

<!-- Definitions -->

[build-badge]: https://github.com/vfile/vfile-reporter-json/workflows/main/badge.svg

[build]: https://github.com/vfile/vfile-reporter-json/actions

[coverage-badge]: https://img.shields.io/codecov/c/github/vfile/vfile-reporter-json.svg

[coverage]: https://codecov.io/github/vfile/vfile-reporter-json

[downloads-badge]: https://img.shields.io/npm/dm/vfile-reporter-json.svg

[downloads]: https://www.npmjs.com/package/vfile-reporter-json

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[chat-badge]: https://img.shields.io/badge/chat-discussions-success.svg

[chat]: https://github.com/vfile/vfile/discussions

[npm]: https://docs.npmjs.com/cli/install

[esm]: https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c

[esmsh]: https://esm.sh

[typescript]: https://www.typescriptlang.org

[contributing]: https://github.com/vfile/.github/blob/main/contributing.md

[support]: https://github.com/vfile/.github/blob/main/support.md

[health]: https://github.com/vfile/.github

[coc]: https://github.com/vfile/.github/blob/main/code-of-conduct.md

[license]: license

[author]: https://wooorm.com

[vfile]: https://github.com/vfile/vfile

[vfile-reporter]: https://github.com/vfile/vfile-reporter

[json-stringify]: https://developer.mozilla.org/JavaScript/Reference/Global_Objects/JSON/stringify
