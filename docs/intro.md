---
sidebar_position: 1
slug: /
---

# Blumea Intro

Let's discover **Blumea in less than 5 minutes**.

Blumea is an easy to plug Bloom filter solution for your applications.

## 🔖 About

A Bloom filter is a space-efficient probabilistic data structure for determining whether or not an element belongs to a set. Checking the availability of a username, for example, is a set membership problem, with the set being a list of all registered usernames. The cost of efficiency is that it is probabilistic in nature, which implies that some False Positive findings may occur. False positive means that it may indicate that a certain username is already taken when it is not.

## 🔍 Getting Started

Get started by **Installation**.

### Installation

```bash
npm i blumea

```

**Or**

```bash
npm install blumea --save
```

## 💻 How to Use?

- Require the **Blumea** module into your javascript/typescript application.

```js
const blumea = require("blumea");
```

- **blumea** can now be used to access various bloom filter options.

```js
const basicFilter = blumea.bloomFilterBasic;
let filter = new basicFilter(itemCount, falsePostiveProbability);
```

### Methods

- ** insert(element: any) ** : To add the element to the bloom filter instance.
- ** find(element: any) ** : To check for element membership with the false positive rate of the filter.

## ❓What you'll need

- Node.js: v7.0.0 or higher
- Google Chrome: v41 or higher
- Mozilla Firefox: v34 or higher
- Microsoft Edge: v12 or higher
