A Partitioned Bloom Filter (PBF) is a probabilistic data structure that allows efficient set membership testing. A PBF consists of multiple independent Bloom filters, each of which has a unique hash function. The Bloom filters are divided into partitions, and each partition is allocated a portion of the overall bit array used by the PBF. Each element is hashed by each of the unique hash functions, and the resulting hash values are used to set bits in the corresponding partitions of the Bloom filters.

### 🛳 How to import?

To import the BloomFilter class from the Blumea package into your project, use the following:

```js
const { PartitionedBloomFilter } = require("blumea");

/**
 * Create a Bloom filter instance for your app.
 * Provide item count and an acceptable false positive rate.
 */

let filter = new PartitionedBloomFilter(5999, 0.03);
```

### 💡 Methods

- ** insert(element) ** : To add the element to the bloom filter instance.

- ** find(element) ** : To check for element membership with the false positive rate of the filter.
- ** updateFalsePositiveRate(newFalsePostive) ** : To update the filter instance with a new false positive rate.
- ** updateItemCount(newItemCount) ** : To update the filter instance with a new item count.
- ** Utility Methods ** :
  - getHashFunctionCount() or filter.hash_count
  - getBitArraySize() or filter.size

### ❗️Usage Warning

- Please note that the false positive rate in a Bloom filter should not exceed 0.999. If this value is exceeded, an exception will be thrown.

- The valid range for false positive rates is between 0.001 and 0.999.

- Sample Node app with Partition Bloom Filter:

```js
const { PartitionedBloomFilter } = require("blumea");

// Create a new Partitioned Bloom Filter with 100 items, 0.05 false positive rate, and 4 partitions.
const pbf = new PartitionedBloomFilter(100, 0.05, 4);

// Insert some elements
pbf.insert("foo");
pbf.insert("bar");

// Check if an element exists in the filter
console.log(pbf.find("foo")); // Returns true
console.log(pbf.find("baz")); // Returns false

// Check the number of hash functions used in each partition
console.log(pbf.getHashCountPerPartition());
```
