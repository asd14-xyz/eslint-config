<!-- markdownlint-disable first-line-h1 line-length -->

[![CircleCI](https://circleci.com/gh/mutantlove/eslint-config.svg?style=svg)](https://circleci.com/gh/mutantlove/eslint-config)
[![npm package version](https://badge.fury.io/js/%40mutantlove%2Feslint-config.svg)](https://badge.fury.io/js/%40mutantlove%2Feslint-config)
[![peer-badge](https://david-dm.org/mutantlove/eslint-config/peer-status.svg)](https://david-dm.org/mutantlove/eslint-config?type=peer)

# JavaScript ESLint rules

> JavaScript ESLint bundle with best practices and common use rules for writing more consistent code
>
> [`"semi": [ "error", "never" ]`](http://eslint.org/docs/rules/semi) :godmode: ... [the horror](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding) :goberserk:

Other bundles: [XO](https://www.npmjs.com/package/xo), [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb), [eslint-config-google](https://github.com/google/eslint-config-google), [more](https://www.npmjs.com/search?q=+eslint-config-)

---

<!-- vim-markdown-toc GFM -->

* [Install](#install)
* [Use](#use)
* [Inside](#inside)
* [Example config](#example-config)
* [Commit messages](#commit-messages)
* [Changelog](#changelog)

<!-- vim-markdown-toc -->

## Install

```bash
npm install eslint @mutantlove/eslint-config --save-dev
```

Run `npm info "@mutantlove/eslint-config@latest" peerDependencies` to get the packages needed in your own `package.json`.

It should be something like this:

```javascript
...
"devDependencies": {
    "eslint": "^6.8.0",
    "eslint-config-prettier": "^6.10.0",
    "eslint-plugin-import": "^2.20.1",
    "eslint-plugin-json": "^2.0.1",
    "eslint-plugin-no-inferred-method-name": "^2.0.0",
    "eslint-plugin-promise": "^4.2.1",
    "eslint-plugin-prettier": "^3.1.2",
    "eslint-plugin-unicorn": "^16.0.0",
    "prettier": "^1.19.1"
}
...
```

## Use

Add the `react` or `node` target file in your `.eslintrc` file:

```javascript
{
    "extends": [
        // for Node.js projects
        "@mutantlove/eslint-config/targets/node",

        // for React projects
        "@mutantlove/eslint-config/targets/react",
    ]
}
```

## Inside

* [eslint-plugin-import](https://www.npmjs.org/package/eslint-plugin-import) - Support for ES2015+ (ES6+) import/export syntax
* [eslint-plugin-promise](https://www.npmjs.org/package/eslint-plugin-promise) - Enforce best practices for JavaScript promises
* [eslint-plugin-unicorn](https://www.npmjs.org/package/eslint-plugin-unicorn) - Various awesome ESLint rules
* [eslint-plugin-html](https://www.npmjs.org/package/eslint-plugin-html) - Allows linting and fixing inline scripts contained in HTML files
* [eslint-plugin-react](https://www.npmjs.org/package/eslint-plugin-react) - React specific linting rules
* [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks) - Linting rules rules of React Hooks.
* [eslint-plugin-no-inferred-method-name](https://www.npmjs.org/package/eslint-plugin-no-inferred-method-name) - In ES6, compact methods and unnamed function expression assignments within object literals do not create a lexical identification (name) binding that corresponds to the function name identifier for recursion or event binding. The compact method syntax will not be an appropriate option for these types of solutions, and a named function expression should be used instead. This custom ESLint rule will identify instances where a function name is being called and a lexical identifier is unavailable within a compact object literal.

## Example config

Using [`babel-eslint`](https://github.com/babel/babel-eslint) and [`eslint-import-resolver-webpack`](https://www.npmjs.com/package/eslint-import-resolver-webpack)

`.eslintrc`

```js
{
    "root"  : true,
    "parser": "babel-eslint",

    "extends": [ "@mutantlove/eslint-config/targets/react" ],

    "settings": {
        // Use webpack to resolve modules in imports
        "import/resolver": {
            "webpack": {
                "config": "./webpack.config.js",
            },
        },

        // Recommended if you use eslint_d
        "import/cache": {
            "lifetime": 5,
        },

        // List of regex strings that, if matched by a path, will not report
        // the matching module if no exports are found.
        "import/ignore": [ "\\.(sass|scss|less|css)$" ],
    },

    // Custom rules
    "rules": {
    },
}
```

`.prettierrc`

```js
{
  "semi": false,
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "singleQuote": false,
  "trailingComma": "es5",
  "bracketSpacing": true,
  "jsxBracketSameLine": true,
  "arrowParens": "avoid"
}
```

Optional `.editorconfig`

```bash
root = true

[*]
charset = utf-8
indent_style = space
indent_size = 2
end_of_line = lf
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false
```

## Commit messages

Using Angular's [conventions](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines).

```text
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

* **feat**: A new feature
* **fix**: A bug fix
* **docs**: Documentation only changes
* **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **perf**: A code change that improves performance
* **test**: Adding missing or correcting existing tests
* **chore**: Changes to the build process or auxiliary tools and libraries such as documentation generation

## Changelog

See the [releases section](https://github.com/mutantlove/eslint-config/releases) for details.
