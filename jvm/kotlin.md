---
layout: default
title: Kotlin
nav_order: 4
parent: JVM
---

# Kotlin
{: .no_toc }

---

## Aufgaben

### Collections / Aggregate Operations

- [ ] finde eine leicht zu verstehende Beschreibung/Definition für `fold` und `reduce`.

## IntelliJ-Integration

### Maven

Mit der Property `kotlin.compiler.jvmTarget` wird die Eigenschaft in IntelliJ
automatisch gesetzt (Projekt auswählen → <kbd>⌘</kbd>+<kbd>↓</kbd> → Modules → Kotlin Target 
platform).

~~~
<properties>
    <kotlin.compiler.jvmTarget>17</kotlin.compiler.jvmTarget>
</properties>
~~~
{: .language-xml .mb-0}

_pom.xml:_ Verwendung des Kotlin Compiler-Arguments `jvmTarget`.
{: .code-example .mt-0 .fs-2}

## Scope functions

| function | context object | return value | use case |
|:-|:-|:-|:-|
| `run` | `this` (lambda receiver) | lambda result | _...recommended for lambdas that mainly operate on the object members: call its functions or assign properties..._ |
| `with` | `this` (lambda receiver) | lambda result | [Calling multiple methods on an object instance (with)](https://kotlinlang.org/docs/reference/idioms.html#calling-multiple-methods-on-an-object-instance-with) |
| `apply` | `this` (lambda receiver) | context object | [Configuring properties of an object (apply)](https://kotlinlang.org/docs/reference/idioms.html#configuring-properties-of-an-object-apply) |
| `let` | `it` (lambda argument) | lambda result | _...when the object is mostly used as an argument in function calls..._ |
| `also` | `it` (lambda argument) | context object | _...also better if you use multiple variables in the code block..._ |

## Links

* [Kotlin Idioms](https://kotlinlang.org/docs/reference/idioms.html)
* [Best Practices for Unit Testing in Kotlin](https://phauer.com/2018/best-practices-unit-testing-kotlin/)
