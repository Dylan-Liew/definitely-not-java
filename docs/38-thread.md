# Threads Summary

## Thread Concept
- Unit of program execution
- Independent sequence of operations
- Can run concurrently
- Example:
  ```java
  Thread t = new Thread(() -> {
    System.out.println("Running in new thread");
  });
  t.start();
  ```

## Creating Threads
1. Using Runnable:
   ```java
   Runnable task = () -> {
     // task code here
   };
   Thread thread = new Thread(task);
   thread.start();
   ```

2. Extending Thread:
   ```java
   class MyThread extends Thread {
     public void run() {
       // task code here
     }
   }
   new MyThread().start();
   ```

## Thread States
- NEW: Created but not yet started
- RUNNABLE: Executing or ready to execute
- BLOCKED: Waiting for monitor lock
- WAITING: Waiting indefinitely
- TIMED_WAITING: Waiting for specified time
- TERMINATED: Completed execution

## Thread Operations
1. Basic Operations:
   ```java
   thread.start();     // start thread
   thread.join();      // wait for completion
   thread.sleep(1000); // pause execution
   thread.interrupt(); // interrupt thread
   ```

2. Thread Information:
   ```java
   Thread.currentThread().getName();    // get name
   Thread.currentThread().isAlive();    // check if alive
   Thread.currentThread().setPriority(5); // set priority
   ```

## Thread Safety Issues
1. Race Conditions:
   ```java
   // Unsafe
   counter++;  // not atomic
   
   // Safe
   synchronized(lock) {
     counter++;
   }
   ```

2. Visibility Problems:
   ```java
   // May have visibility issues
   boolean flag = false;
   
   // Guaranteed visibility
   volatile boolean flag = false;
   ```

## Best Practices
- Use thread pools when possible
- Handle interruptions properly
- Avoid shared mutable state
- Use proper synchronization
- Document thread safety
- Test concurrent behavior
- Example:
  ```java
  try {
    thread.join();
  } catch (InterruptedException e) {
    Thread.currentThread().interrupt();
    // handle interruption
  }
