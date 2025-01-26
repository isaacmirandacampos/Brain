# Memory Management
created:: 2025-01-25 22:11
status:: #zettel/fleeting
tags:: #computer #memory

## Stack
The call stack works like a stack of books, you add some books to the stack and remove them one by one.
In other words, the memory is allocated when the context is running, in the end, will remove the space in use. When a function calls another function, adding a new execution to the current stack, the new context has your stacks. 
The stack has a static size and the limit can be reached, when reached, we call the *stack overflow*.
## Heap
The memory is allocated and the program use the reference to access the value of the memory. It's allow other context to use the same variable to avoid duplicate data. When the context finish, the memory on heap is not erase and for erase you need to make sure to clear the memory manually or wait for the garbage collector erase for you.
In low level languages, you need erase the space in use manually, in bad practices of code, you can cause a *memory leak*.
In high level languages, is common use a garbage collector, it will try to clear the heap memory automatically for you.
### Garbage collector (GC)
The garbage collector isn't free, it will consume your CPU and because of this, the low level languages is more performatic. Exist many strategies to implement an GC. The node.js use the [[generational collection]] and the golang implements the [[tri-color mark-and-sweep algorithm]].
Even though the garbage collector clears the memory automatically, it is still possible that cases memory leaks. Known the language is important to use the best practices and understad the best way to handle your variables.
## Considerations
- Use more the stack memory and avoid use the heap for reduce the garbage collector use.
- Understand how the language will alocate the memory.
- Use with moderation the recursive functions, it can reach the limit of stack.



