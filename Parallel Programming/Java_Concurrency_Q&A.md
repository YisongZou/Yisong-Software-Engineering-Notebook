Java Concurrency Q&A; — Markdown Summary
# Java Concurrency Q&A — Markdown Summary
## 1) Thread synchronization using `Object.wait()` / `notify()` / `notifyAll()`
**Overview**
In Java every object has a monitor. The classic low-level coordination methods are:
- `wait()` — must be called while holding the object's monitor (inside `synchronized`). The thread releases the monitor and enters WAITING (or TIMED_WAITING if wait with timeout). It will remain waiting until another thread calls `notify()` / `notifyAll()` on the same object (or the thread is interrupted or timed out).
- `notify()` — wakes up *one* thread waiting on the object's monitor (which one is JVM-dependent). The awakened thread still has to reacquire the monitor to proceed.
- `notifyAll()` — wakes up *all* waiting threads on the object's monitor. Each awakened thread will contend to reacquire the monitor.
**Best practices / pitfalls**
- Always call `wait()` inside a loop that checks the condition: `while (!cond) wait();` — to handle spurious wakeups and re-check predicates.
- Must call wait/notify from synchronized block; otherwise `IllegalMonitorStateException`.
- Use `notifyAll()` when multiple kinds of waiters exist (e.g., producers & consumers) to avoid missed wakeups or livelock.
- Prefer higher-level constructs (`BlockingQueue`, `Lock`+`Condition`) over raw wait/notify for clarity and safety.
**Markdown Example (Java):**
```java
synchronized(lock) {
 while (!condition) {
 lock.wait(); // releases lock, waits
 }
 // do work
 lock.notifyAll();
}
```
---
## 2) Spin lock vs Mutex — Java equivalents, pros/cons, and hybrid mutex
**Definitions**
- **Spin lock (busy-wait):** Thread repeatedly polls a flag or uses CAS until it acquires the lock; it does not block or yield the CPU. Good when the expected wait time is very short.
- **Mutex (blocking lock):** If lock is unavailable the thread blocks and is suspended (parked) by the JVM/OS; yields CPU. Examples: `synchronized`, `ReentrantLock`.
- **Hybrid mutex:** Combine both: attempt to acquire via spinning for a short time; if unsuccessful, block. Reduces context-switch overhead for short waits while avoiding wasteful CPU burning for long waits.
**Java mapping**
- `synchronized` and `ReentrantLock` are blocking mutexes implemented by the JVM. Modern JVMs use lock optimizations: biased locking, lightweight locking, and *adaptive spinning* (hybrid behavior) to improve performance under short contention.
- You can manually implement a simple spin lock with `AtomicBoolean.compareAndSet()`:
```java
// Simple SpinLock (not production-grade)
class SpinLock {
 private final AtomicBoolean flag = new AtomicBoolean(false);
 public void lock() {
 while (!flag.compareAndSet(false, true)) {
 // busy-wait
 Thread.yield();
 }
 }
 public void unlock() { flag.set(false); }
}
```
**Pros/Cons**
- Spin lock pros: low latency for short critical sections; avoids expensive kernel transitions.
- Spin lock cons: wastes CPU if wait is long; can worsen throughput.
- Mutex pros: conserves CPU when wait times are long; robust.
- Mutex cons: higher latency due to blocking/unblocking (context switch) overhead.
**Hybrid**
- JVM lock implementations are hybrid: they may spin briefly before parking a thread. You can also implement hybrid algorithms using a bounded spin loop followed by `LockSupport.park()` or using `ReentrantLock.tryLock(timeout, unit)`.
---
## 3) `ReentrantLock` & `Condition`: what is a Condition, how to use, why inside Lock context?
**Concept**
- `ReentrantLock` is a `Lock` implementation with features beyond `synchronized`: tryLock, timed lock acquisition, interruptible locking, configurable fairness.
- `Condition` (from `lock.newCondition()`) is an equivalent of a monitor's wait-set but explicitly associated with a `Lock`. You can create multiple `Condition` objects per `Lock`, giving you multiple waiting queues (e.g., `notEmpty` and `notFull`).
**Why use Condition inside Lock context?**
- `Condition.await()` atomically releases the associated lock and suspends the thread, similar to `wait()` with synchronized. When signalled, the thread must reacquire the lock before returning from `await()`.
- Because `Condition` manipulates the lock's internal queues, calling await/signal without holding the lock would break invariants and lead to race conditions; thus it must be used while holding the lock.
**Example (bounded buffer, ReentrantLock + Condition):**
```java
class BoundedBuffer<T> {
 private final Queue<T> q = new LinkedList<>();
 private final Lock lock = new ReentrantLock();
 private final Condition notFull = lock.newCondition();
 private final Condition notEmpty = lock.newCondition();
 private final int capacity;
 public void put(T item) throws InterruptedException {
 lock.lock();
 try {
 while (q.size() == capacity) notFull.await();
 q.add(item);
 notEmpty.signal();
 } finally {
 lock.unlock();
 }
 }
 public T take() throws InterruptedException {
 lock.lock();
 try {
 while (q.isEmpty()) notEmpty.await();
 T item = q.remove();
 notFull.signal();
 return item;
 } finally {
 lock.unlock();
 }
 }
}
```
---
## 4) Classic producer/consumer bounded buffer — implementations
**High-level: BlockingQueue**
- Use `ArrayBlockingQueue` or `LinkedBlockingQueue`. They hide synchronization and correctness tricky parts.
**Low-level: `wait()`/`notify()`**
- Use an intrinsic lock (`synchronized`) and `wait()`/`notifyAll()` to block producers when full and consumers when empty (see earlier example).
**Two-lock queue**
- Idea: decouple enqueue and dequeue with separate locks (head-lock and tail-lock) to allow concurrent enqueues and dequeues. `LinkedBlockingQueue` in Java uses `putLock` and `takeLock` to increase concurrency.
**Non-blocking (lock-free) queue**
- Lock-free queues typically use CAS on head/tail pointers (Michael-Scott queue). Java's `ConcurrentLinkedQueue` is an implementation using `AtomicReference` CAS operations. It avoids blocking, scales well under high concurrency, but algorithms are more complex (ABA, memory reclamation concerns in lower-level languages).
**Example: using `BlockingQueue`**
```java
BlockingQueue<Integer> q = new ArrayBlockingQueue<>(capacity);
q.put(1); // blocks if full
Integer v = q.take(); // blocks if empty
```
---
## 5) Semaphore — what and how to use
**Definition**
- `Semaphore` controls a set of permits. `acquire()` consumes a permit (blocks if none), `release()` returns a permit.
**Use cases**
- Limit concurrent access to a pool of resources (e.g., DB connections).
- Rate-limiting concurrency.
- Implementing certain higher-level coordination patterns.
**Example**
```java
Semaphore sem = new Semaphore(3); // allow up to 3 concurrent holders
try {
 sem.acquire();
 // access resource
} finally {
 sem.release();
}
```
**Notes**
- `Semaphore` can be fair (FIFO) if constructed with fairness parameter.
- A `Semaphore` with zero initial permits can be used as a latch (not typical; prefer CountDownLatch).
---
## 6) HashMap with separate chaining — how to make it thread-safe, lock-free, and fast?
**Background**
- Simple chained HashMap: array of buckets; each bucket is a linked list (or tree). Plain `HashMap` is not thread-safe.
**Design options for concurrency**
1. **Global lock:** easiest, but serializes all accesses — poor concurrency.
2. **Bucket-level locks (lock striping):** each bucket (or stripe) has its own lock. Operations on different buckets can proceed in parallel. Java's older `ConcurrentHashMap` pre-Java 8 used segments (similar idea).
3. **Fine-grained lock-free per-bucket:** maintain bucket head as `AtomicReference<Node>` and use CAS to insert/remove nodes without locking. Deleting requires careful handling (marking nodes, helping, safe memory reclamation).
4. **Hybrid approach (ConcurrentHashMap in Java 8+):**
 - Uses CAS updates on bucket heads.
 - Converts long chains into balanced trees for performance.
 - Uses synchronized locks only for rare cases (e.g., tree-building or resizing).
 - Resizing uses a migration strategy with per-segment transfer and CAS, minimizing global lock time.
**Making it lock-free & fast (practical guidance)**
- Implementing a fully lock-free, resizable hash map is extremely hard and error-prone; it needs to handle ABA, memory reclamation, resizing safely, and linearizability.
- Prefer using `ConcurrentHashMap` which is highly optimized (mix of CAS paths and minimal locking).
- If you must implement a custom concurrent chained map:
 - Use per-bucket `AtomicReference<Node>` for lock-free insertions (CAS-based).
 - Use immutable nodes or copy-on-write approaches for reads (read-only threads read stable snapshots).
 - For deletes/updates, use compare-and-swap loops and logical deletion marking to avoid races; ensure safe reclamation (in Java the GC helps with memory safety).
 - To support fast concurrent reads, design reads to be mostly wait-free (no locks, simple atomic reads) and allow writes to use CAS-based updates.
**Example sketch (simplified insert CAS on bucket head)**
```java
class Node {
 final int hash;
 final K key;
 volatile V value;
 final Node next;
 Node(int h, K k, V v, Node n) { hash=h; key=k; value=v; next=n; }
}
AtomicReferenceArray<Node> table = new AtomicReferenceArray<>(capacity);
void put(K key, V val) {
 int idx = indexFor(key);
 while (true) {
 Node head = table.get(idx);
 // naive check for existing key omitted for brevity
 Node newHead = new Node(hash(key), key, val, head);
 if (table.compareAndSet(idx, head, newHead)) return;
 // else retry
 }
}
```
**Trade-offs**
- CAS-based per-bucket insert is fast and non-blocking for inserts, but lookups/deletes may require traversal and careful handling.
- Resizing table in lock-free way is complex; many practical implementations avoid resizing (use fixed sizing) or use a well-tested library (ConcurrentHashMap).
---
## Final summary & recommendations
- Prefer higher-level concurrency utilities from `java.util.concurrent` (`BlockingQueue`, `Semaphore`, `ReentrantLock`+`Condition`, `ConcurrentHashMap`) unless you have a very specific reason to implement low-level primitives.
- Use `wait()`/`notifyAll()` only when you must — `Condition` or `BlockingQueue` are clearer and safer.
- For short critical sections, hybrid locks (spin then block) can yield better latency; JVM already applies such optimizations.
- For concurrent hash maps, use `ConcurrentHashMap`. Building a correct, fast, resizable lock-free hash map is a significant research/engineering effort.
# End of Markdown Summary
