# remark-textr

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][size-badge]][size]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

[**remark**][remark] plugin to [make your typography better][typewriter-habits]
with [**Textr**][textr].

## Note!

This plugin is ready for the new parser in remark
([`remarkjs/remark#536`](https://github.com/remarkjs/remark/pull/536)).
No change is needed: it works exactly the same now as it did before!

## Install

This package is [ESM only](https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c):
Node 12+ is needed to use it and it must be `import`ed instead of `require`d.

[npm][]:

```sh
npm install remark-textr
```

## Use

Say we have the following file, `example.md`:

````markdown
## spread operator...

```js
function(...args) { return args; }
```
````

And our script, `example.js`, looks as follows:

```js
import {readSync} from 'to-vfile'
import {remark} from 'remark'
import remarkTextr from 'remark-textr'

const file = readSync('example.md')

remark()
  .use(remarkTextr, {plugins: [ellipses]})
  .process(file)
  .then((file) => {
    console.log(String(file))
  })

// Textr plugin: just a function to replace triple dots to ellipses.
function ellipses(input) {
  return input.replace(/\.{3}/gim, '…')
}
```

Yields:

````markdown
## spread operator…

```js
function(...args) { return args; }
```
````

## API

This package exports no identifiers.
The default export is `remarkTextr`.

### `unified().use(remarkTextr[, config])`

[Make your typography better][typewriter-habits] with [**Textr**][textr].

##### `config`

###### `config.plugins`

List of [Textr][] plugins (`Array.<string|Function>?`).
If strings are passed in, those are loaded with `require`.
Textr plugins are available on npm, labelled with [textr][textr-plugins]
keyword.
You can also create them yourself, as shown in the example above.

###### `config.options`

[Textr][] options (`Object?`).
For example, you may want to set the [ISO 639][iso] [locale code][locale] of the
content, which is important for stuff like the correct primary and secondary
quotes.

## Security

Use of `remark-textr` does not involve [**rehype**][rehype] ([**hast**][hast])
or user content so there are no openings for [cross-site scripting (XSS)][xss]
attacks.
[Textr][] operates on text nodes, which are always escaped by remark.

## Contribute

See [`contributing.md`][contributing] in [`remarkjs/.github`][health] for ways
to get started.
See [`support.md`][support] for ways to get help.

This project has a [code of conduct][coc].
By interacting with this repository, organization, or community you agree to
abide by its terms.

## License

[MIT][license] © [Denys Dovhan][author]

<!-- Definitions -->

[build-badge]: https://github.com/remarkjs/remark-textr/workflows/main/badge.svg

[build]: https://github.com/remarkjs/remark-textr/actions

[coverage-badge]: https://img.shields.io/codecov/c/github/remarkjs/remark-textr.svg

[coverage]: https://codecov.io/github/remarkjs/remark-textr

[downloads-badge]: https://img.shields.io/npm/dm/remark-textr.svg

[downloads]: https://www.npmjs.com/package/remark-textr

[size-badge]: https://img.shields.io/bundlephobia/minzip/remark-textr.svg

[size]: https://bundlephobia.com/result?p=remark-textr

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[chat-badge]: https://img.shields.io/badge/chat-discussions-success.svg

[chat]: https://github.com/remarkjs/remark/discussions

[npm]: https://docs.npmjs.com/cli/install

[health]: https://github.com/remarkjs/.github

[contributing]: https://github.com/remarkjs/.github/blob/HEAD/contributing.md

[support]: https://github.com/remarkjs/.github/blob/HEAD/support.md

[coc]: https://github.com/remarkjs/.github/blob/HEAD/code-of-conduct.md

[license]: license

[author]: https://denysdovhan.com

[remark]: https://github.com/remarkjs/remark

[textr]: https://github.com/A/textr

[textr-plugins]: https://www.npmjs.com/browse/keyword/textr

[locale]: https://github.com/A/textr#locale-option-consistence

[iso]: https://www.wikiwand.com/en/List_of_ISO_639-1_codes

[typewriter-habits]: https://practicaltypography.com/typewriter-habits.html

[xss]: https://en.wikipedia.org/wiki/Cross-site_scripting

[rehype]: https://github.com/rehypejs/rehype

[hast]: https://github.com/syntax-tree/hast
