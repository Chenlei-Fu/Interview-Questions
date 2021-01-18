# Threads

### What is daemon thread?
A daemon thread is a thread that does not prevent the JVM from exiting when the program finishes but the thread is still running. An example for a daemon thread is the garbage collection.

You can use the setDaemon(boolean) method to change the Thread daemon properties before the thread starts.

### Multi-threads
Multithreading is the ability of CPU (or a single core in a multi-core processor) to provide multiple threads of execution concurrently, supported by the operating system. In a multithreaded application, the threads share the resources of a single or multiple cores, which include the computing units, the CPU caches, and the translation lookaside buffer (TLB).
Examples:
* Web servers - A threaded web server handles each request with a new thread. There is a thread pool and every time a new request comes in, it is assigned to a thread from the thread pool.
* Text Editors - When you are typing in an editor, spell-checking, formatting of text and saving the text are done concurrently by multiple threads. The same applies for Word processors also.
* IDE - IDEs like Android Studio run multiple threads at the same time. You can open multiple programs at the same time. It also gives suggestions on the completion of a command which is a separate thread.


### Mutex Locks
To resolve the race condition, which occurs when two or more threads can access shared data and they try to change it at the same time, the mutex lock comes in.

Mutex lock is a synchronization mechanism for enforcing limits on access to a resource in an environment where there are many threads of execution. A Mutex is a mutually exclusive flag. It acts as a gate keeper to a section of code allowing one thread in and blocking access to all others. This ensures that the code being controled will only be hit by a single thread at a time. Just be sure to release the mutex when you are done.

### How to serialize threads?
Aquire a lock to only allow one thread to enter the critical section:
```java
public class Coordinator{
    private static object lockObj = new Object();
    public void initialize(InitializeArguments args){
        lock(lockObj){
            if (!args.Entity.IsInitialized)
            {
            ...
            }
        }
    }
}
```