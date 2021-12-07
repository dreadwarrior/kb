---
layout: default
title: Maven
nav_order: 2
parent: JVM
---

# Maven
{: .no_toc }

---

## Inhaltsverzeichnis
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## CLI

### Einige Befehle, die man kennen sollte

1. `mvn clean` - Aufräumen des Projekts, löscht den Ordner `target`
2. `mvn package` - Erzeugt das JAR- oder WAR-Archiv des Projekts.
3. `mvn install` - Die erzeugten Projektartefakte (z.B. JAR-/WAR-Archiv oder 
    pom.xml) werden in das lokale Repository installiert.
4. `mvn dependency:tree` - Listet den Abhängigkeitsbaum des Projekts auf.
5. `mvn dependency:analyze` - Analyse des Projekts um nicht verwendete, aber
    deklarierte und verwendete, aber nicht deklarierte Abhängigkeiten zu 
    ermitteln.
6. `mvn archetype:generate` - Erzeugt ein Projekt auf Basis der Vorlage des
   Archetypens.
7. `mvn -f dir/pom.xml package` - Erzwingt die Verwendung einer alternativen
    POM.
8. `mvn -o <command>` - Führt `<command>` im Offline-Modus aus.
9. `mvn -q <command>` - Führt `<command>` im stillen Modus aus. Es werden nur
   Fehler und Testergebnisse ausgegeben.
10. `mvn -X <command>` - Führt `<command> im Debug-Modus aus.
11. `mvn -v` - Zeigt Versionsinformation an.
12. `mvn -V <command>` - Ausgabe von Versionsinformationen und anschließendes 
    Ausführen von `<command>`.
13. `mvn -DskipTests <command>` - Überspringt die Ausführung von Tests. Es kann
    auch `-Dmaven.skip.tests=true` verwendet werden.
14. `mvn -T 4 clean install` - Parallele Erstellung des Projekts mit 4 Threads,
    kann zur Verbesserung der Performance in einem Multi-Modul-Projekt 
    beitragen.

### Beispiele

* (detaillierte) Hilfe zu einem Goal (z.B. `compiler:compile` aufrufen)

      mvn help:describe -Dcmd=compiler:compile [-Ddetail]

* Ausführung in headless-Umgebungen (z.B. CI-Systeme)

      mvn -B|--batch-mode

* Optimierung von Abhängigkeiten

      mvn dependency:analyze

  * besonderes Augenmerk auf _used, undeclared dependencies_, dann mit 
    `mvn dependency:tree` im entsprechenden Modul genauer schauen und die 
    Abhängigkeit ggf. direkt in der POM laden

## Dependencies

* Scopes
  * `compiled`: immer verfügbar, Standard
  * `provided`: wenn im JDK oder J2EE-Container bereitgestellt, Dependency wird 
     nicht paketiert
  * `runtime`: nicht erforderlich beim Kompilieren
  * `test`
  * `system`: ähnlich provided, nur mit expliziter Pfadangabe zum JAR
* Versionsbereiche
  * Semver 1.0 wird unterstützt[^maven-semver-support]
  * <i class="bi bi-exclamation-triangle-fill"></i> Vorsicht bei der Verwendung 
    des Bugfix-Segments[^maven-semver-bugfix]
    * mögliche Strategie: Verzicht auf Bugfix-Segment
      * ist abhängig von der Entwicklungs- und Versionsmanagementqualität der 
        Dependency
      * z.B. `[1.7,1.8)`
  * [Verwendung des Plugins `org.codehaus.mojo:versions-maven-plugin`](https://www.baeldung.com/maven-dependency-latest-version) 
    für Updateanalyse

## Glossar

Archetype

: _In short, Archetype is a Maven project templating toolkit. An archetype is
  defined as an original pattern or model from which all other things of the
  same kind are made. The name fits as we are trying to provide a system that
  provides a consistent means of generating Maven projects._

Maven Assemblies

: Archiv oder Verzeichnis mit einem benutzerdefinierten Layout

pom.xml

: _descriptive, declarative Project Object Model_[^the-pom]

  * erbt von "The Super POM", definiert Standard-Projektstruktur (sources,
    target, tests, ...)
    * daher kommen auch Plugins wie _compiler_, _assembly_ usw.
    * Analyse mit `mvn help:effective-pom`

## IntelliJ-Integration

### Quell- und Zielplattform angeben

~~~
<properties>
    <maven.compiler.source>17</maven.compiler.source>
    <maven.compiler.target>8</maven.compiler.target>
</properties>
~~~
{: .language-xml .mb-0}

_pom.xml:_ Verwendung der Compiler-Argumente `-source` und `-target`.
{: .code-example .mt-0 .fs-2}

Ab Java 9 existiert das `-release` Argument, welches mit der Property 
`maven.compiler.release` (ab `maven-compiler-plugin:3.8.x`) gesetzt werden kann:

~~~
<properties>
    <maven.compiler.release>17</maven.compiler.release>
</properties>
~~~
{: .language-xml .mb-0}

_pom.xml:_ Verwendung des `-release` Compiler-Arguments.
{: .code-example .mt-0 .fs-2}

## Plugins

* Testrunner[^testrunner]
  * Surefire: Unit tests
  * Failsafe: Integration tests

## pom.xml

### `packaging`

* <i class="bi bi-exclamation-triangle-fill"></i> Wert der Eigenschaft (`pom`, 
  `jar`, `war`) beeinflusst die Lifecycle-Schritte/Phasen[^package-specific-lifecycle]

### `dependencyManagement`

* erlaubt in Elterprojekten die einmalige und zentralisierte Definition von 
  bestimmten Versionen von Abhängigkeiten (und auch den Umgang mit transitiven 
  Abhängigkeiten)
* <i class="bi bi-exclamation-triangle-fill"></i> Eigenschaften von 
  Kindprojekten/-modulen erweitern Eigenschaften von übergeordneten 
  Projekten/Modulen.

## Profile

* <i class="bi bi-lightbulb-fill"></i> mittels `-P` oder `--activate-profiles` über 
  das CLI steuerbar
* <i class="bi bi-lightbulb-fill"></i> wenn ein Profil mittels `<activation>` 
  gesteuert wird, kann an der CLI mit `mvn help:active -profiles` analysiert 
  werden, welche Profile gültig sind

## Links

* [Maven in 5 minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)
* [Maven the reference guide : 3.6 POM Best Practices : 3.6.2 Multi-module vs. Inheritance](https://books.sonatype.com/mvnref-book/reference/pom-relationships-sect-pom-best-practice.html#pom-relationships-sect-multi-vs-inherit)
* [Maven the reference guide : 4.1 Introduction : 4.1.2 Default Lifecycle (default)](https://books.sonatype.com/mvnref-book/reference/lifecycle-sect-structure.html#lifecycle-sect-default)

---

[^testrunner]: [Maven Failsafe Plugin](http://maven.apache.org/surefire/maven-failsafe-plugin/index.html)
[^the-pom]: [Maven the reference guide : 3.2 The POM](https://books.sonatype.com/mvnref-book/reference/pom-relationships-sect-pom.html)
[^package-specific-lifecycle]: [Maven the reference guide : 4.2 Package-specific Lifecycles](https://books.sonatype.com/mvnref-book/reference/lifecycle-sect-package-specific.html)
[^maven-semver-support]: [POM reference : Version Order Specification](https://maven.apache.org/pom.html#version-order-specification)
[^maven-semver-bugfix]: [Legit but Useless: Maven Version Ranges Explained](https://medium.com/@MichaKutz/legit-but-useless-maven-version-ranges-explained-d4ba66ac654)
