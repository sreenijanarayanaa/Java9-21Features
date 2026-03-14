☕ Java 9 → Java 21 Important Features

A structured overview of modern Java evolution from Java 9 to Java 21, highlighting the most important language and platform improvements.

🚀 Java 9 (2017)

Java 9 introduced modularity and better APIs, making Java applications more maintainable and scalable.

🧩 1. Java Platform Module System (JPMS)

Also known as Project Jigsaw.

Before Java 9, Java applications were monolithic, meaning everything was on the classpath.

Java 9 introduced modules, which allow you to organize applications into independent units with explicit dependencies.

Example
```
module com.myapp {
    requires java.sql;
    exports com.myapp.service;
}
```
Benefits

✨ Strong encapsulation
✨ Faster startup
✨ Smaller runtime images
✨ Better dependency management

📦 2. Factory Methods for Collections

Java 9 introduced convenient methods to create immutable collections.

Before Java 9
```
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");
```
Java 9+
```
List<String> list = List.of("A", "B", "C");
Set<Integer> set = Set.of(1, 2, 3);
Map<Integer,String> map = Map.of(1,"A",2,"B");
```

Advantages

✔ Less boilerplate code
✔ Immutable collections
✔ Cleaner code

🌊 3. Stream API Improvements

Java 9 enhanced streams with new methods.


* takeWhile()

Stops when condition becomes false.
```
Stream.of(1,2,3,4,5)
      .takeWhile(n -> n < 4)
      .forEach(System.out::println);
```
Output

1
2
3


* dropWhile()

Skips elements until condition becomes false.
```
Stream.of(1,2,3,4,5)
      .dropWhile(n -> n < 3)
      .forEach(System.out::println);
```
Output

3
4
5


🔒 4. Private Methods in Interfaces

Interfaces can now have private helper methods.
```
interface Vehicle {

    private void log() {
        System.out.println("Logging...");
    }

    default void start() {
        log();
        System.out.println("Vehicle started");
    }
}
```
⚡ Java 10 (2018)

Java 10 introduced type inference for local variables.

🧠 Local Variable Type Inference (var)

The compiler automatically infers the variable type.

Example
```
var name = "Java";
var numbers = List.of(1,2,3);
```
Equivalent to:
```
String name = "Java";
List<Integer> numbers = List.of(1,2,3);
```
Benefits

✔ Reduces boilerplate
✔ Improves readability
✔ Makes refactoring easier

🔥 Java 11 (LTS – 2018)

Java 11 is a Long Term Support version widely used in enterprise applications.

✨ New String Methods
isBlank()

Checks if a string contains only whitespace.

"   ".isBlank(); // true
repeat()

Repeats a string multiple times.

"Java".repeat(3);

Output

JavaJavaJava
strip()

Removes leading and trailing whitespace.

"  Java  ".strip();
🌐 Modern HTTP Client API

Java 11 introduced a new HTTP client that supports HTTP/2 and asynchronous requests.

HttpClient client = HttpClient.newHttpClient();

HttpRequest request =
        HttpRequest.newBuilder()
                   .uri(URI.create("https://example.com"))
                   .build();

HttpResponse<String> response =
        client.send(request, HttpResponse.BodyHandlers.ofString());
🎯 Java 12–13

Mostly performance improvements and preview features.

Key addition:

Switch Expressions (Preview)

Switch can return values.

int result = switch(day) {
    case MONDAY -> 1;
    case TUESDAY -> 2;
    default -> 0;
};
🎨 Java 14

Switch expressions became standard.

🔄 Switch Expressions

Old switch:

switch(day) {
    case MONDAY:
        result = 1;
        break;
}

New switch:

int result = switch(day) {
    case MONDAY -> 1;
    case FRIDAY -> 5;
    default -> 0;
};

Benefits

✨ No fall-through errors
✨ More readable
✨ Functional style

🧾 Java 15
📝 Text Blocks (Multiline Strings)

Useful for SQL, JSON, XML.

String json = """
{
  "name": "Java",
  "version": 21
}
""";

Benefits

✔ Cleaner formatting
✔ No escape characters
✔ Better readability

🧱 Java 16
📦 Records (Very Important)

Records are compact immutable data classes.

Instead of writing:

class User {
    private final String name;
    private final int age;

    // constructor, getters, equals, hashCode
}

You can simply write:

record User(String name, int age) {}

Automatically generates

✔ Constructor
✔ Getters
✔ equals()
✔ hashCode()
✔ toString()

Perfect for:

DTOs

API responses

immutable models

🛡 Java 17 (LTS)

Another Long Term Support version widely used in modern systems.

🔐 Sealed Classes

Restrict which classes can extend a class.

public sealed class Shape
        permits Circle, Rectangle {
}

Allowed subclasses:

final class Circle extends Shape {}
final class Rectangle extends Shape {}

Benefits

✔ Better domain modeling
✔ Safer inheritance
✔ Improved maintainability

🧵 Java 19–20

Focused on concurrency improvements.

⚙️ Virtual Threads (Preview – Project Loom)

Traditional threads are heavyweight.

Virtual threads are lightweight threads managed by the JVM.

Thread.startVirtualThread(() -> {
    System.out.println("Running virtual thread");
});

Benefits

🚀 Handle millions of concurrent tasks
🚀 Simplifies asynchronous programming
🚀 Better scalability

🌟 Java 21 (Latest LTS – 2023)

Java 21 is the latest Long Term Support release.

🧵 1. Virtual Threads (Final)

Virtual threads became production ready.

try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {

    executor.submit(() -> {
        System.out.println("Task running");
    });

}

Benefits

✔ Massive concurrency
✔ Simpler code compared to reactive programming
✔ Ideal for microservices

🎭 2. Pattern Matching for Switch

Switch can match types and patterns.

switch (obj) {
    case Integer i -> System.out.println("Integer: " + i);
    case String s -> System.out.println("String: " + s);
    default -> System.out.println("Unknown type");
}
📦 3. Record Patterns

Allows destructuring records.

record Point(int x, int y) {}

if (obj instanceof Point(int x, int y)) {
    System.out.println(x + "," + y);
}
🧩 4. Sequenced Collections

Provides consistent ordering for collections.

Examples

List

LinkedHashSet

LinkedHashMap

New methods:

getFirst()
getLast()
reversed()
📊 Summary Table
Version	Major Features
Java 9	Modules, Stream improvements
Java 10	var type inference
Java 11	HTTP Client, String APIs
Java 14	Switch expressions
Java 15	Text blocks
Java 16	Records
Java 17	Sealed classes
Java 19	Virtual threads (preview)
Java 21	Virtual threads, pattern matching
💡 Why These Features Matter

Modern Java features help developers:

✔ Write cleaner code
✔ Improve performance
✔ Build scalable microservices
✔ Reduce boilerplate code
✔ Improve concurrency handling
