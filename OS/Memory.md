# Memory
### Difference between linear storage and nonliner storage
#### linear
A Linear data structure have data elements arranged in sequential manner and each member element is connected to its previous and next element. This connection helps to traverse a linear data structure in a single level and in single run. Such data structures are easy to implement as computer memory is also sequential. 
Examples of linear data structures are List, Queue, Stack, Array etc.

Linear structures are further divided into sequential storage and chained storage.
* Sequential storage: individual elements are stored in a continuous address space, and logically adjacent elements are also adjacent in physical memory, such as arrays.
* Chain storage: Individual elements are stored in an arbitrary address space, and logically adjacent elements are not linked in physical memory, as in a chain table.


#### Nonlinear
A non-linear data structure has no set sequence of connecting all its elements and each element can have multiple paths to connect to other elements. Such data structures supports multi-level storage and often cannot be traversed in single run. Such data structures are not easy to implement but are more efficient in utilizing computer memory. 
Examples of non-linear data structures are Tree, BST, Graphs etc.

### How processes share memory?
To use shared memory, we have to perform 2 basic steps:

1. Request to the operating system a memory segment that can be shared between processes. The user can create/destroy/open this memory using a shared memory object: An object that represents memory that can be mapped concurrently into the address space of more than one process..
2. Associate a part of that memory or the whole memory with the address space of the calling process. The operating system looks for a big enough memory address range in the calling process' address space and marks that address range as an special range. Changes in that address range are automatically seen by other process that also have mapped the same shared memory object.