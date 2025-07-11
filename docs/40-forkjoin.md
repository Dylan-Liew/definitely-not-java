# Fork and Join Summary

## Fork/Join Framework Concept
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

## ForkJoinPool
- Thread pool for fork/join tasks
- Work-stealing deque
- Automatic load balancing
- Example:
  ```java
  ForkJoinPool pool = new ForkJoinPool();
  Long result = pool.invoke(new SumTask(array, 0, array.length));
  ```

## RecursiveTask Operations
1. Fork:
   ```java
   leftTask.fork();  // submit task for async execution
   ```

2. Join:
   ```java
   Long result = leftTask.join();  // wait for result
   ```

3. Compute:
   ```java
   Long result = rightTask.compute();  // execute directly
   ```

## Fork/Join Patterns
1. Good Pattern:
   ```java
   left.fork();
   right.compute();  // compute one side directly
   left.join();
   ```

2. Better Pattern:
   ```java
   left.fork();
   Long rightResult = right.compute();
   Long leftResult = left.join();
   return leftResult + rightResult;
   ```

## Performance Considerations
1. Task Granularity:
     - Too small: overhead dominates
     - Too large: poor parallelism
     - Use threshold to switch to sequential
   ```java
   if (end - start <= THRESHOLD) {
     return computeSequentially();
   }
   ```

2. Work Stealing:
     - Idle threads steal work
     - Balances load automatically
     - Efficient for uneven tasks

## Best Practices
- Choose appropriate threshold
- Avoid synchronized methods
- Minimize task dependencies
- Handle exceptions properly
- Profile performance
- Test with different sizes
- Example:
  ```java
  class ParallelTask extends RecursiveTask<Result> {
    @Override
    protected Result compute() {
      if (size <= THRESHOLD) {
        return computeSequentially();
      }
      ParallelTask left = new ParallelTask(leftPart);
      ParallelTask right = new ParallelTask(rightPart);
      left.fork();
      Result rightResult = right.compute();
      Result leftResult = left.join();
      return combine(leftResult, rightResult);
    }
  }
