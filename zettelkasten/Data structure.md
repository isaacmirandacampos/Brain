created:: 2024-04-14 09:47
status:: #zettel/permanent 
tags:: #data-structure #performance #algorithm 

## What is data structure?
Data structure is a study of how manager our data using the best algorithm to our use case. It's enable you to known the trade offers of approach.
### Static sets
Static sets are *immutable* in all cycle life, and example of static set is a vetor.
v = [1, 2, 3, 4, 5]
#### Vantagens
- Direct matching of computer memory
- Most simple information access (indexing)
	- simplest mathematical count
- Necessary memory is allocated in advance
#### Desvantagens
- Impossible resize
- Inefficiency to do some common operations
	- Insert or remove a new value on array
	- Unused time and wasted memory
![[Example of removing data on static sets.png]]
*Example* the code to removing data in a static set
```python
def delete(vetor, position, length_usable):
	for i in range(position, length_usable - 1):
		vetor[i] = vetor[i + 1]
	return vetor, length_usable - 1
```
### Dynamic sets
Dynamic sets are objects *mutable*, more simple and effective. It working using pointers that be target a address in memory.

![[Dynamic set of data in memory.png]]
In this image, we can see the structure:
```js
const p = {
	code: 1234,
	price: 10.0,
	name: "Refrigerante"
}
```
When we use:
```js
p.price
```
Our pointer is in *seventh* cell and it pointing for the *fourth* cell in dynamic set.

Dynamic sets are a idea, the real dynamic sets are:
[[Heap structure]]
# References
-  [USP-Data structure](https://eaulas.usp.br/portal/video?idItem=15593)