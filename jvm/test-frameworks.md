---
layout: default
title: Test-Frameworks
nav_order: 10
parent: JVM
---

# Test-Frameworks
{: .no_toc }

---

## JUnit5

Wichtige Abschnitte der Dokumentation für Neulinge:

* [2. Writing Tests / 2.1 Annotations](https://junit.org/junit5/docs/current/user-guide/#writing-tests-annotations)
* [2. Writing Tests / 2.4 Assertions](https://junit.org/junit5/docs/current/user-guide/#writing-tests-assertions)
* [2. Writing Tests / 2.5 Assumptions](https://junit.org/junit5/docs/current/user-guide/#writing-tests-assumptions)
* [2. Writing Tests / 2.10 Test Instance Lifecycle](https://junit.org/junit5/docs/current/user-guide/#writing-tests-test-instance-lifecycle)
  * obwohl Standardverhalten (Isolation pro Methode) bereits optimal ist,
    aber gut zu wissen wie man es umstellen kann, wenn man "nicht so gute"
    Tests hat
  * [`TestInstance.Lifecycle.PER_CLASS` möglicherweise "Best Practice" für Kotlin-Projekte](https://phauer.com/2018/best-practices-unit-testing-kotlin/#avoid-static-and-reuse-the-test-class-instance) 
    (verhindert statische Instanziierung)
* [2. Writing Tests / 2.11 Nested Tests](https://junit.org/junit5/docs/current/user-guide/#writing-tests-nested)
  (eventuell interessant für BDD-/Acceptance-Tests, siehe 
  [Behavior-Driven Development mit JUnit 5](https://blog.codecentric.de/2018/09/behavior-driven-development-mit-junit-5/))
* [2. Writing Tests / 2.12 Dependency Injection for Constructors and Methods](https://junit.org/junit5/docs/current/user-guide/#writing-tests-dependency-injection)
  (zeigt mit _TestReporter_ wie man ggf. auf `STDOUT`/`STDERR` schreiben kann)
* [2. Writing Tests / 2.15 Parameterized Tests](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parameterized-tests)
  * **Achtung**: diese API ist als _experimental_ gekennzeichnet; benötigt _junit-jupiter-params_ Artefakt 
* [2. Writing Tests / 2.17 Dynamic Tests](https://junit.org/junit5/docs/current/user-guide/#writing-tests-dynamic-tests)
  (ggf. nützlich für property-based testing?)
* [2. Writing Tests / 2.19 Parallel execution](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution)
  * **Achtung**: diese API ist als experimental gekennzeichnet
* [4. Running Tests / 4.2 Build Support / 4.2.2 Maven](https://junit.org/junit5/docs/current/user-guide/#running-tests-build-maven)
  wie man [JUnit5-Konfigurationsparameter in einer Maven pom.xml](https://junit.org/junit5/docs/current/user-guide/#running-tests-build-maven-config-params) setzt
* [5. Extension Model / 5.15 Relative Execution Order of User Code and Extensions](https://junit.org/junit5/docs/current/user-guide/#extensions-execution-order)

## Weitere Bibliotheken


* ArchUnit - Prüfung von Architekturregeln (z.B. Service darf keinen Controller aufrufen)
* [Kotest](https://github.com/kotest/kotest) - (idiomatic) Testframework für Kotlin
* [Testcontainers](https://www.testcontainers.org) - _... a Java library that supports JUnit tests, providing lightweight,
  throwaway instances of common databases, Selenium web browsers, or anything
  else that can run in a Docker container._
* [AssertJ-DB](https://assertj.github.io/doc/#assertj-db)

## Links

* [Modern Best Practices for Testing in Java](https://phauer.com/2019/modern-best-practices-testing-java/)
