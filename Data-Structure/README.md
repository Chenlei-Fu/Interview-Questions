# Data Structure

### HashMap v.s HashTable
There are several differences between HashMap and Hashtable in Java:

1. Hashtable is synchronized, whereas HashMap is not. This makes HashMap better for non-threaded applications, as unsynchronized Objects typically perform better than synchronized ones.

2. Hashtable does not allow null keys or values. HashMap allows one null key and any number of null values.

3. One of HashMap's subclasses is LinkedHashMap, so in the event that you'd want predictable iteration order (which is insertion order by default), you could easily swap out the HashMap for a LinkedHashMap. This wouldn't be as easy if you were using Hashtable.


### List v.s Map v.s Set (Collection)
* Map: An object that maps keys to values. A map cannot contain duplicate keys; each key can map to at most one value.

* List: an ordered collection (also known as a sequence). The user of this interface has precise control over where in the list each element is inserted. We can insert/delete/search for specific element in the list. 

* Set: a collection that contains no duplicate elemtns. 

* Collection: the root interface in the collection hierarchy. A collection represents a group of objects, known as its elements. Some collections allow duplicate elements and others do not. Some are ordered and others unordered. 

### Array v.s LinkedList
Linked lists have several advantages over arrays. 
1. Elements can be inserted/deleted into linked lists indefinitely, while an array will eventually either fill up or need to be resized, an expensive operation that may not even be possible if memory is fragmented. 

2. linked lists lend themselves nicely to efficient multi-threaded implementations. The reason for this is that changes tend to be local - affecting only a pointer or two for insert and remove at a localized part of the data structure. So, you can have many threads working on the same linked list.

Arrays, on the other hand, allow random access, while linked lists allow only sequential access to elements. This makes linked lists unsuitable for applications where it's useful to look up an element by its index quickly, such as heapsort. Sequential access on arrays is also faster than on linked lists on many machines due to locality of reference and data caches. Linked lists receive almost no benefit from the cache.

Another disadvantage of linked lists is the extra storage needed for references, which often makes them impractical for lists of small data items such as characters or boolean values. It can also be slow, and with a naïve allocator, wasteful, to allocate memory separately for each new element, a problem generally solved using memory pools.

### How to implement a queue using two stacks?

Keep 2 stacks, let's call them inbox and outbox.

* Enqueue:

Push the new element onto inbox

* Dequeue:

If outbox is empty, refill it by popping each element from inbox and pushing it onto outbox

Pop and return the top element from outbox

```java
public class Queue<E>
{

    private Stack<E> inbox = new Stack<E>();
    private Stack<E> outbox = new Stack<E>();

    public void queue(E item) {
        inbox.push(item);
    }

    public E dequeue() {
        if (outbox.isEmpty()) {
            while (!inbox.isEmpty()) {
               outbox.push(inbox.pop());
            }
        }
        return outbox.pop();
    }

}
```

### String in Java is immutable? How to change it to mutable?
* Immutability: String is immutable means that you cannot change the object itself, but you can change the reference to the object.
```java
String s1 = "java";
s1.concat(" rules"); 
// the VM creates another new String "java rules", but nothing refers to it. So, the second String is instantly lost. We can't reach it.
System.out.println("s1 refers to "+s1);  // Yes, s1 still refers to "java"
```

Why immutable? 
The JVM sets aside a special area of memory called the "String constant pool". When the compiler sees a String literal, it looks for the String in the pool. If a match is found, the reference to the new literal is directed to the existing String and no new String object is created. The existing String simply has one more reference. Here comes the point of making String objects immutable:

* Change it to mutable? 
Java has two classes StringBuffer and StringBuilder where String class is used to the immutable string.



