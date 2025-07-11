# Asynchronous Programming Summary

## CompletableFuture Concept
- Represents a future result
- Supports non-blocking operations
- Enables asynchronous programming
- Example:
  ```java
  CompletableFuture<String> future = 
      CompletableFuture.supplyAsync(() -> 
          expensiveOperation());
  ```

## Creating CompletableFuture
1. Static Factory Methods:
   ```java
   // Complete future
   CompletableFuture.completedFuture(value);
   
   // Run async task
   CompletableFuture.runAsync(() -> task());
   
   // Supply async result
   CompletableFuture.supplyAsync(() -> compute());
   ```

2. Multiple Futures:
   ```java
   CompletableFuture<Void> all = 
       CompletableFuture.allOf(future1, future2);
   
   CompletableFuture<Object> any = 
       CompletableFuture.anyOf(future1, future2);
   ```

## Chaining Operations
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

## Exception Handling
```java
future.exceptionally(ex -> {
    System.err.println(ex);
    return defaultValue;
  })
  .handle((result, ex) -> {
    if (ex != null) {
      return handleError(ex);
    }
    return result;
  });
```

## Async vs Sync Methods
1. Async Methods:
   ```java
   // Executes in different thread
   future.thenApplyAsync(x -> process(x));
   future.thenComposeAsync(x -> compute(x));
   future.thenCombineAsync(other, (x,y) -> combine(x,y));
   ```

2. Sync Methods:
   ```java
   // Executes in same thread
   future.thenApply(x -> process(x));
   future.thenCompose(x -> compute(x));
   future.thenCombine(other, (x,y) -> combine(x,y));
   ```

## Best Practices
- Use async operations for I/O
- Handle exceptions properly
- Don't block unnecessarily
- Consider thread pools
- Chain operations efficiently
- Test async behavior
- Example:
  ```java
  CompletableFuture<String> result = 
      CompletableFuture.supplyAsync(() -> readFile())
          .thenApplyAsync(content -> process(content))
          .exceptionally(ex -> handleError(ex));
