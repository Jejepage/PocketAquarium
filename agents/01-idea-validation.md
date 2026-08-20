# Rolle: Idee und Problemvalidierung

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt nur die Regeln für die Phase `Idee und Problemvalidierung`.

## Ziel

Verwandle eine zunächst grobe App-Idee gemeinsam mit dem Entwickler in eine kleine, kritisch geprüfte und entscheidungsfähige Produktidee. Das Ergebnis soll zeigen, ob die Idee weitergeführt, verändert oder verworfen werden sollte.

## Erforderliche Eingabe

- ursprüngliche Idee oder Aufgabenbeschreibung des Entwicklers

Fehlt diese Eingabe, setze `STATUS.md` auf `Blockiert` und bitte um die Idee. Erfinde keine Ausgangsidee.

## Grenzen

- Führe noch keine technische Planung oder Implementierung durch.
- Lege noch keine konkrete Architektur, Programmiersprache oder Bibliothek fest.
- Behandle Annahmen nicht als bestätigte Tatsachen.
- Eine externe Marktstudie oder Befragung ist nicht erforderlich.
- Wenn eine Empfehlung von aktuellen externen Fakten abhängt, recherchiere gezielt in möglichst primären, verlässlichen Quellen und verlinke sie. Trenne Quellenbefund und eigene Schlussfolgerung.

## Vorgehen

1. Formuliere die Ausgangsidee in einem kurzen, neutralen Absatz.
2. Kläre Problem, Zielgruppe, Nutzungssituation, bisherigen Lösungsweg und erwarteten Nutzen.
3. Prüfe kritisch, ob eine eigene App einen erkennbaren Vorteil gegenüber dem bisherigen Vorgehen bietet.
4. Reduziere die Idee auf die kleinstmögliche Version, die bereits einen eigenständigen Nutzen hat.
5. Benenne bewusst nicht benötigte Funktionen, wesentliche Annahmen, offene Fragen und Risiken.
6. Stelle nur Fragen, deren Antwort die Empfehlung oder den Mindestumfang wesentlich verändern kann. Fasse zusammengehörige Fragen kompakt zusammen.
7. Gib eine begründete Empfehlung: `Weiterführen`, `Verändern` oder `Verwerfen`.

## Ergebnisdatei

Erstelle oder aktualisiere `docs/idea-validation.md` mit dieser Struktur:

```markdown
# Ideen- und Problemvalidierung

## Status und Freigabe
## Ausgangsidee
## Problem
## Zielgruppe und Nutzungssituation
## Bisheriger Lösungsweg
## Zentraler Nutzen
## Kleinstmögliche sinnvolle Version
## Bewusste Nicht-Ziele
## Annahmen
## Offene Fragen
## Risiken und technische Unsicherheiten
## Empfehlung
## Quellen
```

Unter `Status und Freigabe` stehen zunächst `Entwurf` und `Freigabe ausstehend`. Der Abschnitt `Quellen` enthält nur tatsächlich verwendete Quellen; andernfalls steht dort `Keine externe Recherche erforderlich`.

## Qualitätsprüfung

Prüfe vor der Übergabe:

- Problem, Zielgruppe und Nutzungssituation sind konkret genug, um Produktentscheidungen zu tragen.
- Der Nutzen beschreibt ein Ergebnis für den Benutzer und nicht nur eine Funktionsliste.
- Die kleinste Version ist deutlich enger als eine vollständige Wunschlösung.
- Annahmen, Fakten und offene Fragen sind erkennbar getrennt.
- Risiken und Gegenargumente werden nicht beschönigt.
- Die Empfehlung folgt nachvollziehbar aus dem Dokument.
- Das Dokument enthält keine vorgezogene technische Lösung.

Dokumentiere diese Prüfung in `STATUS.md` und setze den Status auf `Bereit zur persönlichen Abnahme`.

## Freigabe und Übergang

Nach der Entscheidung des Entwicklers:

- `Weiterführen`: Entscheidung in der Ergebnisdatei festhalten, GitHub-Abschluss durchführen und als nächste Phase `Produktbeschreibung / PRD` eintragen.
- `Verändern`: Idee und Dokument überarbeiten; die Phase bleibt aktiv, bis eine neue Entscheidung vorliegt.
- `Verwerfen`: Entscheidung dokumentieren, GitHub-Abschluss durchführen und das Projekt ohne Start einer weiteren Produktphase abschließen.

Wechsle erst nach dokumentierter Freigabe und erfolgreichem GitHub-Abschluss zur nächsten Phase.
