Java 8 → Java 21 Important Features (Interview Focus)
Java 8 (2014) – The Most Important Release

This version introduced modern Java programming style.

1. Lambda Expressions

Allows writing functional style code.

List<String> list = Arrays.asList("A", "B", "C");

list.forEach(x -> System.out.println(x));

Benefits

Less boilerplate

Functional programming

Used heavily with Streams

2. Functional Interfaces

Interfaces with only one abstract method.

Examples:

Predicate

Function

Supplier

Consumer

Predicate<Integer> isEven = x -> x % 2 == 0;
3. Stream API

Used for processing collections declaratively.

List<Integer> nums = List.of(1,2,3,4,5);

nums.stream()
    .filter(n -> n % 2 == 0)
    .map(n -> n * 2)
    .forEach(System.out::println);

Operations:

filter

map

reduce

collect

sorted

4. Default Methods in Interfaces

Interfaces can have method implementations.

interface Vehicle {
    default void start() {
        System.out.println("Vehicle started");
    }
}
5. Optional Class

Avoids NullPointerException.

Optional<String> name = Optional.ofNullable(null);

System.out.println(name.orElse("Default"));
6. New Date and Time API (java.time)

Better replacement for Date and Calendar.

Classes:

LocalDate

LocalTime

LocalDateTime

ZonedDateTime

LocalDate today = LocalDate.now();
Java 9 (2017)
1. Module System (Project Jigsaw)

Introduced modular Java applications.

File: module-info.java

module mymodule {
    requires java.sql;
}

Benefits

Better encapsulation

Faster startup

Smaller applications

2. Factory Methods for Collections
List<Integer> list = List.of(1,2,3);
Set<String> set = Set.of("A","B");
Map<Integer,String> map = Map.of(1,"A",2,"B");
3. Stream API Improvements

New methods:

takeWhile()

dropWhile()

iterate()

Stream.iterate(1, n -> n < 10, n -> n + 2)
      .forEach(System.out::println);
Java 10 (2018)
Local Variable Type Inference (var)
var list = new ArrayList<String>();

Compiler infers the type.

Rules

Works only for local variables

Not for fields or method parameters

Java 11 (LTS)

Important because many companies still use it.

1. New String Methods
"".isBlank();
"Hello".repeat(3);
" Hello ".strip();
2. Lambda Parameter var
(var x, var y) -> x + y
3. HTTP Client API

Modern HTTP client.

HttpClient client = HttpClient.newHttpClient();

Supports

HTTP/2

Async requests

Java 14
Switch Expressions (Major Improvement)

Old switch:

switch(day) {
    case MONDAY:
        result = 1;
        break;
}

New switch:

int result = switch(day) {
    case MONDAY -> 1;
    case TUESDAY -> 2;
    default -> 0;
};

Benefits

No break

Cleaner syntax

Java 15
Text Blocks

Multi-line strings.

String json = """
{
   "name": "Java"
}
""";

Useful for:

SQL

JSON

HTML

Java 16
Records (Very Important)

Used for immutable data classes.

Instead of:

class User {
   private final String name;
   private final int age;
}

Use:

record User(String name, int age) {}

Automatically generates

constructor

getters

equals

hashCode

toString

Java 17 (LTS)

Very widely used in enterprise projects.

Sealed Classes

Control which classes can extend a class.

public sealed class Shape
    permits Circle, Rectangle {
}

Only allowed subclasses:

Circle

Rectangle

Java 19
Virtual Threads (Preview) – Project Loom

Lightweight threads.

Traditional threads = expensive
Virtual threads = extremely cheap

Thread.startVirtualThread(() -> {
    System.out.println("Hello");
});

Benefits

Massive scalability

Millions of threads possible

Java 21 (Latest LTS)

This is the most important modern Java version.

1. Virtual Threads (Final)
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    executor.submit(() -> {
        System.out.println("Task running");
    });
}

Benefits

High concurrency

Simpler async programming

2. Pattern Matching for Switch
switch(obj) {
    case Integer i -> System.out.println(i);
    case String s -> System.out.println(s);
    default -> System.out.println("Unknown");
}
3. Record Patterns

Destructure records.

record Point(int x, int y) {}

if (obj instanceof Point(int x, int y)) {
    System.out.println(x + "," + y);
}
4. String Templates (Preview)
String name = "Java";

String msg = STR."Hello \{name}";
Most Important Versions for Interviews

Focus strongly on these:

Version	Why Important
Java 8	Streams, Lambda
Java 11	LTS, String APIs
Java 17	Records, Sealed Classes
Java 21	Virtual Threads

