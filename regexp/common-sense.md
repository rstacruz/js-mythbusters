# Use RegExp in cases with sense

When use with care, `RegexEp` are fast.

However, They're usually overkill when you are merely searching for literal strings:

```js
var endsWithSemiColon = /;$/.test(str)
```

Each time a semicolon is found, the `RegExp` advances to the next token (`$`), which checks wheter the match is at the end of the string. If not, the `RegExp` continues searching for a match until it finally makes its way throough the entire string.

In this case, a better approach is to skip all the intermediate steps required by a `RegExp` and simply check whether the last character is a semicolon:

```js
var endsWithSemiColon = str.charAt(str.length - 1) === ';'
```

This is just a bit faster than the regex-based test with small target strings, but, more importantly, the string's length no longer affects the time needed to perfom the test.
