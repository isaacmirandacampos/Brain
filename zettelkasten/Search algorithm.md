created:: 2024-04-14 09:11
status:: #zettel/permanent 
tags:: #algorithm 
## What is a search algorithm?
A search algorithm is a procedure or formula used to *find specific* data among a *collection of data*. The data can be anything from a simple array of numbers to more complex data structures like a graph or a database. Search algorithms are fundamental to computer science and are used in a wide range of applications, from simple tasks like finding a contact in your phone book to more complex ones like executing queries on a large database or navigating through a map.

There are many types of search algorithms, and they can be broadly classified into two categories:

## The types of search algorithms

### Sequential search
Also known as *linear search*, this is the *simplest search* algorithm. It *checks each element* of the data structure until it finds the target value. If the data structure *is not sorted*, this is often the *only feasible search method*. Its performance is O(n)([[Big-oh notation]]), where n is the number of elements in the data structure, meaning that, in the *worst case, every element needs to be checked*.
### Interval search
These algorithms are *more efficient* and work on *sorted* data structures. They *divide the data into intervals* and discard intervals where the target value cannot possibly be. The most common interval search algorithm is the [[Binary Search]], which repeatedly divides the sorted data in half, discarding the half that does not contain the target value. Its performance in the worst case is *O(log n)*([[Big-oh notation]]), which is much faster than sequential search for large datasets.

#### Search algorithms can also be more specialized, like:
**Hashing**: Involves transforming the search key into an index of an array where the desired data can be found.
**Depth-First and Breadth-First Search (DFS and BFS)**: Used for searching graph data structures.
**Binary Search Tree (BST)**: A tree data structure where each node allows searches to continue only to its left or right child, effectively performing a binary search.
The choice of search algorithm depends on several factors, such as whether the data is sorted or not, the size of the dataset, and the frequency of searches. Some algorithms are better for quick lookups in large, sorted datasets, while others are suited for unsorted data or when adding and removing elements frequently.