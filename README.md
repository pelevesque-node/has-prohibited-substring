[![Build Status](https://travis-ci.org/pelevesque/has-prohibited-substring.svg?branch=master)](https://travis-ci.org/pelevesque/has-prohibited-substring)
[![Coverage Status](https://coveralls.io/repos/github/pelevesque/has-prohibited-substring/badge.svg?branch=master)](https://coveralls.io/github/pelevesque/has-prohibited-substring?branch=master)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# has-prohibited-substring

Checks if a string has a prohibited substring.

## Related Packages

https://github.com/pelevesque/has-prohibited-substring-at-indexes  
https://github.com/pelevesque/has-prohibited-substring-after-sums   
https://github.com/pelevesque/has-required-substrings    
https://github.com/pelevesque/has-required-substrings-at-indexes    
https://github.com/pelevesque/has-required-substrings-after-sums    

## Node Repository

https://www.npmjs.com/package/@pelevesque/has-prohibited-substring

## Installation

`npm install @pelevesque/has-prohibited-substring`

## Tests

Command                      | Description
---------------------------- | ------------
`npm test` or `npm run test` | All Tests Below
`npm run cover`              | Standard Style
`npm run standard`           | Coverage
`npm run unit`               | Unit Tests

## Usage

### Parameters

```js
str                       (required)
prohibitedSubstrings      (required)
allowLastSubstringToBleed (optional) default = false
```

### Requiring

```js
const hasProhibitedSubstring = require('@pelevesque/has-prohibited-substring')
```

### Basic Usage

`prohibitedSubstrings` is an array of substrings. `true` is returned if at least
one substring is found.

```js
const str = 'abcde'
const prohibitedSubstrings = ['f']
const result = hasProhibitedSubstring(str, prohibitedSubstrings)
// result === false
```

```js
const str = 'abcde'
const prohibitedSubstrings = ['a']
const result = hasProhibitedSubstring(str, prohibitedSubstrings)
// result === true
```

```js
const str = 'abcde'
const prohibitedSubstrings = ['a', 'b', 'f']
const result = hasProhibitedSubstring(str, prohibitedSubstrings)
// result === true
```

```js
const str = 'abcde'
const prohibitedSubstrings = ['a', 'b', 'c']
const result = hasProhibitedSubstring(str, prohibitedSubstrings)
// result === true
```

```js
const str = 'a man a plan a canal'
const prohibitedSubstrings = ['man', 'fly', 'bee']
const result = hasProhibitedSubstring(str, prohibitedSubstrings)
// result === true
```

### Options

#### allowLastSubstringToBleed

The `allowLastSubstringToBleed` option is `false` by default. It it used when you want
to allow the last substring to be incomplete if the string is too short.
In the following example, the last substring `canal` starts at the correct index,
but remains incomplete since the string ends. Normally this would return `false`.
With `allowLastSubstringToBleed` set to `true`, it returns `true`.

```js
const str = 'a man a plan a c'
const prohibitedSubstrings = ['canal']
const allowLastSubstringToBleed = true
const result = hasProhibitedSubstring(str, prohibitedSubstrings, allowLastSubstringToBleed)
// result === true
```

##### options style

For style compatibility with related packages like `has-required-substrings-after-sums`,
it is possible to set `allowLastSubstringToBleed` using an options style.

```js
const str = 'a man a plan a c'
const prohibitedSubstrings = ['canal']
const allowLastSubstringToBleed = true
const result = hasProhibitedSubstring(str, prohibitedSubstrings, {
  allowLastSubstringToBleed: allowLastSubstringToBleed
})
// result === true
```
