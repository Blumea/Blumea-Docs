---
sidebar_position: 1
slug: /
---

# Blumea Intro

Let's discover **Blumea in less than 5 minutes**.

Blumea is a simple and efficient Bloom filter implementation for your applications. It's designed to help you determine whether an element belongs to a set in a space-efficient way.

## 🔖 About Bloom Filters

A Bloom filter is a probabilistic data structure that allows you to test if an element is in a set. It does so by using a bit array and multiple hash functions to check if a given element is likely to be in the set or not. This makes Bloom filters ideal for use cases where space is at a premium, or when you need to test for set membership quickly.

One common example of where Bloom filters are useful is in checking the availability of usernames. Here, the set is the list of all registered usernames, and Bloom filters can be used to determine if a new username is already taken. The downside of Bloom filters is that they are probabilistic in nature and can sometimes give false positives (indicating that an element is in the set when it isn't).

## 📝 Installation

- You can install Blumea via npm by running:

```bash
npm i blumea
```

- Alternatively, you can save the latest dependency by running:

```bash
 npm i blumea@latest --save
```

## 💻 Usage

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

## ❓What you'll need

- Node.js: v7.0.0 or higher
- Google Chrome: v41 or higher
- Mozilla Firefox: v34 or higher
- Microsoft Edge: v12 or higher
