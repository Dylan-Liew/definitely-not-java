# Concurrency

## Threads

### Thread Concept
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

### Creating Threads
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

### Thread States
- NEW: Created but not yet started
- RUNNABLE: Executing or ready to execute
- BLOCKED: Waiting for monitor lock
- WAITING: Waiting indefinitely
- TIMED_WAITING: Waiting for specified time
- TERMINATED: Completed execution

### Thread Safety Issues
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

## Parallel Streams

### Parallel Processing Concept
- Concurrent execution of tasks
- Uses multiple threads/cores
- Automatic work distribution
- Example:
  ```java
  List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
  numbers.parallelStream()
         .map(x -> x * 2)
         .collect(Collectors.toList());
  ```

### Creating Parallel Streams
1. From Collection:
   ```java
   // Method 1
   list.parallelStream()
   
   // Method 2
   list.stream().parallel()
   ```

2. From Arrays:
   ```java
   Arrays.stream(array).parallel()
   ```

### Performance Considerations
1. When to Use:
     - Large data sets
     - Computationally intensive
     - Independent operations
     - Multiple cores available

2. When to Avoid:
     - Small data sets
     - IO-bound operations
     - Operations with dependencies
     - Single core systems

## Asynchronous Programming

### CompletableFuture Concept
- Represents a future result
- Supports non-blocking operations
- Enables asynchronous programming
- Example:
  ```java
  CompletableFuture<String> future = 
      CompletableFuture.supplyAsync(() -> 
          expensiveOperation());
  ```

### Creating CompletableFuture
1. Static Factory Methods:
   ```java
   // Complete future
   CompletableFuture.completedFuture(value);
   
   // Run async task
   CompletableFuture.runAsync(() -> task());
   
   // Supply async result
   CompletableFuture.supplyAsync(() -> compute());
   ```

### Chaining Operations
1. Transformations:
   ```java
   future.thenApply(x -> x * 2)        // map
         .thenCompose(x -> compute(x))  // flatMap
         .thenCombine(other, (x,y) -> x + y);
   ```

2. Side Effects:
   ```java
   future.thenAccept(System.out::println)  // consumer
         .thenRun(() -> cleanup());        // runnable
   ```

## Fork/Join Framework

### Fork/Join Framework Concept
- Divide-and-conquer parallelism
- Work-stealing algorithm
- Recursive task decomposition
- Example:
  ```java
  class SumTask extends RecursiveTask<Long> {
    private final long[] array;
    private final int start;
    private final int end;
    
    @Override
    protected Long compute() {
      if (end - start <= THRESHOLD) {
        return computeDirectly();
      }
      int mid = (start + end) / 2;
      SumTask left = new SumTask(array, start, mid);
      SumTask right = new SumTask(array, mid, end);
      left.fork();
      return right.compute() + left.join();
    }
  }
  ```

### ForkJoinPool
- Thread pool for fork/join tasks
- Work-stealing deque
- Automatic load balancing
- Example:
  ```java
  ForkJoinPool pool = new ForkJoinPool();
  Long result = pool.invoke(new SumTask(array, 0, array.length));
  ```

### Best Practices
- Choose appropriate threshold
- Avoid synchronized methods
- Minimize task dependencies
- Handle exceptions properly
- Test with different sizes
