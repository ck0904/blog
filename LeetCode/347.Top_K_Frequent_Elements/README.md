### 347.Top K Frequent Elements

Given a non-empty array of integers, return the k most frequent elements.

```js
Example 1:

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

Example 2:

```js
Input: nums = [1], k = 1
Output: [1]
```

Note:

* You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
* Your algorithm's `time complexity must be better than O(n log n)`, where n is the array's size.
* It's guaranteed that `the answer is unique`, in other words the set of the top k frequent elements is unique.
* You can return the answer in any order.

### Analyze

一种思路是将各个元素出现的频率统计进哈希表中, 然后对出现频率进行排序, 取频率排前 k 的元素, 这样的时间复杂度 O(nlog n) 级别, 由于题目给出了时间复杂度不超过 `(n log n)` 这一限制, 因而我们要思考其它方式🤔, 在这里我们可以使用*优先队列*的思想。

```js
{
  1: 3,
  2: 2,
  3: 1
}
```

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
  const obj = {}
  for (let i = 0; i < nums.length; i++) {
    if (!obj[i]) {
      obj[nums[i]] = 1
    } else {
      obj[nums[i]] = obj[nums[i]]++
    }
  }

  const list = []

  const keysArr = Object.keys(obj)
  for (let i = 0; i < keysArr.length; i++) {
    if (list[0] && list[0].value < value) {
      list.unshift({ key, value })
    } else {
      list.push({ key, value })
    }
  }

  const result = []
  list.map((obj, index) => {
    if (index < k) {
      result.push(obj.value)
    }
  })
  return result
}
```