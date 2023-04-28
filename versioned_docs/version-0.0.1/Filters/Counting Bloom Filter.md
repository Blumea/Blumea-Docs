Counting Bloom Filters are a variant of Bloom Filters that allow adding and removing items efficiently. Rather than simply setting bits to indicate the presence of an item, Counting Bloom Filters keep a count of the number of times an item has been added. This allows the removal of items by decrementing their count, and also reduces the chance of false positives. Counting Bloom Filters are useful when items need to be added and removed from the filter, but at the cost of increased memory usage. Prime use cases include Network traffic management, Web caching and Transactional Fraud detection.

### 🛳 How to import?

To import the BloomFilter class from the Blumea package into your project, use the following:

```js
const { CountingBloomFilter } = require("blumea");

/**
 * Create a Bloom filter instance for your app.
 * Provide item count and an acceptable false positive rate.
 */

let filter = new CountingBloomFilter(5999, 0.03);
```

### 💡 Methods

- ** insert(element) ** : To add the element to the bloom filter instance.

:::note

When an element is added to the Counting Bloom Filter with a single bit count, the filter increments the count of that element every time it is added. This count is maintained in the `count_bit ` array for each element in the filter.
:::

- ** find(element) ** : To check for element membership with the false positive rate of the filter.
- ** getCount(element) ** : To check for element membership and extract it's count. It returns the count if the element is found, `0` otherwise.
- ** Utility Methods ** :

  - getHashFunctionCount() or filter.hash_count
  - getBitArraySize() or filter.size

- Sample Code snippet for Counting Bloom Filter:

```js
const { CountingBloomFilter } = require("blumea");
const express = require("express");
const app = express();

let filter = new CountingBloomFilter(1000, 0.01);

app.post("/login", async (req, res) => {
  try {
    const { username, password } = req.body;
    // Save NT bandwidth on db queries to validate username.
    if (!filter.find(username)) {
      // handle invalid username case
    }

    //Some Logic to verify credentials.
    await processLogin({ username, password });

    // save count with bloom filter.
    filter(username, filter.getCount(username) + 1);

    // Or simply use the insert method.
    filter.insert(username);
  } catch (error) {
    // handle error
  }
});
// ...code
```
