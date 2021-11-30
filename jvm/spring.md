---
layout: default
title: Spring Boot / Spring Framework
nav_order: 4
parent: JVM
---

# Spring Boot / Spring Framework
{: .no_toc }

---

## Annotationen

`@Configuration`

: _...is a class-level annotation indicating that an object is a source of bean 
  definitions._[^annot-configuration]

## Glossar

Spring Beans

: _In Spring, the objects that form the backbone of your application and that
are managed by the Spring IoC container are called beans. A bean is an object
that is instantiated, assembled, and otherwise managed by a Spring IoC
container. Otherwise, a bean is simply one of many objects in your
application. Beans, and the dependencies among them, are reflected in the
configuration metadata used by a container._

## IoC / DI-Container

Basis sind die Pakete `org.springframework.beans` und `org.springframework.context`.

Wie erhält der IoC-Container Informationen zum Instanziieren, Konfigurieren und 
Zusammenbauen von Objekten?

> The container gets its instructions on what objects to instantiate, configure, 
> and assemble by reading configuration metadata. The configuration metadata is 
> represented in XML, Java annotations, or Java code.

* <i class="bi bi-exclamation-triangle-filled"></i> [Java-basierte Container-Konfiguration](https://docs.spring.io/spring/docs/5.2.7.RELEASE/spring-framework-reference/core.html#beans-java)

## Tooling

* `spring-dev-tools`: Reload nach Build (<kbd>⌘ + F9</kbd>)

## Links

* [Referenzdokumentation: Spring Boot](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/index.html)
* [Referenzdokumentation: Spring Framework](https://docs.spring.io/spring/docs/5.2.7.RELEASE/spring-framework-reference/index.html)
* [Referenzdokumentation: Spring Security](https://docs.spring.io/spring-security/site/docs/5.3.2.RELEASE/reference/html5/)
* [Übersicht Spring Boot Starters](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/using-spring-boot.html#using-boot-starter)
* [A Guide to Spring Boot ConfigurationProperties for Kotlin Data Class](https://towardsdatascience.com/a-guide-to-use-spring-boots-configurationproperties-annotation-in-kotlin-s-dataclass-1341c63110f4)

---

[^annot-configuration]: https://docs.spring.io/spring/docs/5.2.7.RELEASE/spring-framework-reference/core.html#beans-java-configuration-annotation