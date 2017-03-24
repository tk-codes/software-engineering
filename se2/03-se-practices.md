# Software Engineering Practices

## Requirements Practices

### 1. Dig for requirements

1. Zusammenarbeit mit den Kunden (Denken aus Benutzersicht)
2. Kritisches hinterfragen und nachbearbeiten
3. Genügend generell und abstrakt definieren
4. Verfolgung des Ursprungs (Person, Grund, Datum)

Ermittlungstechniken:
* Dokumentenstudium
* Befragung: Interview, Fragebogen, Workshop
* Beobachtung
* Kreativität: Brainstorming


### 2. Make quality a requirement

1. Qualität als NF-Requirements aufnehmen (Performance, scalability, security, robustness etc.)
2. Qualitätsanforderungen sollen testbar/messbar sein.
  * Max. Antwortzeiten unter definierten Umständen
  * Min. unterstützte Datenmenge

Beispiele:
1. Stock orders should be placed `within 100ms`.
2. The processing of an image should not `exceed 2 seconds` for an image size `up to 100MB`.

### 3. Deal with changes

1. Anticipate Requirement changes
  * define requirements as abstract as possible.
2. Design for change
3. Short iterations
  * continuous user feedback
4. Change assessment
  * Qualität der Requirements nach jeder Iteration prüfen und bei Bedarf überarbeiten

## Design Practices

### 4. Don't repeat yourself

Gefahr von Inkonsistenzen bei Änderungen.

**Avoid**

1. Code duplication
2. Documentation in code: redundant description

### 5. Achieve orthogonality

> Eliminate effects between unrelated things.

1. Keine Koppelung zwischen konzeptionell unabhängiger Aspekte
2. Möglichst wenig Abhängigkeiten
3. Acylic Dependency Prinzip (Direkte und indirekte Zyklen meiden)

Ziel: Hohe Kohäsion --> Reduktion auf eine zusammengehörigen Aufgabe/Abstraktion pro Komponente

Schlecht:
1. Koppellung
```java
class Splitter {
    public Splitter(InputStreamReader reader);
    public void readNextLine();
    public int numFields();
    public String getField(int fieldNumber);
}
```
Reader und Splitter zusammengekoppelt.

2. zwei unterschiedliche Funktionen
```java
Item getOrCreateItem(string id);
```

Vorteile Orthogonalität
1. Selektive wiederverwendung eines Aspekt
2. Ein Aspekt isoliert änderbar
3. Einfacher zu verstehen
4. Einfacher zu testen

### 6. Design to test

1. Testbarkeit vor Entwicklungszeit betrachten
2. Testbarkeit hat Einfluss auf die Architektur

>>> Dependency Injection

## Implementation Practices

### 7. Fix broken windows

Probleme sofort beheben, wenn sie entstehen

### 8. Refactor early and often

Vorgehen
1. Refactoring soll keine neue Funktionen bieten
2. Gute Tests vor Beginn des Refactoring haben
3. Mehrere kleinere Schritte als eine Riesenänderung

### 9. Program deliberately

>>> Avoid "Programming by Coincidence/Luck"

## Verification Practices

### 10. Test rigorously

1. Früh, häufig und automatisch testen
  * Design to test
  * TDD / BDD
  * Hohe Code Coverage erzielen
2. "Find issues Once"
  * Gefundene Fehler verstehen und dafür Test schreiben

Verifikation

1. Statische Analyse
  * Design Reviews
  * Code Reviews
2. Testing (Dynamisch)
  * Unit Tests
  * Integration Tests

### 11. Perform reviews

1. Einzelne Reviews durch Experten
2. Kombination Design & Code Reviews

