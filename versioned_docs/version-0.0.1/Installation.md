---
sidebar_position: 2
---


- You can install Blumea via npm by running:

```bash
npm i blumea
```

- Alternatively, you can save the latest dependency by running:

```bash
 npm i blumea@latest --save
```

To start using Blumea in your JavaScript or TypeScript project, you need to first import it. This can be done using either of the following methods:

- ES5 import could be done as follows:

```js
const blumea = require("blumea");

// import one or more bloom filters
const { BloomFilter } = require("blumea");
```

- Alternatively, for ES6 or later versions:

```js
import * as blumea from "blumea";

//// import one or more bloom filters
import { BloomFilter } from "blumea";
```

- After importing Blumea into your project, you can create and access different bloom filter options.
- Blumea includes a logger module to monitor basic logs while using the filter.
- To enable the logger, use one of the following flags while running your JavaScript/TypeScript or Node.js application: `-l`, `-log`, or `-blumea`.

  - Here are examples of how to enable the logger:

    ```bash
    node application.js -blumea
    ```

  - Alternatively, applications with start scripts could use:

    ```bash
     npm run <app-script> -log
    ```

## ❓ What you'll need

- Node.js: v7.0.0 or higher
- Google Chrome: v41 or higher
- Mozilla Firefox: v34 or higher
- Microsoft Edge: v12 or higher
