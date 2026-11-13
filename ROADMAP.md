# Java Roadmap

Target: Java 25 (LTS). Everything here also works on Java 21 unless marked.
Each section maps to a folder in this repo. Notes inside a folder are numbered `001.`, `002.`, ... in the order below.
Tick a box only when you have written the note AND can explain the topic without looking.

---

## 01-java-fundamentals

### 1. Getting started
- [ ] 001. JDK vs JRE vs JVM; how `javac` and `java` work
- [ ] 002. Installing JDKs (SDKMAN), `JAVA_HOME`, switching versions
- [ ] 003. First program, `main`, compiling and running from the terminal
- [ ] 004. Packages, imports, classpath, naming conventions
- [ ] 005. Using `jshell` for quick experiments

### 2. Language basics
- [ ] 006. Primitive types, ranges, overflow, implicit vs explicit casting
- [ ] 007. Wrapper classes, autoboxing, `Integer` cache pitfalls
- [ ] 008. Operators, precedence, integer division, `==` vs `equals`
- [ ] 009. Control flow: `if`, `switch`, loops, labeled `break`/`continue`
- [ ] 010. Arrays: declaration, multi-dimensional, `Arrays` utility class
- [ ] 011. Methods: parameters, pass-by-value (even for references), varargs, overloading
- [ ] 012. `var` (local variable type inference) and its limits

### 3. Strings and text
- [ ] 013. `String` immutability, string pool, `intern()`
- [ ] 014. `StringBuilder` vs `StringBuffer`, when concatenation is fine
- [ ] 015. Common methods, `String.format`, `formatted`, text blocks
- [ ] 016. Regex basics: `Pattern`, `Matcher`
- [ ] 017. Character encoding: UTF-8, `Charset`, bytes vs chars

### 4. Object-oriented programming
- [ ] 018. Classes, objects, constructors, `this`, initialization order
- [ ] 019. Access modifiers, encapsulation, getters/setters vs immutability
- [ ] 020. `static`, `final`, static nested classes, initializer blocks
- [ ] 021. Inheritance, `super`, method overriding, `@Override`
- [ ] 022. Polymorphism, dynamic dispatch, upcasting and downcasting
- [ ] 023. Abstract classes vs interfaces; default, static and private interface methods
- [ ] 024. Inner, local and anonymous classes
- [ ] 025. `Object` class: `equals`, `hashCode`, `toString`, `clone`, the contracts between them
- [ ] 026. Composition over inheritance
- [ ] 027. Enums: fields, methods, abstract methods, `EnumMap`, `EnumSet`

### 5. Exceptions
- [ ] 028. Exception hierarchy: `Throwable`, `Error`, checked vs unchecked
- [ ] 029. `try`/`catch`/`finally`, multi-catch, try-with-resources, `AutoCloseable`
- [ ] 030. Custom exceptions, exception chaining, suppressed exceptions
- [ ] 031. Best practices: what to catch, what to log, what to rethrow
- [ ] 032. Assertions and defensive checks (`Objects.requireNonNull`)

### 6. Generics
- [ ] 033. Generic classes, methods, interfaces
- [ ] 034. Bounded types, wildcards, PECS (producer extends, consumer super)
- [ ] 035. Type erasure and its consequences
- [ ] 036. Generic pitfalls: arrays, raw types, heap pollution

### 7. Core APIs
- [ ] 037. `java.time`: `LocalDate`, `Instant`, `ZonedDateTime`, `Duration`, formatting
- [ ] 038. `Optional` done right
- [ ] 039. `Math`, `BigInteger`, `BigDecimal` (money), `Random` and `SecureRandom`
- [ ] 040. File I/O with `java.nio.file`: `Path`, `Files`, reading and writing
- [ ] 041. Streams of bytes and chars (`InputStream`, `Reader`), buffering, serialization basics
- [ ] 042. `java.net.http.HttpClient`
- [ ] 043. Properties, environment variables, system properties, `Runtime`
- [ ] 044. Logging basics: `java.util.logging` vs SLF4J + Logback

### 8. Reflection and annotations
- [ ] 045. Annotations: built-in, custom, retention, targets
- [ ] 046. Reflection API: classes, methods, fields, invoking, limits
- [ ] 047. Why frameworks (Spring, Hibernate) rely on this

**Practice for this folder**
- [ ] CLI expense tracker (classes, collections, `java.time`, file persistence)
- [ ] Bank account model with custom exceptions and an immutable money type
- [ ] 30 small exercises (strings, arrays, recursion, OOP)

---

## 02-modern-java (Java 8 to 25)

- [ ] 001. Lambdas and functional interfaces (`Function`, `Predicate`, `Supplier`, `Consumer`, `BiFunction`)
- [ ] 002. Method references (four kinds)
- [ ] 003. Streams API in depth: `map`, `filter`, `flatMap`, `reduce`, `collect`, `Collectors`
- [ ] 004. Primitive streams, `parallelStream` and when not to use it
- [ ] 005. `var`, text blocks, enhanced `switch` expressions
- [ ] 006. Records: compact constructors, as DTOs, limits
- [ ] 007. Sealed classes and interfaces
- [ ] 008. Pattern matching: `instanceof`, `switch`, record patterns
- [ ] 009. Sequenced collections (Java 21)
- [ ] 010. Virtual threads (Java 21)
- [ ] 011. Scoped values, structured concurrency (preview in some releases, check your JDK)
- [ ] 012. Java 25 additions: module import declarations, flexible constructor bodies, compact source files and instance `main`
- [ ] 013. What changed between LTS releases: 8 -> 11 -> 17 -> 21 -> 25

---

## 03-collections-streams

- [ ] 001. Collections framework overview and hierarchy
- [ ] 002. `ArrayList` vs `LinkedList`, growth and complexity
- [ ] 003. `HashMap` internals: buckets, treeification, resizing, load factor
- [ ] 004. `HashSet`, `LinkedHashMap`, `TreeMap`, `TreeSet`
- [ ] 005. `Queue`, `Deque`, `PriorityQueue`, `ArrayDeque`
- [ ] 006. Immutable collections: `List.of`, `Map.of`, `Collections.unmodifiable*`
- [ ] 007. `Comparable` vs `Comparator`; sorting stability
- [ ] 008. Iterators, fail-fast vs fail-safe, `ConcurrentModificationException`
- [ ] 009. Time complexity cheat sheet for every collection
- [ ] 010. Choosing the right collection (decision guide)

---

## 04-multithreading

You already wrote 26 notes here; revisit from the beginning and add:
- [ ] Virtual threads, `ThreadLocal`, `Semaphore`, `Phaser`, `Exchanger`
- [ ] `ConcurrentHashMap` and other concurrent collections
- [ ] ForkJoin framework, parallel streams
- [ ] Java Memory Model (happens-before)
- [ ] Reading thread dumps; diagnosing deadlocks and thread starvation

---

## 05-jvm-internals

- [ ] 001. JVM architecture: class loader, runtime data areas, execution engine
- [ ] 002. Bytecode and `javap`
- [ ] 003. Class loading, initialization order, class loader hierarchy
- [ ] 004. Heap, stack, metaspace; escape analysis
- [ ] 005. JIT compilation: C1, C2, tiered compilation, warm-up
- [ ] 006. Garbage collection: generations, G1, ZGC, Shenandoah; choosing a collector
- [ ] 007. GC logs and tuning basics; common JVM flags
- [ ] 008. Memory leaks, `OutOfMemoryError` types, heap dumps (VisualVM, Eclipse MAT)
- [ ] 009. Profiling with Java Flight Recorder, `jcmd`, `jstack`, `jmap`
- [ ] 010. JMH and the pitfalls of micro-benchmarking
- [ ] 011. Modules (JPMS), `jlink`, `jpackage` (awareness)

---

## 06-maven-gradle

- [ ] 001. Maven: project layout, `pom.xml`, coordinates
- [ ] 002. Dependency scopes, transitive dependencies, exclusions
- [ ] 003. Dependency management and BOMs
- [ ] 004. Build lifecycle and phases, plugin goals
- [ ] 005. Surefire and Failsafe; test reports
- [ ] 006. Profiles, properties, resource filtering
- [ ] 007. Multi-module builds, parent POMs
- [ ] 008. Debugging dependency problems (`dependency:tree`, `help:effective-pom`)
- [ ] 009. Repositories, `settings.xml`, publishing to Nexus/Artifactory
- [ ] 010. Maven Wrapper and reproducible builds
- [ ] 011. Gradle basics: Kotlin DSL, tasks, version catalogs; Maven-to-Gradle mapping

---

## 07-junit-mockito

- [ ] 001. JUnit Jupiter: lifecycle, assertions, `@Nested`, `@ParameterizedTest`
- [ ] 002. AssertJ fluent assertions
- [ ] 003. Mockito: mocks, stubs, spies, verification, `ArgumentCaptor`
- [ ] 004. Test design: arrange-act-assert, test data builders, avoiding over-mocking
- [ ] 005. Code coverage with JaCoCo; mutation testing with PIT
- [ ] 006. Testing concurrency and time (`Clock` injection)

---

## 08-design-patterns-solid

- [ ] 001. SOLID principles with Java examples
- [ ] 002. Creational: builder, factory, singleton (and its problems)
- [ ] 003. Structural: adapter, decorator, facade, proxy
- [ ] 004. Behavioural: strategy, observer, template method, command
- [ ] 005. Clean code: naming, small methods, immutability, avoiding nulls
- [ ] 006. Refactoring and code smells
- [ ] 007. Domain modelling basics (value objects, entities)

---

## Suggested order

1. 01-java-fundamentals (weeks 1 to 3)
2. 02-modern-java and 03-collections-streams (weeks 3 to 5)
3. 06-maven-gradle in parallel with the above (weeks 3 to 4)
4. 07-junit-mockito (week 5, then keep writing tests from here on)
5. 04-multithreading (weeks 6 to 8)
6. 05-jvm-internals (weeks 8 to 9)
7. 08-design-patterns-solid (ongoing)

After this, move on to the `spring-boot-notes` repo.
