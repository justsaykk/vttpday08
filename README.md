# Streams!

### What are streams?

Streams are literally a stream of data.

### What can we do with the stream of data?

We could do operations on streams. We could map it, we could reduce it, we could perform stuff on it!
Streams are also infinite, one could think of it as an assembly line on a 24/7 manufacturing floor.

### Common operations/method on streams:

1. .map()

   - Takes one element and perform stuff on it
   - Expects a stream & a function to do things with the element
   - Returns a stream of the new elements

2. .filter()

   - Just like what it says -> it filters
   - Expects a stream && a test (a.k.a "Predicate")
   - Returns a filtered stream that meets the test

3. .reduce()

   - Takes all the elements and aggregate it to become a single value
   - Expects a starting value
   - Some task to do on the elements

4. .toList()
   - Converts the stream into a list
   - Expects a stream, Returns a List.
   - Terminal command.

### Lingo used in the java documentation:

1. Function
   - a function that does something to the elements and returns something
2. Predicate
   - A test, basically. Returns a stream
3. Consumer
   - Takes a value, and does't return anything

Also, any collection can be converted into a stream!

### A common implementation of streams:

```java
public List<String> search(List<String> bookList, String keyWord) {
        List<String> result = bookList.stream()
                .filter(el -> el.trim().toLowerCase().contains(keyWord.toLowerCase
                ()))
                .toList();
        return result;
    }
```

### Another example:

```java
public static void main(String[] args) {
    List<Integer> intList = new LinkedList<>();
    Random rand = new SecureRandom();

    // Just creating a list of 1000 random numbers
    for (int i = 0; i < 1000; i++) {
        intList.add(rand.nextInt());
    }

    // Doing stuff on the stream:
    intList.stream()
        .map(v -> v * 2)    // Multiplies the element of the stream by 2. Returns a stream.
        .filter(v -> v > 0) // Returns elements that meets the requirement
        .sorted()           // Sorts the stream, returns the sorted stream
        .limit(10)          // Returns a stream of the first 10 numbers
        .forEach(v -> {     // For each number, print to console
            System.out.printf("v: %d", v);
        })
}
```
