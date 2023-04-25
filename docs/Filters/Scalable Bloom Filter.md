A Scalable Bloom Filter is a type of Bloom Filter that is designed to be scalable, meaning it can handle an arbitrary number of items and can dynamically adjust its size based on the number of items being inserted. It is a probabilistic data structure that works by using multiple hash functions to generate a set of bit positions in a bit array, where a 1 indicates that the item is likely present and a 0 indicates that the item is definitely not present. Scalable Bloom Filters are useful in a variety of real-life applications, such as:

- Web Cache Optimization: improving web caching system performance by quickly determining whether a requested web page is present in the cache.
- Distributed Systems: reducing network traffic in distributed systems by determining which nodes contain a particular item without having to query each node individually.
- Database Indexing: speeding up database queries by providing a quick filter to determine if a record is not present in a table, and as an index in a database to help with range queries.

### 🛳 How to import?

To import the BloomFilter class from the Blumea package into your project, use the following:

```js
const { ScalableBloomFilter } = require("blumea");

/**
 * Create a Bloom filter instance for your app.
 * Default values (itemCount: 1000, falsePostiveRate: 0.01) is used.
 */

let filter = new ScalableBloomFilter();
```

### 💡 Methods

- ** insert(element) ** : To add the element to the bloom filter instance.

:::note
Insertion checks for the available size and would automatically scale the filter by a factor of 2, as and when needed.
:::

- ** find(element) ** : To check for element membership with the false positive rate of the filter.
- ** About Custom Parameters ** :
  - ScalableBloomFilter's constructor can accept an array of custom hash functions as the third parameter.
  - :::note
    new ScalableBloomFilter(
    expectedItems?: number,
    falsePositiveRate?: number,
    hashFunctions?: hashFunction []
    ): ScalableBloomFilter
    :::
  - Function Prototype for acceptable hash function :
    ```js
    hashingFunction: (str: string, seed?: number | undefined) => number;
    ```

### ❗️Usage Warning

- Please note that the false positive rate in a Bloom filter should not exceed 0.999. If this value is exceeded, an exception will be thrown.

- The valid range for false positive rates is between 0.001 and 0.999.

- Sample TODO app with Scalable Bloom Filter:

```js

  const { ScalableBloomFilter } = require('blumea'),

  class TODO {

    constructor () {
      /*
       * Initialize scalable bloom filter.
       * Default config is for 1000 items at 0.01 fp rate.
       * Filter auto-scales by a factor of 2 when needed.
       */
     this.filter = new ScalableBloomFilter();
    }

    /*
      TODO: {
        _id: uuid(),
        title: string,
        deadline: Date,
        desc: string
        }
    */
    addTodo (todo) {

      if (filter.find(todo._id)) {
        // handle case.
      } else {

        /*
         * Write todo to DB & update filter.
         * code to insert to DB goes here.
         */
        filter.insert(todo._id); //auto-scales during insert.
      }
    }
    // add custom implementations
  }

```
