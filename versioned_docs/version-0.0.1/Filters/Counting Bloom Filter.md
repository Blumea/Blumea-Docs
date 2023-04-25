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

When an element is added to the Counting Bloom Filter with a single bit count, the filter increments the count of that element every time it is added. This count is maintained in the count_bit array for each element in the filter.
:::

- ** find(element) ** : To check for element membership with the false positive rate of the filter.
- ** updateFalsePositiveRate(newFalsePostive) ** : To update the filter instance with a new false positive rate.
- ** updateItemCount(newItemCount) ** : To update the filter instance with a new item count.
- ** Utility Methods ** :
  - getHashFunctionCount() or filter.hash_count
  - getBitArraySize() or filter.size

### ❗️Usage Warning

- Please note that the false positive rate in a Bloom filter should not exceed 0.999. If this value is exceeded, an exception will be thrown.

- The valid range for false positive rates is between 0.001 and 0.999.

- Sample Node app with Counting Bloom Filter:

```js
  const express = require('express')
  const { CountingBloomFilter } = require('blumea'),
  const app = express();

  // Initialize counting bloom filter
  const filter = new CountingBloomFilter(5999, 0.03);

  // Route to check for username availability
  app.post('/check-username', (req,res)=>{
      try {
          const username = req.body.username;
          if(!username) {
            // Handle invalid input case
          } else {
            /**
             * Check if username is available using filter.
             * Saves network bandwidth on db queries.
             * */

            if(filter.find(username))
              res.send(`${username} already in use.`)
            else
              res.send(`${username} is available.`)
          }
      } catch (e) {
        // Handle errors
      }
  })

  app.listen(3000, ()=> {console.log (`Server live on PORT: ${3000}`);})
```
