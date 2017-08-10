# Error Handling Design

Massnahmen für die Fehler-Vermeidung
1. Testen
2. Statische Codeanalyse
3. Review der Architektur und Code
4. Bewusstes Programmieren

Lernziele
* [ ] Error Handling und defensiver Programmierung erklären und anweden können
* [ ] Eine sinnvolle Error-Handling Policy, Exception Policy, Asertion Policy und Logging Policy für eigenes Projekt definieren können

---

## Defensive Programmierung

### 1. Schutz vor ungültigem Input

Alle Werte von externen Quellen, Benutzereingaben überprüfen

### 2. Fehler abfangen

Ungültige Zustände systematisch abfangen.

Schlecht:
```java
switch (motor.getCommand()) {
    case Command_Accelerate:
        accelerate();
        break;
    case Command_Turn:
        turn();
        break;
    // there are no other commands
}
```
Default-Verhalten nicht definiert. Es muss eine Exception geworfen werden.
```java
default:
    throw new AssertionError("Unsupported command");
```

### 3. Fehler Barrikaden

Barrikade im Programm gegen Fehler definieren.
* Hinter den Barrikaden sind Daten gültig
* Daten bei Grenzübertritt überprüfen

Beispiel auf Klassenniveau
* `public` Methoden überprüfen Daten
* `private` Methoden gehen von gültigen Daten aus

Probleme bei der defensiver Programmierung
1. Man kann nicht alles testen
2. Kostet mehr (Programmierzeit + Programmlaufzeit)
3. Duplizierter Code

## Fehlerbehandlung

* Konservative Behandlung
  * Error Handling Funktion aufrufen
  * Fehlermeldung anzeigen
  * Shutdown
* Optimistische Behandlung
  * Neutrales Resultat
  * Nächstögliches plausibles Resultat
  * Warnung in Stream loggen

*Korrektheit* vs *Robustheit*

Korrektheit: Niemals ungenaues Resultat liefern

Robustheit: Versuche Software am Laufen zu halten

p.20 cont.

## Error Handling Werkzeuge
* Exceptions
* Assertions
* Logging

