---
layout: default
title: Multi-Modul-Projekte
nav_order: 3
parent: JVM
---

# Multi-Modul-Projekte
{: .no_toc }

---

## Einleitung

Multi-Modul-Projekte mit Maven (i.F. _MMMP_) können eine große Herausforderung 
darstellen.
Trotz des seit Jahren anhaltenden Trends der Entwicklung von Microservice-
Architekturen, findet man im Berufsleben oft das Gegenteil vor, und muss sich
mit großen Entwicklungs- oder gar Deployment-Monolithen auseinandersetzen.

Das Nachschlagewerk [Maven by Example][maven-by-example] bietet mit den beiden
Kapiteln für [einfache][simple-mmmp] und [komplizierte][enterprise-mmmp] _MMMP_
eine detaillierte Beschreibung des Themas.

## Kommandozeilen-Schalter

Bei der Arbeit mit einem _MMMP_ ist es wichtig, dass Entwickler*innen schnell 
und effizient entwickeln können. Dazu gehört auch, dass bei Fehlschag von Maven 
_Goals_ nach der Korrektur die Ausführung fortgesetzt werden kann ohne erneut 
alle Module des Projekts kompilieren zu müssen.

In der Maven Dokumentation "[Guide to Working with Multiple Modules][guide-mmmp]"
findet sich neben der Dokumentation dieser Kommandozeilen-Schalter außerdem 
Informationen über die Funktionsweise des _Reactor_.

## Erzeugung eines Blanko-MMMP für Experimentierzwecke

Mit den folgenden Befehlen lässt sich schnell ein _MMMP_ erzeugen:

~~~
$ mvn archetype:generate \
    -DarchetypeGroupId=org.codehaus.mojo.archetypes \
    -DarchetypeArtifactId=pom-root \
    -DarchetypeVersion=RELEASE \
    -DgroupId=de.dreadlabs \
    -DartifactId=mymmmp \
    -Dversion=1.0-SNAPSHOT \
    -DpackageInPathFormat=mymmmp \
    -B
$ cd mymmmp
$ mvn archetype:generate \
    -DarchetypeGroupId=org.apache.maven.archetypes \
    -DarchetypeArtifactId=maven-archetype-quickstart \
    -DarchetypeVersion=RELEASE \
    -DgroupId=de.dreadlabs \
    -DartifactId=module-a \
    -Dversion=1.0-SNAPSHOT \
    -DpackageInPathFormat=module-a \
    -B
~~~
{: .language-shell}

[<i class="bi bi-download"></i> Ergebnis als .tar.gz-Archiv zum Download]({{ "/assets/files/jvm/multi-modul-projekte/mymmmp.tar.gz" | relative_url }}){: .btn .btn-primary }

## Tipps

### Reactor Build Order anzeigen

Das Maven Goal `validate` kann als leichtgewichtiges Ausführungsziel die 
Erzeugungsreihenfolge der Module des _MMMP_ anzeigen.

~~~
mvn validate
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] mymmmp                                                             [pom]
[INFO] module-a                                                           [jar]
...
~~~

[maven-by-example]: https://books.sonatype.com/mvnex-book/reference/index.html
[simple-mmmp]: https://books.sonatype.com/mvnex-book/reference/multimodule.html
[enterprise-mmmp]: https://books.sonatype.com/mvnex-book/reference/multimodule-web-spring.html
[guide-mmmp]: https://maven.apache.org/guides/mini/guide-multiple-modules.html
