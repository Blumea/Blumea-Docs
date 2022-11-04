A Bloom filter is a space-efficient probabilistic data structure that is used to test whether an element is a member of a set.

### 🛳 Imports

```js
//import the the class from blumea package
const { BloomFilter } = require("blumea");

//create a filter instance with itemCount && falsePositive rate.
let filter = new BloomFilter(799, 0.02);
```

### 💡 Public Access Methods

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

- The false positive rate must not exceed 1.0. An exception will be thrown if this value is exceeded.

- Valid Range: 0.01 to 0.99

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
