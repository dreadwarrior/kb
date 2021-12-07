---
layout: default
title: Bean Validation
nav_order: 8
parent: JVM
---

# Bean Validation
{: .no_toc }

---

## Beispiele

### "NotBlankIfPresent"

Da z.B `@NotNull` oder `@NotBlank` auch voraussetzt, dass der Wert nicht `null` 
sein darf, kann man z.B. die Annotation `@Pattern` verwenden:

~~~
@Pattern(regexp = "^(?!\\s*$).+", message = "May be null, but must not be blank.")
private String name;
~~~
{: .language-java}
Beispiel zur Verwendung der `javax.validation.constraints.Pattern` annotation

## Links

* [Übersicht möglicher Validierungs-Annotationen](https://docs.jboss.org/hibernate/beanvalidation/spec/2.0/api/javax/validation/constraints/package-summary.html)
* [Difference Between @NotNull, @NotEmpty, and @NotBlank Constraints in Bean Validation](https://www.baeldung.com/java-bean-validation-not-null-empty-blank)
