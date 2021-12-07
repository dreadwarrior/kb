---
layout: default
title: JVM
nav_order: 4
has_children: true
has_toc: false
---

# JVM
{: .no_toc }

Die **Java Virtual Machine** (abgekürzt _Java VM_ oder _JVM_) ist der Teil der 
Java-Laufzeitumgebung (Java Runtime Environment, JRE) für Java-Programme, der 
für die Ausführung des Java-Bytecodes verantwortlich ist. Hierbei wird im 
Normalfall jedes gestartete Java-Programm in seiner eigenen virtuellen Maschine 
(VM) ausgeführt. Der andere Teil der Java-Laufzeitumgebung sind die Java-
Klassenbibliotheken.[^1]
{: .fs-6 .fw-300 }

---

## JVM Implementationen

Es gibt verschiedenen Implementationen der JVM. Zwei Beispiele dafür sind
[Eclipse OpenJ9][open-j9] und [Oracle HotSpot][oracle-hs].

Wenn man mit mehreren JVMs arbeitet und deshalb [SDKMAN!][sdkman] verwendet um
diese zu verwalten, fallen die Abkürzungen `j9` oder `hs` ins Auge.

~~~
================================================================================
 Vendor        | Use | Version      | Dist    | Status     | Identifier
--------------------------------------------------------------------------------
 AdoptOpenJDK  |     | 16.0.1.j9    | adpt    | installed  | 16.0.1.j9-adpt
               |     | 16.0.1.hs    | adpt    | installed  | 16.0.1.hs-adpt
~~~
{: .mb-0}

_SDKMAN! sdk list java:_ Unterschiedliche JVM Implementationen.
{: .code-example .mt-0 .fs-2}

In einem 2018 erschienen [Artikel von Roy van Rijn][j9-vs-hs] wurden die 
verschiedenen Implementationen auf ihre Geschwindigkeitsunterschiede untersucht.
Hierbei zeigte sich, dass die **OpenJ9**-Implementation einige Vorteile 
aufweist.

## `equals()` / `hashCode()`

* gehören zusammen
* `hashCode()` zweier Instanzen kann gleich sein, auch wenn Instanzen bei 
   Vergleich unterschiedlich sind
* wenn `a.equals(b)` `true` ist, muss auch `a.hashCode() == b.hashCode()` gleich
  sein
* diese Standardsignatur ermöglicht einmalige Implementierung und 
  Wiederverwendung in Collections der Standardbibliothek

## Interessante Bibliotheken & Werkzeuge

* [resilience4j](https://resilience4j.readme.io)
  * [Tutorial: RateLimiter](https://reflectoring.io/rate-limiting-with-resilience4j/#tune-client-side-and-server-side-rate-limiters)
* MapStruct
  * z.B. für für die saubere _separation of concerns_ in (Jpa)Repositories
  * [Mapping immutable POJOs with MapStruct](https://medium.com/trabe/mapping-immutable-pojos-with-mapstruct-3f0bf4627fbc)
  * [Quick Guide to MapStruct](https://www.baeldung.com/mapstruct)
* [Kotlin kapt](https://kotlinlang.org/docs/kapt.html) (Annotation Processor)
* MicroProfile (Eclipse) (z.B. OpenTracing)
* [vy/hrrs: Record, transform, and replay HTTP requests in Java EE and Spring applications.](https://github.com/vy/hrrs)
* [gceasy - JVM Heap Dump Analyse](https://gceasy.io)

---

[^1]: Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Java_Virtual_Machine)

[open-j9]: https://www.eclipse.org/openj9/
[oracle-hs]: http://openjdk.java.net/groups/hotspot/
[sdkman]: https://sdkman.io/
[j9-vs-hs]: https://www.royvanrijn.com/blog/2018/05/openj9-jvm-shootout/