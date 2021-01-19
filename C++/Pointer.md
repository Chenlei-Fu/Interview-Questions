# Pointer

### Smart Pointer
#### What's a smart pointer?
It's a type whose values can be used like pointers, but which provides the additional feature of automatic memory management: When a smart pointer is no longer in use, the memory it points to is deallocated.
#### "When should I use one?"
In code which involves tracking the ownership of a piece of memory, allocating or de-allocating; the smart pointer often saves you the need to do these things explicitly.

#### Which smart pointer should I use in which of those cases
* Use std::unique_ptr when you want your object to live just as long as a single owning reference to it lives. For example, use it for a pointer to memory which gets allocated on entering some scope and de-allocated on exiting the scope.
* Use std::shared_ptr when you do want to refer to your object from multiple places - and do not want your object to be de-allocated until all these references are themselves gone.
* Use std::weak_ptr when you do want to refer to your object from multiple places - for those references for which it's ok to ignore and deallocate (so they'll just note the object is gone when you try to dereference).
* Don't use the boost:: smart pointers or std::auto_ptr except in special cases which you can read up on if you must.

#### "So when should I use regular pointers then?"
Mostly in code that is oblivious to memory ownership. This would typically be in functions which get a pointer from someplace else and do not allocate nor de-allocate, and do not store a copy of the pointer which outlasts their execution.