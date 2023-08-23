#java #threading

# Basics
---
It's better not to create and manage lifecycle of threads manually, instead use a ThreadPool.
## Types
- **newFixedThreadPool:** A fixed-size thread pool creates threads as tasks are submitted, up to maximum pool size, and then attempts to keep the pool size constant (adding new threads if a thread dies due to an unexpected exception).
- **newCachedThreadPool:** A cached thread pool has more flexibility to reap idle threads when the current size of the pool exceeds the demand for processing, and to add new threads when demand increases, but **places no bounds on the size of the pool.**
- **newSingleThreadExecutor:** A single-threaded executor creates a single worker thread to process tasks, replacing it if it dies unexpectedly. **Tasks are guaranteed to be processed** sequentially according to the order imposed by the task queue (FIFO, LIFO, priority order).
- **newScheduledThreadPool:** A fixed-size thread pool that supports delayed and periodic task execution, similar to _Timer_.

ExecutorService spawns NonDaemon threads by default. We can also control the maxConcurrency of tasks, execution order of tasks (LIFO, FIFO) etc.

> Note: **JVM (Java Virtual Machine) can't exit until all the non-daemon threads have terminated, so failing to shut down an _Executor_ could prevent the JVM from exiting.**
> 
> (Daemon threads are the ones that exit when the main thread exits)

Check out using ExecutorService to send [SSEe in Spring](Server%20Sent%20Events%20In%20Spring).