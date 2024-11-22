# Plugin Solhint Rules

A set of Solhint rules for Plugin's Solidity Style Guide.

[You can find a working Foundry example here](https://github.com/goplugin/plugin-solhint-rules-example).

## Install to a new project

```
npm init && npm install solhint solhint-plugin-plugin-solidity@npm:@pluginv3.0/solhint-plugin-plugin-solidity --save
```

Create a `.solhint.json` in your root project directory:

```
{
  "extends": "solhint:recommended",
  "plugins": ["plugin-solidity"],
  "rules": {
    "compiler-version": ["off", "^0.8.0"],
    "const-name-snakecase": "off",
    "constructor-syntax": "error",
    "var-name-mixedcase": "off",
    "func-visibility": [
      "error",
      {
        "ignoreConstructors": true
      }
    ],
    "max-line-length": ["error", 160],
    "not-rely-on-time": "off",
    "no-empty-blocks": "off",
    "quotes": ["error", "single"],
    "reason-string": [
      "warn",
      {
        "maxLength": 64
      }
    ],
    "plugin-solidity/prefix-internal-functions-with-underscore": "warn",
    "plugin-solidity/prefix-private-functions-with-underscore": "warn",
    "plugin-solidity/prefix-storage-variables-with-s-underscore": "warn",
    "plugin-solidity/prefix-immutable-variables-with-i": "warn",
    "plugin-solidity/prefix-interfaces-with-i": "warn",
    "plugin-solidity/all-caps-constant-storage-variables": "warn",
    "plugin-solidity/no-hardhat-imports": "warn",
    "plugin-solidity/inherited-constructor-args-not-in-contract-definition": "warn",
    "plugin-solidity/no-block-single-if-reverts": "warn",
    "plugin-solidity/explicit-returns": "warn"
  }
}
```

Add the following to your `package.json`:

```
  "scripts": {
    "solhint": "solhint --config .solhint.json \"src/*.sol\""
  },
```

Then, run:

```
npm solhint

src/Counter.sol
  4:1  warning  Internal function increment is not prefixed with underscore (_)  plugin-solidity/prefix-internal-functions-with-underscore
  4:1  warning  Private / internal variable number is not prefixed with s_       plugin-solidity/prefix-storage-variables-with-s-underscore
  8:9  warning  Provide an error message for require                             reason-string
```

## Rules

| Rule Id                                                 | Description                                                                           |
|---------------------------------------------------------|---------------------------------------------------------------------------------------|
| `prefix-internal-functions-with-underscore`             | Naming convention                                                                     |
| `prefix-private-functions-with-underscore`              | Naming convention                                                                     |
| `prefix-storage-variables-with-s-underscore`            | Naming convention                                                                     |
| `prefix-immutable-variables-with-i`                     | Naming convention                                                                     |
| `prefix-interfaces-with-i`                              | Naming convention                                                                     |
| `all-caps-constant-storage-variables`                   | Naming convention                                                                     |
| `no-hardhat-imports`                                    | Leftover `hardhat/*.sol` imports not allowed                                          |
| `inherited-constructor-args-not-in-contract-definition` | Inherited contract constructor arguments should be specified in the constructor block |
| `no-block-single-if-reverts`                            | Omit curly braces for single-line guard clauses                                       |
| `explicit-returns`                                      | Always specify an expression after a `return`                                         |
