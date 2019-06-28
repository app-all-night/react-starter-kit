# Setup

[*] - VS Code Debugger

[Here's the source](https://facebook.github.io/create-react-app/docs/setting-up-your-editor#debugging-in-the-editor)

You would need to have the latest version of VS Code and VS Code Chrome Debugger Extension installed.

Then add the block below to your `launch.json` file and put it inside the `.vscode` folder in your app’s root directory.

```
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Chrome",
      "type": "chrome",
      "request": "launch",
      "url": "http://localhost:3000",
      "webRoot": "${workspaceFolder}/src",
      "sourceMapPathOverrides": {
        "webpack:///src/*": "${webRoot}/*"
      }
    }
  ]
}
```

[*] - ESLint

[Here's the source](https://itnext.io/how-eslint-makes-me-a-better-react-developer-237fb14c00ae)

```
npm install --save-dev eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react
```

For `.eslintrc` file

```
{
  "extends": "airbnb",
  "parser": "babel-eslint",
  "env":
    {
      "node": true,
      "es6": true,
      "browser": true
    },
  "rules":
    {
      "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],
      "implicit-arrow-linebreak": "off",
      "comma-dangle": "off",
      "indent": "off",
      "no-trailing-spaces": "off"
    }
  }
```

[*] Prettier

```
{
  "arrowParens": "avoid",
  "bracketSpacing": true,
  "htmlWhitespaceSensitivity": "css",
  "insertPragma": false,
  "jsxBracketSameLine": false,
  "jsxSingleQuote": false,
  "printWidth": 80,
  "proseWrap": "preserve",
  "quoteProps": "as-needed",
  "requirePragma": false,
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "all",
  "useTabs": false
}
```

[*] - Jest/ Enzyme

[Here's the source](https://thetrevorharmon.com/blog/configuring-jest-and-enzyme-in-create-react-app-on-typescript)

```
yarn add @types/jest ts-jest -D
```

`jest.config.js`

```
module.exports = {
  "roots": [
    "<rootDir>/src"
  ],
  "transform": {
    "^.+\\.tsx?$": "ts-jest"
  },
  "testRegex": "(/__tests__/.*|(\\.|/)(test|spec))\\.tsx?$",
  "moduleFileExtensions": [
    "ts",
    "tsx",
    "js",
    "jsx",
    "json",
    "node"
  ],
}
```

For `enzyme`

```
yarn add enzyme @types/enzyme enzyme-to-json enzyme-adapter-react-16 -D
```

Enzyme needs to be configured and instantiated for it to work properly. If it doesn't already exist, create the file `setupTests.js` in your `src` directory and add the following to it:

```
import { configure } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';

configure({ adapter: new Adapter() });
```
