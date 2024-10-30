# Here’s a list of common JavaScript interview questions focused on array manipulation, along with brief explanations and example solutions for each:
<details>
  <summary>
1. How do you remove duplicates from an array?
  </summary>
  
**Solution 1:** Use a Set (which automatically stores only unique values) and spread it back into an array.

```javascript
let arr = [1, 2, 3, 3, 4, 4, 5];
let uniqueArr = [...new Set(arr)]; // Output: [1, 2, 3, 4, 5]
```
**Solution 2:** Use filter with indexOf to keep only the first occurrence of each element.

```javascript
let uniqueArr = arr.filter((item, index) => arr.indexOf(item) === index);
```
</details>
<details>
  <summary>
2. How do you reverse an array without using .reverse()?
  </summary>
  
**Solution:** Use a for loop or reduce to build the array backward.
```javascript
let arr = [1, 2, 3, 4];
let reversed = arr.reduce((acc, val) => [val, ...acc], []); // Output: [4, 3, 2, 1]
```
</details>
<details>
  <summary>
3. How do you find the maximum (or minimum) number in an array?
  </summary>

**Solution:** Use the Math.max or Math.min function with the spread operator.
```javascript
let arr = [3, 5, 7, 2, 8];
let max = Math.max(...arr); // Output: 8
let min = Math.min(...arr); // Output: 2
```
</details>
<details>
  <summary>
4. How do you flatten a nested array (i.e., reduce its depth to 1)?
  </summary>
  
**Solution:** Use Array.flat() for a specific depth, or Array.flat(Infinity) for a completely flat array.
```javascript
let arr = [1, [2, [3, [4]]]];
let flatArr = arr.flat(Infinity); // Output: [1, 2, 3, 4]
```
</details>
<details>
  <summary>
5. How do you find the frequency of each element in an array?
  </summary>
  
**Solution:** Use reduce to create an object that counts each element.
```javascript
let arr = ['a', 'b', 'a', 'c', 'b', 'a'];
let frequency = arr.reduce((acc, val) => {
  acc[val] = (acc[val] || 0) + 1;
  return acc;
}, {}); // Output: { a: 3, b: 2, c: 1 }
```
</details>
<details>
  <summary>
6. How do you remove a specific element from an array?
  </summary>
  
**Solution:** Use filter to create a new array without the specified element.
```javascript
let arr = [1, 2, 3, 4, 5];
let toRemove = 3;
let filteredArr = arr.filter(item => item !== toRemove); // Output: [1, 2, 4, 5]
```
</details>
<details>
  <summary>
7. How do you find if an array contains a specific value?
  </summary>
  
**Solution:** Use includes() to check for a value’s presence.
```javascript
let arr = [1, 2, 3, 4];
let hasThree = arr.includes(3); // Output: true
```
</details>
<details>
  <summary>
8. How do you sort an array of numbers?
  </summary>
  
**Solution:** Use sort() with a compare function for numbers.
```javascript
let arr = [5, 2, 8, 1, 4];
arr.sort((a, b) => a - b); // Output: [1, 2, 4, 5, 8]
```
</details>
<details>
  <summary>
9. How do you merge multiple arrays into one?
  </summary>
  
**Solution:** Use the concat() method or the spread operator to combine arrays.
```javascript
let arr1 = [1, 2];
let arr2 = [3, 4];
let merged = [...arr1, ...arr2]; // Output: [1, 2, 3, 4]
```
</details>
<details>
  <summary>
10. How do you find the intersection of two arrays?
  </summary>
  
**Solution:** Use filter() and includes() to retain only elements present in both arrays.
```javascript
let arr1 = [1, 2, 3];
let arr2 = [2, 3, 4];
let intersection = arr1.filter(item => arr2.includes(item)); // Output: [2, 3]
```
</details>
<details>
  <summary>
11. How do you find the difference between two arrays?
  </summary>
  
**Solution:** Use filter() and includes() to find elements unique to each array.
```javascript
let arr1 = [1, 2, 3];
let arr2 = [2, 3, 4];
let difference = arr1.filter(item => !arr2.includes(item)); // Output: [1]
```
</details>
<details>
  <summary>
12. How do you partition an array into two groups based on a condition?
  </summary>
  
**Solution:** Use reduce() to separate elements into two arrays.
```javascript
let arr = [1, 2, 3, 4, 5];
let [evens, odds] = arr.reduce(
  ([evens, odds], num) => (num % 2 === 0 ? [[...evens, num], odds] : [evens, [...odds, num]]),
  [[], []]
); // Output: evens: [2, 4], odds: [1, 3, 5]
```
</details>
<details>
  <summary>
13. How do you shuffle an array randomly?
  </summary>
  
  **Solution:** Use the Fisher-Yates shuffle algorithm to shuffle elements.
```javascript
function shuffle(arr) {
  for (let i = arr.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [arr[i], arr[j]] = [arr[j], arr[i]];
  }
  return arr;
}
let arr = [1, 2, 3, 4];
shuffle(arr); // Output: A random order of [1, 2, 3, 4]
```
</details>
<details>
  <summary>
14. How do you group elements of an array based on a key?
  </summary>
  
  **Solution:** Use reduce() to group elements based on a specific property or key.
```javascript
let arr = [
  { name: 'Alice', role: 'developer' },
  { name: 'Bob', role: 'designer' },
  { name: 'Charlie', role: 'developer' },
];
let grouped = arr.reduce((acc, obj) => {
  let key = obj.role;
  if (!acc[key]) acc[key] = [];
  acc[key].push(obj);
  return acc;
}, {});
// Output: { developer: [{...}, {...}], designer: [{...}] }
```
</details>
<details>
  <summary>
15. How do you find the cumulative sum of elements in an array?
  </summary>
  
  **Solution:** Use reduce() to calculate cumulative sums up to each index.
```javascript
let arr = [1, 2, 3, 4];
let cumulativeSum = arr.reduce((acc, num, i) => {
  acc[i] = (acc[i - 1] || 0) + num;
  return acc;
}, []);
// Output: [1, 3, 6, 10]
```
</details>
<details>
  <summary>
16. How do you rotate an array k steps to the right?
  </summary>
  
  **Solution:** Use slicing and concatenation to reorder the elements.
```javascript
function rotateRight(arr, k) {
  k = k % arr.length; // Handle cases where k > arr.length
  return arr.slice(-k).concat(arr.slice(0, -k));
}
let arr = [1, 2, 3, 4, 5];
let rotated = rotateRight(arr, 2); // Output: [4, 5, 1, 2, 3]
```
</details>
<details>
  <summary>
17. How do you remove falsy values from an array?
  </summary>

  **Solution:** Use filter to keep only truthy values.
```javascript
let arr = [0, 1, false, 2, '', 3, null, 'a', undefined];
let truthyArr = arr.filter(Boolean); // Output: [1, 2, 3, 'a']
```
</details>
<details>
  <summary>
18. How do you check if all elements in an array are equal?
  </summary>

  **Solution:** Use every to check if all elements match the first element.
```javascript
let arr = [5, 5, 5, 5];
let allEqual = arr.every(val => val === arr[0]); // Output: true
```
</details>
<details>
  <summary>
19. How do you split an array into chunks of a given size?
  </summary>

  **Solution:** Use a loop to break the array into smaller arrays of a specified size.
```javascript
function chunkArray(arr, size) {
  let result = [];
  for (let i = 0; i < arr.length; i += size) {
    result.push(arr.slice(i, i + size));
  }
  return result;
}
let arr = [1, 2, 3, 4, 5];
let chunks = chunkArray(arr, 2); // Output: [[1, 2], [3, 4], [5]]
```
</details>
<details>
  <summary>
    20. How do you remove an element at a specific index in an array?
  </summary>

  **Solution:** Use slice to exclude the element at the specified index.
```javascript
function removeAtIndex(arr, index) {
  return arr.slice(0, index).concat(arr.slice(index + 1));
}
let arr = [1, 2, 3, 4];
let newArr = removeAtIndex(arr, 2); // Output: [1, 2, 4]
```
</details>
<details>
  <summary>
    21. How do you check if two arrays are equal?
  </summary>

  **Solution:** Use every to compare corresponding elements in sorted arrays.
```javascript
function arraysEqual(arr1, arr2) {
  if (arr1.length !== arr2.length) return false;
  return arr1.every((val, index) => val === arr2[index]);
}
let arr1 = [1, 2, 3];
let arr2 = [1, 2, 3];
arraysEqual(arr1, arr2); // Output: true
```
</details>
<details>
  <summary>
    22. How do you move all zeroes in an array to the end?
  </summary>

  **Solution:** Use filter to separate zeroes and non-zeroes, then concatenate.
```javascript
let arr = [0, 1, 0, 3, 12];
let result = arr.filter(num => num !== 0).concat(arr.filter(num => num === 0));
// Output: [1, 3, 12, 0, 0]
```
</details>
<details>
  <summary>
    23. How do you find all pairs in an array that sum to a specific target?
  </summary>

**Solution:** Use nested loops or a hash map to track complements.
```javascript
function findPairs(arr, target) {
  let pairs = [];
  let seen = new Set();
  for (let num of arr) {
    let complement = target - num;
    if (seen.has(complement)) pairs.push([complement, num]);
    seen.add(num);
  }
  return pairs;
}
findPairs([1, 2, 3, 4, 5], 5); // Output: [[2, 3], [1, 4]]
```
</details>
<details>
  <summary>
    24. How do you convert an array of objects into a single object?
  </summary>

  **Solution:** Use reduce to merge array items into a single object.
```javascript
let arr = [{ key: 'a', value: 1 }, { key: 'b', value: 2 }];
let obj = arr.reduce((acc, item) => {
  acc[item.key] = item.value;
  return acc;
}, {});
// Output: { a: 1, b: 2 }
```
</details>
<details>
  <summary>
    25. How do you create a frequency map of values in an array?
  </summary>

  **Solution:** Use reduce to count occurrences.
```javascript
let arr = [1, 2, 2, 3, 3, 3];
let frequencyMap = arr.reduce((acc, val) => {
  acc[val] = (acc[val] || 0) + 1;
  return acc;
}, {});
// Output: { 1: 1, 2: 2, 3: 3 }
```
</details>
<details>
  <summary>
    26. How do you generate all possible subsets of an array?
  </summary>

  **Solution:** Use reduce to add each element to all existing subsets.
```javascript
function subsets(arr) {
  return arr.reduce((subsets, val) => 
    subsets.concat(subsets.map(set => [...set, val])), [[]]);
}
subsets([1, 2]); // Output: [[], [1], [2], [1, 2]]
```
</details>
<details>
  <summary>
    27. How do you transpose a 2D array (matrix)?
  </summary>

  **Solution:** Use nested map functions to swap rows and columns.
```javascript
function transpose(matrix) {
  return matrix[0].map((_, colIndex) => matrix.map(row => row[colIndex]));
}
transpose([[1, 2, 3], [4, 5, 6]]); // Output: [[1, 4], [2, 5], [3, 6]]
```
</details>
<details>
  <summary>
    28. How do you generate a cumulative sum array?
  </summary>

**Solution:** Use reduce to accumulate sums progressively.
```javascript
let arr = [1, 2, 3, 4];
let cumulativeSum = arr.reduce((acc, num, i) => {
  acc[i] = (acc[i - 1] || 0) + num;
  return acc;
}, []);
// Output: [1, 3, 6, 10]
```
</details>
<details>
  <summary>
    29. How do you find the most frequent element in an array?
  </summary>

  **Solution:** Use a frequency map and then find the max frequency.
```javascript
function mostFrequent(arr) {
  let frequencyMap = arr.reduce((acc, val) => {
    acc[val] = (acc[val] || 0) + 1;
    return acc;
  }, {});
  return Object.keys(frequencyMap).reduce((a, b) => 
    frequencyMap[a] > frequencyMap[b] ? a : b);
}
mostFrequent([1, 2, 2, 3, 3, 3]); // Output: 3
```
</details>
<details>
  <summary>
    30. How do you find the longest increasing subsequence in an array?
  </summary>

  **Solution:** Use dynamic programming to find the length of the LIS.
```javascript
function longestIncreasingSubsequence(arr) {
  let dp = Array(arr.length).fill(1);
  for (let i = 1; i < arr.length; i++) {
    for (let j = 0; j < i; j++) {
      if (arr[i] > arr[j]) dp[i] = Math.max(dp[i], dp[j] + 1);
    }
  }
  return Math.max(...dp);
}
longestIncreasingSubsequence([10, 9, 2, 5, 3, 7, 101, 18]); // Output: 4
```
</details>
These questions are a good mix of fundamental array manipulation techniques and more advanced logic that demonstrates problem-solving skills with arrays in JavaScript!
