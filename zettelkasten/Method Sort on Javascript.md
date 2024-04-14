created:: 2024-04-14 09:23
status:: #zettel/permanent 
tags:: #algorithm #performance 
## How it's works?
The sort method converts each value on the array into a string, it's mean that in some cases the sort is wrong.
The code below shows an example of this.
```js
let numArray = [3, 10, 4, 21, 5, 9, 2, 6, 5, 3, 5].sort();
console.log(numArray); // Output: [10,2,21,3,3,4,5,5,5,6,9]
```

One way to solve this is to use the function inside sort method.
The code below gives an example of this solution.
```js
let numArr = [10, 5, 80];
numArr.sort((a, b) => a - b);
console.log(numArr); // Output: [5, 10, 80]
```
Compare to make sure the result is what you expected.
## Big-oh
The sort method implemented by browsers generally uses the [[Mergesort|mergesort]] algorithm, which is o(n log n).
The V8 (engine of  google chrome) uses [[Quicksort]] when applying in small arrays and mergesort in large arrays. 
# References
-  [JavaScript Sort Array - How to Sort an Array Accurately](https://www.freecodecamp.org/news/how-to-sort-javascript-array-accurately/)
