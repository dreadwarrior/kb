---
layout: default
title: JVM
nav_order: 4
has_children: true
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

* [gceasy - JVM Heap Dump Analyse](https://gceasy.io)

## `equals()` / `hashCode()`

* gehören zusammen
* `hashCode()` zweier Instanzen kann gleich sein, auch wenn Instanzen bei 
   Vergleich unterschiedlich sind
* wenn `a.equals(b)` `true` ist, muss auch `a.hashCode() == b.hashCode()` gleich
  sein
* diese Standardsignatur ermöglicht einmalige Implementierung und 
  Wiederverwendung in Collections der Standardbibliothek

## Comparatoren

* werden zur Sortierung verwendet

## Interessante Bibliotheken

* [resilience4j](https://resilience4j.readme.io)
  * [Tutorial: RateLimiter](https://reflectoring.io/rate-limiting-with-resilience4j/#tune-client-side-and-server-side-rate-limiters)
* MapStruct
  * z.B. für für die saubere _separation of concerns_ in (Jpa)Repositories
  * [Mapping immutable POJOs with MapStruct](https://medium.com/trabe/mapping-immutable-pojos-with-mapstruct-3f0bf4627fbc)
  * [Quick Guide to MapStruct](https://www.baeldung.com/mapstruct)
* [Kotlin kapt](https://kotlinlang.org/docs/kapt.html) (Annotation Processor)
* MicroProfile (Eclipse) (z.B. OpenTracing)

---

[^1]: Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Java_Virtual_Machine)
