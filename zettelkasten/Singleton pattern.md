created:: 2024-04-14 09:16
status:: #zettel/permanent 
tags:: #algorithm  #pattern 
## What is it?
It is a pattern can allow use a unique instance to reference a class. Basically, you don't create a new instance of a class if it class already instanced.
## Advantages
You can use singletons to global states. A good example of use is a logger. You can create a logger file to create a request context, and retrieve the same context in other files only using the class. It's allow you make some solutions in some cases.
## Disadvantages
It can cause a behavior don't expected, for this, it's considered a ant-pattern.