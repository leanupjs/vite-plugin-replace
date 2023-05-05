# Vite Plugin Replace

With this plugin text in sourcecode could be replaced before bundling.

## Motivation

The initial reason for implementing a new plugin to replace it was that the approach of [@rollup/plugin-replace](https://github.com/rollup/plugins/tree/master/packages/replace) is not flexible enough. So we looked at what [JavaScript replace](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/String/replace) actually offers us.

### Declaration of the Replacement (interface):

```ts
interface Replacement {
  from: RegExp | string;
  to: string | Function
}
```

| Attribute | Type | Description |
| -- | -- | -- |
| `from` | `regexp` \| `string` | 
| `to` | `string` \| `string` |

### Additional config
| Attribute | Type | Description |
| -- | -- | -- |
| `enforce` | `pre` \| `post` | 

## Installation

```bash
npm i -D vite-plugin-replace
```

## Usage

```js
import packageJson from "./package.json";
import { replaceCodePlugin } from "vite-plugin-replace";

module.exports = mergeConfig(config, {
  plugins: [
    replaceCodePlugin({
      replacements: [
        {
          from: "__CLI_NAME__",
          to: packageJson.name,
        },
        {
          from: /__CLI_VERSION__/g,
          to: packageJson.version,
        },
      ],
    }),
  ],
});
```
