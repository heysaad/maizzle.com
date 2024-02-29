---
title: "Expressions configuration"
description: "Configuring expressions in Maizzle."
---

# Expressions configuration

Expressions may be configured in your project's `config.js`:

```js [config.js]
module.exports = {
  build: {
    posthtml: {
      expressions: {
        // posthtml-expressions options
      }
    }
  }
}
```

## delimiters

Type: `Array`\
Default: `['{{', '}}']`

Array containing beginning and ending delimiters for expressions.

## unescapeDelimiters

Type: `Array`\
Default: `['{{{', '}}}']`

Array containing beginning and ending delimiters for unescaped locals.

## locals

Type: `Object`\
Default: `{}`

Data defined here will be available under the `page` object.

For example, if you set this to `{foo: 'bar'}`, you can access it in your templates through `{{ page.foo }}`.

## localsAttr

Type: `String`\
Default: `locals`

Attribute name for `<script>` tags that contain locals.

## removeScriptLocals

Type: `Boolean`\
Default: `false`

Remove `<script>` tags that contain locals.

## conditionalTags

Type: `Array`\
Default: `['if', 'elseif', 'else']`

Array containing tag names to be used for if/else statements.

## switchTags

Type: `Array`\
Default: `['switch', 'case', 'default']`

Array containing tag names to be used for switch statements.

## loopTags

Type: `Array`\
Default: `['each', 'for']`

Array containing tag names to be used for loops.

## scopeTags

Type: `Array`\
Default: `['scope']`

Array containing tag names to be used for scopes.

## ignoredTag

Type: `String`\
Default: `raw`

Name of tag inside of which expression parsing is disabled.

## strictMode

Type: `Boolean`\
Default: `false`

Maizzle disables `strictMode` so that, if you have an error inside an expression, it will be rendered as `undefined` and the email will still be compiled, instead of the build failing.

## missingLocal

Type: `undefined|String`\
Default: `undefined`

Define what to render when referencing a value that is not defined in `locals`.

| `missingLocal` |  `strictMode`  | Output                              |
|:--------------:|:--------------:|:------------------------------------|
|  `undefined`   |     `true`     | Error is thrown                     |
|  `undefined`   |    `false`     | 'undefined'                         |
|      `''`      | `false`/`true` | `''` (no output, empty string)      |
|   `{local}`    | `false`/`true` | Original reference like `{{ foo }}` |

By default, Maizzle will output the string `undefined` when a value is not defined in `locals`.
