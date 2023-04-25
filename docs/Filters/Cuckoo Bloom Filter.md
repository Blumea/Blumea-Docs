### 🛳 Import

```js
//import the the class from blumea package
const { CuckooBloomFilter } = require("blumea");

//create a filter instance with itemCount && falsePositive rate.
let filter = new CuckooBloomFilter(799, 0.02);
```

### 💡 Public Access Methods

- ** insert(element) ** : To add the element to the bloom filter instance.
  - This will set element bit count to 1 and add the element.
  - If the same element is added x number of time, count_bit will maintain the count of the specific element in the filter.
- ** find(element) ** : To check for element membership with the false positive rate of the filter.
- ** updateFalsePositiveRate(newFalsePostive) ** : To update the filter instance with a new false positive rate.
- ** updateItemCount(newItemCount) ** : To update the filter instance with a new item count.
- ** Utility Methods ** :
  - getHashFunctionCount() or filter.hash_count
  - getBitArraySize() or filter.size
