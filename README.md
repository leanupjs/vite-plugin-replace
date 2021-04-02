# Vite Plugin Replace

With this plugin text in sourcecode could be replaced before bundling.

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
