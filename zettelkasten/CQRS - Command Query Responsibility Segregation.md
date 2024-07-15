# CQRS - Command Query Responsibility Segregation
created:: 2024-07-15 20:31
status:: #zettel/fleeting
tags:: #solution-architecture 

-  The software is divided into two parts, command stack and query stack. The command stack is responsible for writing commands, it's will write in db and have the domain layer to manage business rule. When we only need to read, have the domain is useless, and we can only make the visualization of the data avoiding this layer. It's allow have two databases, one to read and other to write.