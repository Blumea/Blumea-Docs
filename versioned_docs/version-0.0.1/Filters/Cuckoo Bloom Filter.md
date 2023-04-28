A cuckoo bloom filter is a variation of a Bloom filter, which is a probabilistic data structure used for efficient set membership testing. Like a Bloom filter, a cuckoo bloom filter represents a set of items as a bit array, but it uses two hash functions and two hash tables instead of one. Cuckoo bloom filters offer better performance than standard Bloom filters for some use cases, but they are more complex to implement and require more memory. They are commonly used in network routers, firewalls, and other applications where fast and efficient set membership testing is required.

### 🛳 How to import?

To import the BloomFilter class from the Blumea package into your project, use the following:

```js
const { CuckooBloomFilter } = require("blumea");

/**
 * Create a Bloom filter instance for your app.
 * Provide item count and an acceptable false positive rate.
 */

let filter = new CuckooBloomFilter(2999, 0.01);
```

### 💡 Methods

- ** insert(element) ** : This function inserts the element into the filter by hashing it with multiple hash functions and placing it into one of two tables. If both tables are full, it attempts cuckoo hashing by swapping the current element with an existing one. If the element can't be inserted after a certain number of attempts, it returns false. Successful insertion returns true.
- ** find(element) ** : This function checks if an element exists in the filter by hashing it with the same functions used during insertion and checking the corresponding slots in either table. If the element is found, it returns true. If not, it returns false.
- ** Utility Methods ** :

  - getHashFunctionCount() or filter.hash_count
  - getBitArraySize() or filter.size

- Sample Node app with Cuckoo Bloom Filter:

```js
const { CuckooBloomFilter } = require("blumea");

// Create a new Cuckoo Bloom Filter with 100 items, 0.05 false positive rate.
const cf = new CuckooBloomFilter(100, 0.05);

// Insert some elements
cf.insert("apple");
cf.insert("banana");
cf.insert("strawberry");

// Check if an element exists in the filter
console.log(cf.contains("banana")); // Returns true
console.log(cf.contains("mango")); // Returns false

// Check the number of hash functions used in the filer
console.log(cf.getHashCount());
```
