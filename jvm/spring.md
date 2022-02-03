---
layout: default
title: Spring Boot / Spring Framework
nav_order: 50
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

* `spring-dev-tools`: Reload nach Build (<kbd>⌘</kbd>+<kbd>F9</kbd>)

## Test-Slices

Übersicht wissenswerter Annotationen und ihre Bedeutung.

Allen hier aufgeführten Annotationen ist gemein, das sie standardmäßig den 
Spring `ApplicationContext` laden. Damit hat man Zugriff auf den Dependency 
Injection Mechanismus und kann mit `@Autowired` Beans in die Testklassen 
injizieren.

`@SpringBootTest`

: erstellt Spring `ApplicationContext` mit der im Klassenpfad vorhandenen 
  `SpringBootApplication`
  * startet standardmäßig keinen Server
  * mittels `webEnvironment` kann weiter spezifiziert werden wie die Tests 
    ausgeführt werden
    * `MOCK` (Standard): `ApplicationContext` und gemockte Web-Umgebung, Server 
       wird nicht gestartet
    * `RANDOM_PORT`: `WebApplicationContext` mit echter Web-Umgebung, Server 
      wird gestartet mit zufällig gewähltem Port
    * `DEFINED_PORT`: wie `RANDOM_PORT` aber Port aus `application.properties`
       oder Standard-Port `8080`
    * `NONE`: `ApplicationContext` aber keine (gemockte oder echte) Web-Umgebung

  [Quelle][test-slice-spring-boot]

`@JsonTest`

: lädt zusätzlich Jackson `ObjectMapper` und verwandte Beans.

  [Quelle][test-slice-json-test]

`@WebMvcTest`

: Spring MVC Infrastruktur wird geladen. Begrenzung des Klassenscans z.B. auf 
  mit`@Controller` annotierte Komponenten.

  Kein Scan von `@Component`- oder `@ConfigurationProperties`-Beans. Letztere 
  können mit `@EnableConfigurationProperties` geladen werden.

  [Quelle][test-slice-web-mvc-test]

`@WebFluxTest`

: Ähnlich `@WebMvcTest` aber für Spring WebFlux-gestütze Anwendungen.

  Kein Scan von `@Component`- oder `@ConfigurationProperties`-Beans. Letztere 
  können mit `@EnableConfigurationProperties` geladen werden.

  [Quelle][test-slice-web-flux-test]

`@DataJpaTest`

: Lädt Spring JPA spezifische Komponenten wie `@Entity`-annotierte Klassen und
  Repositories.

  Kein Scan von `@Component`- oder `@ConfigurationProperties`- Beans. Letztere 
  können mit `@EnableConfigurationProperties` geladen werden.

  [Quelle][test-slice-data-jpa-test]

`@RestClientTest`

: Jackson, GSON und Jsonb-Unterstützung. Konfiguriert `RestTemplateBuilder`.
  
  Kein Scan von `@Component`- oder `@ConfigurationProperties`-Beans. Letztere 
  können mit `@EnableConfigurationProperties` geladen werden.

  [Quelle][test-slice-rest-client-test]

Darüber hinaus kann man in den Abschnitten 
[Additional Auto-configuration and Slicing][test-slice-additional] und
[User Configuration and Slicing][test-slice-user-configuration] des Kapitels 
"Testing" der Spring Boot Core Referenzdokumentation nachlesen, wie man die 
Tests weiter verfeinern kann falls weitere Komponenten gescannt bzw. geladen 
werden müssen.

## Links

* [Referenzdokumentation: Spring Boot](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/index.html)
* [Referenzdokumentation: Spring Framework](https://docs.spring.io/spring/docs/5.2.7.RELEASE/spring-framework-reference/index.html)
* [Referenzdokumentation: Spring Security](https://docs.spring.io/spring-security/site/docs/5.3.2.RELEASE/reference/html5/)
* [Übersicht Spring Boot Starters](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/using-spring-boot.html#using-boot-starter)
* [A Guide to Spring Boot ConfigurationProperties for Kotlin Data Class](https://towardsdatascience.com/a-guide-to-use-spring-boots-configurationproperties-annotation-in-kotlin-s-dataclass-1341c63110f4)

---

[^annot-configuration]: https://docs.spring.io/spring/docs/5.2.7.RELEASE/spring-framework-reference/core.html#beans-java-configuration-annotation

[test-slice-spring-boot]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications
[test-slice-json-test]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications.json-tests
[test-slice-web-mvc-test]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications.spring-mvc-tests
[test-slice-web-flux-test]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications.spring-webflux-tests
[test-slice-data-jpa-test]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications.autoconfigured-spring-data-jpa
[test-slice-rest-client-test]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications.autoconfigured-rest-client
[test-slice-additional]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications.additional-autoconfiguration-and-slicing
[test-slice-user-configuration]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.testing.spring-boot-applications.user-configuration-and-slicing
