
| **Topic**                                                    | **Before Java 8**                                                                         | **With Java 8**                                                                                                                                         |
| ------------------------------------------------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Introduction / Compilation / Runtime**                     | JVM, JRE, JDK unchanged in core. PermGen space used for class metadata.                   | **PermGen removed**, replaced by **Metaspace** (native memory). New flags: `-XX:MetaspaceSize`, `-XX:MaxMetaspaceSize`.                                 |
| **Hello World / Syntax**                                     | Classic structure with `main`, no shorthand for behavior.                                 | Same syntax; **new option to use lambdas/method references** inside methods.                                                                            |
| **Naming Conventions**                                       | Same (camelCase, PascalCase, etc.).                                                       | No change, except `_` reserved as identifier (warning in 8, error in 9).                                                                                |
| **Data Types & Variables**                                   | Primitive/wrapper types. No functional interfaces bundled.                                | Added **`Optional<T>`** type to model missing values safely. New functional interfaces in `java.util.function` package (`Predicate`, `Consumer`, etc.). |
| **Operators & Expressions**                                  | Only traditional operators.                                                               | No new operators, but **lambdas** allow treating methods/functions like first-class values.                                                             |
| **Type Casting / Promotion**                                 | Manual casting rules only.                                                                | No new casting rules; **Streams/Optionals** introduce functional conversions (`map`, `flatMap`) instead of manual casts in some cases.                  |
| **Control Flow (if, switch)**                                | Standard forms only.                                                                      | No change (string switch was Java 7). Lambdas often replace switch/case boilerplate in practice.                                                        |
| **Loops**                                                    | `for`, `while`, `do-while` plus `foreach` since Java 5.                                   | Same loops, but **`Iterable.forEach()` default method** introduced — now idiomatic to loop with lambdas.                                                |
| **Break / Continue**                                         | Same as always.                                                                           | No change, but inside lambdas you cannot use `break`/`continue` directly (must restructure via stream ops).                                             |
| **Classes & Objects**                                        | Plain classes. Interfaces had no method bodies.                                           | **Interfaces can now have `default` and `static` methods**.                                                                                             |
| **Constructors & Init blocks**                               | Same.                                                                                     | No change.                                                                                                                                              |
| **Method Overloading/Overriding**                            | Same as OOP rules.                                                                        | No syntax change, but lambdas make **passing behavior as argument** an alternative to overloading in some APIs.                                         |
| **Encapsulation / Inheritance / Polymorphism / Abstraction** | Classic OOP only.                                                                         | Same, but **functional style** (via lambdas + streams) complements OOP.                                                                                 |
| **Static / Instance Members**                                | Standard fields/methods.                                                                  | Interfaces may define **static methods**.                                                                                                               |
| **`this` / `super`**                                         | Standard semantics.                                                                       | Same, but lambdas capture enclosing `this` (unlike inner classes, which have their own `this`).                                                         |
| **Interfaces & Abstract Classes**                            | Interfaces only had constants + abstract methods. Abstract classes allowed method bodies. | **Default & static methods in interfaces** reduce need for abstract classes. **`@FunctionalInterface` annotation** enforces single-method contracts.    |
| **Nested & Anonymous Classes**                               | Anonymous classes often used for callbacks (e.g., `Runnable`).                            | **Lambdas replace most anonymous classes** for single-method interfaces. Method references also help.                                                   |
| **Exception Handling (checked/unchecked)**                   | Classic try-catch-finally.                                                                | Same rules.                                                                                                                                             |
| **try-catch-finally**                                        | Manual resource cleanup.                                                                  | Try-with-resources was Java 7, not 8. In Java 8: no new syntax.                                                                                         |
| **throw / throws**                                           | Same rules.                                                                               | Same rules.                                                                                                                                             |
| **Custom Exceptions**                                        | Subclass `Exception` or `RuntimeException`.                                               | Same.                                                                                                                                                   |
| **Best Practices**                                           | Null checks, defensive coding.                                                            | Use **`Optional`** instead of nulls, **streams** for declarative error-tolerant pipelines, **CompletableFuture.exceptionally/handle** for async errors. |



| **Area**              | **Java 8 (Before)**                                                                          | **Need for Change**                                    | **Java 11 (After)**                                                                                        | **Developer Impact / Example**                                                                                     |
| --------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Type Inference**    | Explicit types everywhere. <br>`Map<String, List<Integer>> map = new HashMap<>();`           | Verbose, repetitive declarations.                      | `var` (Java 10) for local vars and in lambdas.                                                             | Cleaner but still strongly typed. <br>`var map = new HashMap<String, List<Integer>>();`                            |
| **Interfaces**        | Could only have `default` and `static` methods.                                              | Code duplication inside interfaces.                    | Private methods in interfaces (Java 9).                                                                    | Improves interface design. <br>`private void log(String msg) { … }` used inside `default`.                         |
| **Strings**           | Only `trim()`. <br>No direct multiline handling.                                             | `trim()` is ASCII-only, limited utility.               | New methods: `isBlank()`, `strip()`, `stripLeading()`, `stripTrailing()`, `repeat()`, `lines()` (Java 11). | Unicode-aware whitespace, easier text ops. <br>`"   ".isBlank(); // true`                                          |
| **Collections**       | Verbose creation: <br>`List<String> list = new ArrayList<>(); list.add("a"); list.add("b");` | Too much boilerplate for small, immutable collections. | Factory methods (Java 9): `List.of()`, `Set.of()`, `Map.of()`.                                             | Immutable by default. <br>`List<String> list = List.of("a", "b");`                                                 |
| **Optional**          | Only `isPresent()`, `get()`, `ifPresent()`.                                                  | Hard to chain logic, forced manual handling.           | New methods: `ifPresentOrElse`, `or`, `stream` (Java 9/10).                                                | Cleaner functional-style code. <br>`opt.ifPresentOrElse(System.out::println, () -> log("empty"));`                 |
| **Streams**           | Limited operations, e.g., `filter`, `map`, etc.                                              | No easy short-circuiting or controlled iteration.      | `takeWhile`, `dropWhile`, enhanced `iterate` (Java 9).                                                     | More expressive stream processing. <br>`list.stream().takeWhile(x -> x < 10);`                                     |
| **Files API**         | `Files.readAllLines`, `BufferedReader`.                                                      | Verbose for simple text I/O.                           | `Files.readString()`, `Files.writeString()` (Java 11).                                                     | Fewer lines: <br>`String content = Files.readString(path);`                                                        |
| **Networking**        | `HttpURLConnection`, Apache HttpClient dependency.                                           | Very clunky, no HTTP/2, async hard.                    | Standardized `HttpClient` (Java 11).                                                                       | Async with `CompletableFuture`, supports HTTP/2. <br>`client.sendAsync(request, BodyHandlers.ofString())…`         |
| **Process Handling**  | `Process` API weak, `Runtime.exec()` hacky.                                                  | No control over child processes.                       | `ProcessHandle` API (Java 9).                                                                              | Monitor, destroy, query processes. <br>`ProcessHandle.current().pid();`                                            |
| **Scripting**         | Nashorn JS engine bundled.                                                                   | Outdated JS engine, security + perf issues.            | Nashorn deprecated, removed in later versions.                                                             | Use **GraalVM** for polyglot.                                                                                      |
| **Packaging**         | Monolithic JRE, no customization.                                                            | Too heavy for microservices / containers.              | `jlink` (Java 9) → custom runtime images.                                                                  | Ship smaller apps. Example: `jlink --module-path $JAVA_HOME/jmods --add-modules java.base,java.sql --output myJRE` |
| **GC**                | Default: Parallel GC.                                                                        | High throughput, but not low-latency friendly.         | Default: G1 GC (Java 9+). <br>ZGC introduced (Java 11).                                                    | Better latency for server workloads.                                                                               |
| **Strings in Memory** | `char[]` backing (2 bytes/char).                                                             | Memory waste for Latin-1 text.                         | Compact Strings (Java 9): `byte[]` with encoding flag.                                                     | Automatic optimization, no code change.                                                                            |
| **Modules**           | Everything in one big JDK.                                                                   | Hard to scale, insecure reflection access.             | Module System (Project Jigsaw, Java 9).                                                                    | Optional, but improves encapsulation: <br>`module my.app { requires java.sql; }`                                   |
| **Removed APIs**      | Java EE & CORBA (`javax.xml.bind`, `javax.transaction`, etc.), JavaFX, Web Start.            | Legacy, rarely used, better handled by external libs.  | Removed in Java 11.                                                                                        | Must add dependencies (Jakarta EE, OpenJFX) if still needed.                                                       |
| **Security**          | TLS 1.2 default.                                                                             | TLS 1.3 adoption in industry.                          | TLS 1.3 supported in Java 11.                                                                              | More secure defaults.                                                                                              |


## Collections 

| **Aspect**                   | **Java 8 (What was available)**                                                                         | **Need for Change (Why)**                                                                                           | **Java 9–11 (What changed & implemented)**                                                                                            | **Developer Impact / Example**                                                                                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Collection Creation**      | - `new ArrayList<>()` / `new HashSet<>()` <br> - `Arrays.asList()` (fixed-size, but not immutable)      | Verbose and confusing immutability semantics. Developers wanted a **concise, immutable way** to create collections. | **Java 9**: Factory methods <br> - `List.of(...)`, `Set.of(...)`, `Map.of(...)`, `Map.ofEntries(...)`.                                | `java<br>List<String> list = List.of("a","b","c");<br>Map<String,Integer> map = Map.of("a",1,"b",2);<br>` <br> → Immutable, concise, no accidental modification. |
| **Mutability Control**       | `Collections.unmodifiableList(list)` created unmodifiable views but still backed by mutable collection. | Error-prone (modifying the backing list affected the “immutable” view).                                             | **Java 9**: Factory methods return **truly immutable collections**.                                                                   | Safer immutability with no surprises.                                                                                                                            |
| **Stream Enhancements**      | Java 8 introduced Streams, but only unbounded `iterate()` was supported.                                | Needed **better bounded iteration** and **more expressive filtering**.                                              | **Java 9**: <br> - `takeWhile(predicate)` <br> - `dropWhile(predicate)` <br> - `iterate(seed, hasNext, next)`                         | `java<br>Stream.iterate(1, n -> n <= 10, n -> n+1)<br>      .forEach(System.out::println);<br>`                                                                  |
| **Optional Integration**     | `Optional` introduced in Java 8, but awkward with streams (`optional.isPresent()` + manual handling).   | Developers wanted **smoother interop with streams** and more expressive methods.                                    | **Java 9**: <br> - `Optional.stream()` <br> - `ifPresentOrElse()` <br> - `or(Supplier)`                                               | `java<br>Optional.of("data").stream()<br>       .forEach(System.out::println);<br>`                                                                              |
| **Map Enhancements**         | Java 8 added `computeIfAbsent`, `merge`, etc. but construction was still verbose.                       | Needed a **compact immutable map** builder and better readability.                                                  | **Java 9**: <br> - `Map.of(...)`, `Map.ofEntries(...)` <br> - `Map.entry(k, v)`                                                       | `java<br>Map<String,Integer> map = Map.ofEntries(<br>    Map.entry("x",1), Map.entry("y",2));<br>`                                                               |
| **Collectors Enhancements**  | Only had `Collectors.toList()`, `toSet()`, `toMap()` (all mutable).                                     | Developers wanted immutable collectors directly from Streams.                                                       | **Java 11**: <br> - `Collectors.toUnmodifiableList()` <br> - `Collectors.toUnmodifiableSet()` <br> - `Collectors.toUnmodifiableMap()` | `java<br>List<String> l = Stream.of("a","b")<br>    .collect(Collectors.toUnmodifiableList());<br>`                                                              |
| **Null Handling**            | Collections (like `ArrayList`) allowed `null` values. <br> `Arrays.asList(null)` didn’t throw error.    | Nulls in immutable collections cause ambiguity & runtime issues.                                                    | **Java 9**: `List.of`, `Set.of`, `Map.of` **forbid nulls**.                                                                           | `java<br>List.of(null); // NPE<br>` → Safer, predictable collections.                                                                                            |
| **Performance / Memory**     | Immutable collections via `Collections.unmodifiableList()` were **backed wrappers** with overhead.      | Needed **compact, memory-optimized** representations.                                                               | **Java 9**: Factory-created immutable collections use **special compact storage**.                                                    | Optimized for small collections → better in microservices/low-memory deployments.                                                                                |
| **Code Conciseness (`var`)** | Must repeat type: <br>`List<String> list = new ArrayList<>();`                                          | Boilerplate-heavy.                                                                                                  | **Java 10**: Local-variable type inference (`var`).                                                                                   | `java<br>var list = List.of("a","b","c");<br>` <br> → Less verbose, especially with generics.                                                                    |


## String
| **Aspect**              | **Java 8**                     | **Java 11**                                                    |
| ----------------------- | ------------------------------ | -------------------------------------------------------------- |
| **Internal storage**    | `char[]`                       | `byte[]` (Compact String)                                      |
| **Whitespace handling** | Only `trim()` (ASCII)          | `strip()`, `stripLeading()`, `stripTrailing()` (Unicode-aware) |
| **Empty check**         | `isEmpty()`                    | `isBlank()` (includes whitespace-only)                         |
| **Repetition**          | Manual loop or `StringBuilder` | `repeat(int)`                                                  |
| **Line splitting**      | `split("\n")` manually         | `lines()` returns Stream                                       |
| ==**Transformation**==      | ==No direct method==               | ==`transform(Function)`==                                          |
| ==**Indentation**==         | ==Manual string manipulation==     | ==`indent(int)` built-in==                                         |
| ==**Memory efficiency**==   | ==Higher (2 bytes per char)==      | ==Compact and efficient (1 or 2 bytes)==                           |



## Collections
Excellent — you’re now asking for the **complete architecture** of the **Java Collections Framework (JCF)**, one of the most powerful parts of the Java platform.

Let’s build this in a **layered, structured, and visual** way so you fully understand:
how the framework is designed, how each interface connects, and what implementations belong where.

---

# 🧩 Java Collections Framework (JCF) — Complete Architecture

## 🏗️ 2️⃣ High-Level Structure

```
        Iterable (root)
            │
         Collection
     ┌──────┼─────────┐
     │      │         │
   List    Set      Queue
     │      │         │
     │      │         └─────── Deque
     │      │
     │      └──────── SortedSet → NavigableSet
     │
     └────── Map (not a true child but part of JCF)
            │
            └──── SortedMap → NavigableMap
```

---

## 🧩 3️⃣ Core Interfaces (by purpose)

| Category         | Interface           | Description                                         |
| ---------------- | ------------------- | --------------------------------------------------- |
| **Root**         | `Iterable<T>`       | Base interface for enhanced for-loops (`for-each`)  |
| **Main**         | `Collection<T>`     | Base interface for all collections (except maps)    |
| **List**         | `List<T>`           | Ordered, indexed, allows duplicates                 |
| **Set**          | `Set<T>`            | Unique elements, no duplicates                      |
| **SortedSet**    | `SortedSet<T>`      | Set with natural or custom order                    |
| **NavigableSet** | `NavigableSet<T>`   | Extended operations for range views, floor, ceiling |
| **Queue**        | `Queue<T>`          | FIFO or priority-based access                       |
| **Deque**        | `Deque<T>`          | Double-ended queue (insert/remove both ends)        |
| **Map**          | `Map<K,V>`          | Key-value pairs, no duplicate keys                  |
| **SortedMap**    | `SortedMap<K,V>`    | Map with natural order of keys                      |
| **NavigableMap** | `NavigableMap<K,V>` | Extended SortedMap with floor/ceiling/range view    |

---

## ⚙️ 4️⃣ Abstract Classes (Skeletons)

| Abstract Class           | Implements   | Purpose                               |
| ------------------------ | ------------ | ------------------------------------- |
| `AbstractCollection`     | `Collection` | Base for most collections             |
| `AbstractList`           | `List`       | Partial implementation of List        |
| `AbstractSequentialList` | `List`       | Base for linked lists                 |
| `AbstractSet`            | `Set`        | Simplifies custom Set implementations |
| `AbstractQueue`          | `Queue`      | Base for queue implementations        |
| `AbstractMap`            | `Map`        | Base for map implementations          |

---

## 🧱 5️⃣ Concrete Implementations

### 🔹 **List Implementations**

| Class        | Backing Structure  | Thread Safety        | Key Points                                |
| ------------ | ------------------ | -------------------- | ----------------------------------------- |
| `ArrayList`  | Dynamic array      | ❌ No                 | Fast random access, slow inserts/removals |
| `LinkedList` | Doubly linked list | ❌ No                 | Fast inserts/removals, slower access      |
| `Vector`     | Dynamic array      | ✅ Yes (synchronized) | Legacy, replaced by `ArrayList`           |
| `Stack`      | Extends `Vector`   | ✅ Yes                | Legacy, replaced by `Deque`               |

---

### 🔹 **Set Implementations**

| Class                 | Backing Structure        | Order           | Thread Safety |
| --------------------- | ------------------------ | --------------- | ------------- |
| `HashSet`             | Hash table               | Unordered       | ❌             |
| `LinkedHashSet`       | Hash table + linked list | Insertion order | ❌             |
| `TreeSet`             | Red-Black tree           | Sorted          | ❌             |
| `CopyOnWriteArraySet` | Copy-on-write array      | Insertion order | ✅             |
| `EnumSet`             | Bit-vector               | Natural order   | ❌             |

---

### 🔹 **Queue / Deque Implementations**

| Class                   | Type          | Thread Safety | Description                        |
| ----------------------- | ------------- | ------------- | ---------------------------------- |
| `PriorityQueue`         | Queue         | ❌             | Elements ordered by priority       |
| `ArrayDeque`            | Deque         | ❌             | Efficient double-ended queue       |
| `LinkedList`            | Deque         | ❌             | Implements both `List` and `Deque` |
| `ConcurrentLinkedQueue` | Queue         | ✅             | Lock-free queue for concurrency    |
| `LinkedBlockingQueue`   | BlockingQueue | ✅             | Supports producer-consumer model   |
| `ArrayBlockingQueue`    | BlockingQueue | ✅             | Fixed capacity blocking queue      |

---

### 🔹 **Map Implementations**

| Class               | Backing Structure                   | Order                 | Thread Safety |
| ------------------- | ----------------------------------- | --------------------- | ------------- |
| `HashMap`           | Hash table                          | Unordered             | ❌             |
| `LinkedHashMap`     | Hash table + linked list            | Insertion order       | ❌             |
| `TreeMap`           | Red-Black tree                      | Sorted                | ❌             |
| `Hashtable`         | Hash table                          | Unordered             | ✅ (legacy)    |
| `ConcurrentHashMap` | Hash table (segmented)              | Unordered             | ✅             |
| `WeakHashMap`       | Hash table (weak keys)              | Unordered             | ❌             |
| `IdentityHashMap`   | Hash table (== instead of equals()) | Unordered             | ❌             |
| `EnumMap`           | Array-based                         | Natural order of enum | ❌             |

---

## 🧩 6️⃣ Special Purpose Collections

| Class                                            | Purpose                                              |
| ------------------------------------------------ | ---------------------------------------------------- |
| `CopyOnWriteArrayList`, `CopyOnWriteArraySet`    | Safe iteration under concurrency                     |
| `ConcurrentSkipListMap`, `ConcurrentSkipListSet` | Sorted concurrent maps/sets                          |
| `SynchronizedList`, `SynchronizedMap`            | Wrappers via `Collections.synchronizedX()`           |
| `UnmodifiableList`, etc.                         | Read-only wrappers via `Collections.unmodifiableX()` |

---

## 🧮 7️⃣ Utility Classes

| Class         | Description                                                                    |
| ------------- | ------------------------------------------------------------------------------ |
| `Collections` | Factory & utility methods (sorting, unmodifiable, synchronized wrappers, etc.) |
| `Arrays`      | Utility methods for array-based collections                                    |
| `Objects`     | Null-safe utilities for equals, hash, etc.                                     |

---

## 🔐 8️⃣ Thread-safe Collections Summary

| Type  | Modern Class                             | Legacy Equivalent |
| ----- | ---------------------------------------- | ----------------- |
| List  | `CopyOnWriteArrayList`                   | `Vector`          |
| Set   | `CopyOnWriteArraySet`                    | —                 |
| Map   | `ConcurrentHashMap`                      | `Hashtable`       |
| Queue | `ConcurrentLinkedQueue`, `BlockingQueue` | —                 |

---

## 📘 9️⃣ Visualization (Concept Map)

```
Iterable
 └── Collection
      ├── List
      │    ├── ArrayList
      │    ├── LinkedList
      │    ├── Vector → Stack
      │    └── CopyOnWriteArrayList
      │
      ├── Set
      │    ├── HashSet → LinkedHashSet
      │    ├── TreeSet
      │    └── CopyOnWriteArraySet
      │
      └── Queue
           ├── PriorityQueue
           ├── ArrayDeque
           ├── ConcurrentLinkedQueue
           └── BlockingQueue → LinkedBlockingQueue
           
Map
 ├── HashMap → LinkedHashMap
 ├── TreeMap
 ├── WeakHashMap
 ├── IdentityHashMap
 ├── EnumMap
 ├── ConcurrentHashMap
 └── Hashtable (legacy)
```

