# Mergesort
created:: 2024-04-14 09:39
status:: #zettel/fleeting 
tags:: #algorithm #performance 

## What is it?
The merge sort is an ordering algorithm, from divider to conqueror.
### How to use in code?
```python
def mergeSort(data, start, end):
	if start < end: #if there are more than one element
		mid = (start + end) // 2
		mergeSort(data, start, mid)
		mergeSort(data, mid+1, end)
		merge(data, start, mid, end)

def merge(data, start, mid, end):
	left = data[start:mid+1]
	right = data[mid+1:end+1]
	addSentinelValue(left)
	addSentinelValue(right)
	target_index = start
	left_index = 0
	right_index = 0
	while arrayHasTheIndex(target_index, end):
		if left[left_index] < right[right_index]:
			data[target_index] = left[left_index]
			left_index += 1
		else:
			data[target_index] = right[right_index]
			right_index += 1
		target_index += 1

def addSentinelValue(value):
	value.append(float('inf'))

def arrayHasTheIndex(index, size):
	return index <= size

data = [4, 88 , 2, 3, 1, 6, 0, 99]
mergeSort(data, 0, len(data)-1)
print(data)
```
This algorithm needs to *compare 2 values* in order to sort, and there's a scenario where this is a *problem*. If you go through the entire array, the *last element will be missing* from the comparison and it would be left out of the final array. *One way to solve this* is to use a [[Sentinel Value]], which guarantees that the last element will not be missing at the end of the array. In our case, we are always *comparing an infinite value to with the last value in the array*.

## What is the temporal order of execution according to the [[Big-oh notation]]? 
The merge sort algorithm has a time complexity of *O(n log n)* in Big O notation. Let's analyse how this applies to your algorithm:

**Recursive Splitting**: In the *mergeSort* method, the array is split in half at each recursive call (*mergeSort(data, start, mid)* and *mergeSort(data, mid+1, end)*). This results in a decomposition that creates *log n levels* of recursive calls, where *n* is the number of elements in the array.

**Merge**: At *each level of recursion*, the *merge* function *is called* to merge *two halves of an array*. This operation has a time complexity of *O(n)* for each recursion level, as it loops through all the elements of the sub-parts to merge them back together.

*Combining these two parts*, the total complexity of the merge sort algorithm is determined by *the number of split levels (log n) multiplied by the merge cost at each level (n)*, resulting in an O(n log n) time complexity.

See more in: [[big oh notation - mergesort]]
## When we don't use it?
It is an algorithm that requires the creation of new contexts, it *generates 2 sub-arrays* for the algorithm to work.
If we *have smaller arrays, it is more advantageous to use another algorithm with fewer constants*, since the assignments of the constants in the algorithm have more influence than the number of interactions.

# References
-  [e-Aulas da USP :: Mod. 2 - Análise de Algoritmos - vídeo 1 de 3 -...](https://eaulas.usp.br/portal/video?idItem=20198)
- [Making Sense of Merge Sort \[Part 1\] | by Vaidehi Joshi | basecs | Medium](https://medium.com/basecs/making-sense-of-merge-sort-part-1-49649a143478)

