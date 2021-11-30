---
layout: default
title: Softwarearchitektur
nav_order: 1
has_children: false
---

# Softwarearchitektur
{: .no_toc }

Eine **Softwarearchitektur** ist einer der Architekturtypen in der Informatik 
und beschreibt die grundlegenden Komponenten und deren Zusammenspiel innerhalb 
eines Softwaresystems.[^1]
{: .fs-6 .fw-300 }

---

## [DAO vs Repository Patterns](https://www.baeldung.com/java-dao-vs-repository)

* DAO "_...is an abstraction of data persistence and is considered closer to the underlying storage, which is often table-centric..._"
* Repository "_...sits at a higher level, closer to the business logic of an app..._"
* <i class="bi bi-question-circle-fill"></i> Kombination möglich, z.B.:

![Repository – depends_on DAO – depends_on DatabaseConnection/HTTPCLient](http://yuml.me/diagram/scruffy/class/%5BRepository%5D%3C%3E-depends%20on%3E%5BDAO%5D%3C%3E-depends%20on%3E%5BDatabaseConnection/HTTPClient%5D.svg)

---

[^1]: Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Softwarearchitektur)
