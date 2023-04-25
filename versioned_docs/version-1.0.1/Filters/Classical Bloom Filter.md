Classical Bloom Filters are an extension of Bloom Filters that use a bit array and hash functions to represent the membership of an element in a set. They are probabilistic data structures used for membership testing with applications in web caching, spell checkers, virus scanners, Content Delivery Networks (CDN) and network routers.

### 🛳 How to import?

To import the BloomFilter class from the Blumea package into your project, use the following:

```js
const { BloomFilter } = require("blumea");

/**
 * Create a Bloom filter instance for your app.
 * Provide item count and an acceptable false positive rate.
 */

let filter = new BloomFilter(9700, 0.01);
```

By passing the desired item count and false positive rate as arguments to the BloomFilter constructor, you can create a Bloom filter instance with the appropriate settings for your use case.

### 💡 Methods:

- ** insert(element) ** : To add the element to the bloom filter instance.
- ** find(element) ** : To check for element membership with the false positive rate of the filter.
- ** updateFalsePositiveRate(newFalsePostive) ** : To update the filter instance with a new false positive rate.
- ** updateItemCount(newItemCount) ** : To update the filter instance with a new item count.
- ** Utility Methods ** :
  - getHashFunctionCount() or filter.hash_count
  - getBitArraySize() or filter.size

:::note

updateX methods() are experimental. Classical Bloom filters have static false positive rate and item count for a single instance.

:::

### ❗️Usage Warning

- Please note that the false positive rate in a Bloom filter should not exceed 0.999. If this value is exceeded, an exception will be thrown.

- The valid range for false positive rates is between 0.001 and 0.999.

- Sample Code Snipet:

```js
const { BloomFilter } = require("blumea");
let filter = new BloomFilter(20, 0.03);

filter.insert("James Clear");
filter.insert("Paulo Coelho");

console.log(filter.find("blumea")); //return false.
console.log(filter.find("Paulo Coelho")); //return true.

console.log(filter.getHashFunctionCount()); //return the optimal hash func count.

filter.updateFalsePositiveRate(0.0); //warning thrown and filter will update the rate to 0.01.
filter.updateItemCount(50); //updates the item count & recompute parameters.
console.log(filter.getHashFunctionCount()); //return the new optimal hash func count.
```
