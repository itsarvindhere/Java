# Java Roadmap

Target: Java 25 (LTS). Everything here also works on Java 21 unless it is marked.

Markers:
- `[22]`, `[24]`, `[25]`: the feature is final only from that release onwards
- `[preview]`: preview or incubator feature in JDK 25; needs `--enable-preview` and may change

## How this repo works

- Each section below maps to a folder in this repo.
- Notes inside a folder are numbered `001.`, `002.`, ... in the order listed.
- Practice code for a folder goes in a `practice/` subfolder inside it.
- Tick a box only when you have written the note AND can explain the topic without looking.
- When a new JDK ships (every March and September), add an entry to `02-modern-java/024` and update any note it affects.

---

## 01-java-fundamentals

A quick pass through the basics. The aim is the pitfalls and the exact rules, not syntax you already use every day.

### 1. Setup and tooling
- [ ] 001. JDK vs JRE vs JVM; how `javac` and `java` work; launching single-file and multi-file source programs `[22]`
- [ ] 002. JDK distributions (Temurin, Oracle, Corretto), SDKMAN, `JAVA_HOME`, switching versions
- [ ] 003. Packages, imports, classpath vs module path, naming conventions
- [ ] 004. Using `jshell` for quick experiments

### 2. Language core and pitfalls
- [ ] 005. Primitive types, ranges, overflow, implicit vs explicit casting, floating-point precision
- [ ] 006. Wrapper classes, autoboxing, `Integer` cache pitfalls, `NullPointerException` from unboxing
- [ ] 007. Operators, precedence, integer division, `==` vs `equals`
- [ ] 008. Loops, labeled `break`/`continue` (switch expressions are covered in 02)
- [ ] 009. Arrays: declaration, multi-dimensional, `Arrays` utility class
- [ ] 010. Methods: pass-by-value (even for references), varargs, overload resolution rules

### 3. Strings and text
- [ ] 011. `String` immutability, string pool, `intern()`, compact strings
- [ ] 012. `StringBuilder` vs `StringBuffer`; when concatenation is fine (invokedynamic since Java 9)
- [ ] 013. Common methods, `String.format`, `formatted`, text blocks
- [ ] 014. Regex: `Pattern`, `Matcher`, groups, common mistakes
- [ ] 015. Character encoding: UTF-8, `Charset`, bytes vs chars, UTF-8 as the default since Java 18

### 4. Object-oriented programming
- [ ] 016. Classes, objects, constructors, `this`, initialization order (language rules)
- [ ] 017. Access modifiers, encapsulation, getters/setters vs immutability
- [ ] 018. `static`, `final`, static nested classes, initializer blocks
- [ ] 019. Inheritance, `super`, overriding, `@Override`, covariant return types
- [ ] 020. Polymorphism, dynamic dispatch, upcasting and downcasting
- [ ] 021. Abstract classes vs interfaces; default, static and private interface methods
- [ ] 022. Inner, local and anonymous classes
- [ ] 023. `Object` class: `equals`, `hashCode`, `toString`, `clone`, and the contracts between them
- [ ] 024. Composition over inheritance
- [ ] 025. Enums: fields, methods, abstract methods, `EnumMap`, `EnumSet`

### 5. Exceptions
- [ ] 026. Exception hierarchy: `Throwable`, `Error`, checked vs unchecked
- [ ] 027. `try`/`catch`/`finally`, multi-catch, try-with-resources, `AutoCloseable`
- [ ] 028. Custom exceptions, exception chaining, suppressed exceptions
- [ ] 029. Best practices: what to catch, what to log, what to rethrow
- [ ] 030. Assertions and defensive checks (`Objects.requireNonNull`, `Objects.checkIndex`)

### 6. Generics
- [ ] 031. Generic classes, methods, interfaces
- [ ] 032. Bounded types, wildcards, PECS (producer extends, consumer super)
- [ ] 033. Type erasure and its consequences
- [ ] 034. Generic pitfalls: arrays, raw types, heap pollution, `@SafeVarargs`

### 7. Core APIs
- [ ] 035. `java.time`: `LocalDate`, `Instant`, `ZonedDateTime`, `Duration`, `Clock`, formatting
- [ ] 036. `Optional` done right (and where not to use it)
- [ ] 037. `Math`, `BigInteger`, `BigDecimal` (money), `Random`, `RandomGenerator` (17), `SecureRandom`
- [ ] 038. File I/O with `java.nio.file`: `Path`, `Files`, reading, writing, walking directories
- [ ] 039. Byte and char streams (`InputStream`, `Reader`), buffering; Java serialization as legacy and a security risk
- [ ] 040. `java.net.http.HttpClient`: sync, async, timeouts
- [ ] 041. Properties, environment variables, system properties, `Runtime`
- [ ] 042. Logging: `java.util.logging`, `System.Logger`, SLF4J + Logback

### 8. Reflection, annotations and proxies
- [ ] 043. Annotations: built-in, custom, retention, targets
- [ ] 044. Reflection API: classes, methods, fields, invoking, `setAccessible`, limits under the module system
- [ ] 045. Dynamic proxies: JDK `Proxy` vs class-based proxies (CGLIB, ByteBuddy)
- [ ] 046. How frameworks (Spring, Hibernate) rely on this; why `@Transactional` on a self-invoked method does nothing

**Practice (`01-java-fundamentals/practice`)**
- [ ] CLI expense tracker (classes, collections, `java.time`, file persistence), built with Maven and tested with JUnit
- [ ] Bank account model with custom exceptions and an immutable money type
- [ ] Mini dependency-injection container using reflection and annotations
- [ ] 30 small exercises (strings, arrays, recursion, OOP)

---

## 02-modern-java (Java 8 to 25)

### 1. Functional style
- [ ] 001. Lambdas and functional interfaces (`Function`, `Predicate`, `Supplier`, `Consumer`, `BiFunction`)
- [ ] 002. Method references (four kinds)
- [ ] 003. Streams API in depth: `map`, `filter`, `flatMap`, `reduce`, `collect`, laziness, short-circuiting
- [ ] 004. Primitive streams; `parallelStream` and when not to use it (internals in 04)
- [ ] 005. Stream Gatherers: `Stream.gather`, built-in gatherers, writing your own `[24]`

### 2. Language features
- [ ] 006. `var` (local variable type inference) and its limits
- [ ] 007. Switch expressions, arrow labels, `yield`
- [ ] 008. Records: compact constructors, as DTOs and value objects, limits
- [ ] 009. Sealed classes and interfaces
- [ ] 010. Pattern matching for `instanceof` and `switch`, guards (`when`), exhaustiveness
- [ ] 011. Record patterns and nested deconstruction
- [ ] 012. Unnamed variables and patterns (`_`) `[22]`
- [ ] 013. Flexible constructor bodies (statements before `super(...)`) `[25]`
- [ ] 014. Compact source files, instance `main` methods, `java.lang.IO` `[25]`
- [ ] 015. Module import declarations (`import module java.base;`) `[25]`
- [ ] 016. Markdown documentation comments (`///`) `[23]`

### 3. Concurrency features (overview; depth in 04)
- [ ] 017. Virtual threads: what they are and the thread-per-request model (21)
- [ ] 018. Scoped values as a replacement for `ThreadLocal` `[25]`
- [ ] 019. Structured concurrency: `StructuredTaskScope` `[preview]`

### 4. Preview and incubating features
- [ ] 020. How preview features work: `--enable-preview`, `--release`, enabling them in Maven
- [ ] 021. Stable values and primitive types in patterns `[preview]` (check their status in the latest JDK)
- [ ] 022. Foreign Function & Memory API (awareness; replaces JNI) `[22]`

### 5. Release history
- [ ] 023. What changed between LTS releases: 8 -> 11 -> 17 -> 21 -> 25
- [ ] 024. Release tracker: non-LTS releases after 25 (add an entry for each new release)

**Practice (`02-modern-java/practice`)**
- [ ] Expression evaluator using sealed interfaces, records and pattern matching (no Visitor)
- [ ] Rewrite the 01 expense tracker using records, streams, gatherers and switch patterns

---

## 03-collections

- [ ] 001. Collections framework overview and hierarchy
- [ ] 002. `ArrayList` vs `LinkedList`, growth and complexity
- [ ] 003. `HashMap` internals: buckets, treeification, resizing, load factor; what bad `hashCode` and mutable keys do
- [ ] 004. `HashSet`, `LinkedHashMap` (access order, LRU cache), `TreeMap`, `TreeSet`, `NavigableMap`
- [ ] 005. `Queue`, `Deque`, `PriorityQueue`, `ArrayDeque`
- [ ] 006. Sequenced collections: `SequencedCollection`, `SequencedMap`, `reversed()` (21)
- [ ] 007. Specialised maps: `IdentityHashMap`, `WeakHashMap`, and when they matter
- [ ] 008. Immutable collections: `List.of`, `Map.of`, `Collections.unmodifiable*`, `Stream.toList()`; null handling
- [ ] 009. `Comparable` vs `Comparator`; comparator chaining; sorting stability
- [ ] 010. Iterators, fail-fast vs fail-safe, `ConcurrentModificationException`
- [ ] 011. `Collectors` deep dive: `groupingBy` with downstream collectors, `partitioningBy`, `toMap` merge pitfalls, `teeing`
- [ ] 012. Time complexity cheat sheet for every collection
- [ ] 013. Choosing the right collection (decision guide)

**Practice (`03-collections/practice`)**
- [ ] Implement an LRU cache two ways: with `LinkedHashMap`, then from scratch
- [ ] Implement a simplified `HashMap` with resizing and compare it to the JDK version

---

## 04-multithreading

Notes 001 to 026 already exist. Revisit them from the beginning, then continue from 027.
Before writing each new note, check whether the old notes already cover it. If they do, update the old note instead and renumber the rest.

- [ ] 027. Executors and thread pools: types, sizing, rejection policies, shutdown
- [ ] 028. `CompletableFuture`: composition, combining, error handling, custom executors
- [ ] 029. Concurrent collections: `ConcurrentHashMap` internals, `CopyOnWriteArrayList`, `BlockingQueue` implementations
- [ ] 030. Synchronizers: `Semaphore`, `CountDownLatch`, `CyclicBarrier`, `Phaser`, `Exchanger`
- [ ] 031. `ThreadLocal`, inheritance, and leaks in thread pools
- [ ] 032. Java Memory Model: happens-before, `volatile`, safe publication, `final` field semantics
- [ ] 033. Atomics and CAS: `AtomicInteger`, `LongAdder`, `VarHandle`
- [ ] 034. ForkJoin framework, work stealing, parallel streams in depth
- [ ] 035. Virtual threads deep dive: carrier threads, pinning (no longer caused by `synchronized` since 24), when not to use them, pooling anti-patterns
- [ ] 036. Structured concurrency and scoped values in practice `[preview]` / `[25]`
- [ ] 037. Reading thread dumps; diagnosing deadlocks and thread starvation (`jstack`, `jcmd Thread.dump_to_file`)
- [ ] 038. Testing concurrent code (see also 07-006)

**Practice (`04-multithreading/practice`)**
- [ ] Concurrent web crawler using virtual threads, `HttpClient` and structured concurrency
- [ ] In-memory key-value store with TTL expiry, tested for thread safety
- [ ] Rate limiter (token bucket) that is safe under contention
- [ ] Write a deliberate deadlock, then find it from a thread dump

---

## 05-jvm-internals

- [ ] 001. JVM architecture: class loader, runtime data areas, execution engine
- [ ] 002. Bytecode and `javap`
- [ ] 003. Class loading, linking, initialization; class loader hierarchy
- [ ] 004. Heap, stack, metaspace; object layout and compact object headers `[25]`; escape analysis
- [ ] 005. JIT compilation: C1, C2, tiered compilation, warm-up
- [ ] 006. Garbage collection: generations, G1 (default), generational ZGC, Shenandoah (generational mode in 25), Parallel, Serial; choosing a collector
- [ ] 007. GC logs (`-Xlog:gc*`) and tuning basics; common JVM flags
- [ ] 008. The JVM in containers: container awareness, `-XX:MaxRAMPercentage`, CPU limits, why a fixed `-Xmx` is risky
- [ ] 009. Memory leaks, `OutOfMemoryError` types, heap dumps (VisualVM, Eclipse MAT)
- [ ] 010. Profiling with Java Flight Recorder and JDK Mission Control, `jcmd`, `jstack`, `jmap`
- [ ] 011. JMH and the pitfalls of micro-benchmarking
- [ ] 012. Startup time: CDS, the AOT cache (Project Leyden) `[24]`/`[25]`, GraalVM native image (awareness)
- [ ] 013. Modules (JPMS), `jlink`, `jpackage` (awareness)

**Practice (`05-jvm-internals/practice`)**
- [ ] Write a deliberate memory leak, capture a heap dump, and find the leak in Eclipse MAT
- [ ] Profile a slow program with JFR and fix the hotspot
- [ ] Benchmark two implementations with JMH and explain the result

---

## 06-maven-gradle

- [ ] 001. Maven: project layout, `pom.xml`, coordinates
- [ ] 002. Dependency scopes, transitive dependencies, exclusions
- [ ] 003. Dependency management and BOMs
- [ ] 004. Build lifecycle and phases, plugin goals
- [ ] 005. Compiler settings: `maven.compiler.release`, toolchains, enabling preview features
- [ ] 006. Surefire and Failsafe; test reports
- [ ] 007. Profiles, properties, resource filtering
- [ ] 008. Multi-module builds, parent POMs
- [ ] 009. Debugging dependency problems (`dependency:tree`, `help:effective-pom`, `versions` plugin)
- [ ] 010. Repositories, `settings.xml`, publishing to Nexus/Artifactory
- [ ] 011. Maven Wrapper and reproducible builds
- [ ] 012. Gradle basics: Kotlin DSL, tasks, version catalogs; Maven-to-Gradle mapping

---

## 07-junit-mockito

- [ ] 001. JUnit Jupiter: lifecycle, assertions, `@Nested`, `@ParameterizedTest`, extensions
- [ ] 002. AssertJ fluent assertions
- [ ] 003. Mockito: mocks, stubs, spies, verification, `ArgumentCaptor`; configuring the Mockito agent on JDK 21+
- [ ] 004. Test design: arrange-act-assert, test data builders, avoiding over-mocking
- [ ] 005. Integration testing with Testcontainers (real database in tests)
- [ ] 006. Testing concurrency and time (`Clock` injection, Awaitility)
- [ ] 007. Code coverage with JaCoCo; mutation testing with PIT

---

## 08-design-patterns-solid

- [ ] 001. SOLID principles with Java examples
- [ ] 002. Creational: builder, factory, singleton (and its problems)
- [ ] 003. Structural: adapter, decorator, facade, proxy
- [ ] 004. Behavioural: strategy, observer, template method, command
- [ ] 005. Patterns in modern Java: strategy as a lambda, sealed types and pattern matching instead of Visitor, records as value objects
- [ ] 006. Clean code: naming, small methods, immutability, avoiding nulls
- [ ] 007. Refactoring and code smells
- [ ] 008. Domain modelling basics (value objects, entities, aggregates)

---

## 09-data-access-json

The bridge to Spring Boot. Spring Data and `@Transactional` make much more sense once you have done this by hand.

- [ ] 001. JDBC basics: `DriverManager`, `Connection`, `PreparedStatement`, `ResultSet`, SQL injection
- [ ] 002. Transactions: commit, rollback, isolation levels, and the anomalies each one prevents
- [ ] 003. Connection pooling with HikariCP
- [ ] 004. SQL refresher for Java developers: joins, indexes, the N+1 query problem, pagination
- [ ] 005. JSON with Jackson: `ObjectMapper`, annotations, records, `java.time` support, common errors

---

## Capstone

- [ ] A small REST-style service in plain Java: JDK `HttpServer` or a minimal library, JDBC with HikariCP, Jackson, virtual threads, JUnit + Testcontainers, and a Maven multi-module build
- [ ] Rebuild the same service in Spring Boot as the first project in the `spring-boot-notes` repo, and write a note comparing the two

---

## Suggested order

Weeks assume a full-time study pace. Alongside a job, expect roughly 12 to 14 weeks.

1. 06-maven-gradle (001 to 006) and 07-junit-mockito (001 to 003) first, so every practice project has a build and tests from day one (week 1)
2. 01-java-fundamentals (weeks 1 to 2)
3. 02-modern-java and 03-collections (weeks 3 to 4)
4. Rest of 06 and 07 alongside the above (weeks 3 to 4)
5. 04-multithreading (weeks 5 to 7)
6. 05-jvm-internals (weeks 7 to 8)
7. 09-data-access-json (week 9)
8. Capstone (week 10)
9. 08-design-patterns-solid (ongoing; write a note whenever a pattern comes up in practice)

After this, move on to the `spring-boot-notes` repo.
