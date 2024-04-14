created:: 2024-04-14 09:43
status:: #zettel/permanent 
tags:: #algorithm #performance 

## Introduction
It is a example that how to improve performance avoiding a loop inside other loop. It example is using javascript, but we can use others languages too.
#### Hands on code
We start setting the *users* array and a *list* arrays. The data that we will use to validate our performance.

```javascript
let users = []
for (let i = 0; i < 9999; i++) {
	users.push({
		id: i,
		name: `user${i}`
	})
}
let list = []
for (let i = 0; i < 100000; i++) {
	list.push({
		id: i,
		name: `user${i}`,
		created_at: new Date().toISOString()
	})
}
```

The next example, we are using a code in *quadratic time order O(n²)*:

```javascript
console.time('Adding new property on list of users, using find method inside map')
const newPropertiesOnUserList = users.map(user => {
	return {
		...user,
		created_at: list.find(item => item.id === user.id).created_at
	}
})
console.timeEnd('Adding new property on list of users, using find method inside map')
```
The output is:
```bash
Adding new property on list of users, using find method inside map: 45.989ms
```

Now we use two loops in *linear time order O(n)*:
```javascript
console.time('Adding new property on list of users, changing list structure to no use a new loop inside map')
const remappedList = list.reduce((acc, item) => {
	acc[item.id] = item
	return acc
}, {})
const newPropertiesOnUserRemapped = users.map(user => {
	return {
		...user,
		created_at: remappedList[user.id].created_at
	}
})
console.timeEnd('Adding new property on list of users, changing list structure to no use a new loop inside map')
```
The output is:
```bash
Adding new property on list of users, changing list structure to no use a new loop inside map: 12.325ms
```

### Conclusions
Same we make *two linear time order*, it's better instead loops *in quadratic time order*.
in our test the code was *3x more effective*.