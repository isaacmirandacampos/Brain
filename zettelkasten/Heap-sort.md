created:: 2024-04-14 09:37
status:: #zettel/fleeting
tags:: #algorithm #performance 
## Prerequisite
- Dynamic set of type [[Heap structure]].
## What is?
Is an ordering algorithm that will orders a *max-heap* ([[Heap structure]]) to a *min-heap* ([[Heap structure]]). It's an O(n log n) algorithm ([[Big-oh notation]]).
### How to implement the heap sorting?
We used the code in the [[Heap structure]] file with the following to below example
```python
vetor = [1,2,3,4,5,6,7,8,9,10]
maxheap = build_max_heap(vetor)
## heapsort algorithm
maxheap_length = len(maxheap)
for i in range(maxheap_length - 1, 0, -1):
	vetor[0], vetor[i] = vetor[i], vetor[0]
	heapify(vetor, i, 0)
```

# References
-  [HEAPSORT-USP](https://eaulas.usp.br/portal/video?idItem=20816)