# Rolle: Produktbeschreibung / PRD

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt nur die Regeln für die Phase `Produktbeschreibung / PRD`.

## Ziel

Übersetze die freigegebene Produktidee in ein kompaktes, verbindliches und technisch neutrales Product Requirements Document für die erste Version.

## Erforderliche Eingabe

- freigegebene `docs/idea-validation.md`

Prüfe, ob die Entscheidung `Weiterführen` dokumentiert und die vorherige Phase auf GitHub abgeschlossen ist. Bei einer fehlenden Freigabe, einem ungeklärten Widerspruch oder einem fehlenden GitHub-Abschluss setze `STATUS.md` auf `Blockiert`.

## Grenzen

- Entscheide noch nicht über Architektur, Framework, Speicherung oder konkrete technische Umsetzung.
- Entwirf noch keine einzelnen Ansichten oder detaillierten Bedienabläufe.
- Halte die erste Version möglichst bei drei bis fünf Kernfunktionen.
- Übernimm offene Annahmen aus der Ideenvalidierung nicht stillschweigend als Anforderungen.
- Erfinde keine Messwerte oder Zielzahlen; kennzeichne noch festzulegende Werte ausdrücklich.

## Vorgehen

1. Übernimm Problem, Zielgruppe und zentralen Nutzen konsistent aus der freigegebenen Ideenvalidierung.
2. Formuliere Produktvision und Hauptanwendungsfall als beobachtbares Benutzerergebnis.
3. Leite die wichtigsten Benutzerbedürfnisse ab.
4. Definiere nur die unverzichtbaren Kernfunktionen der ersten Version. Gib jeder Funktion eine stabile Kennung wie `F-01` und ordne sie einem Benutzerbedürfnis zu.
5. Trenne spätere Optionen und bewusste Nicht-Ziele klar vom Umfang der ersten Version.
6. Beschreibe relevante Qualitätsanforderungen aus Benutzersicht, beispielsweise Zuverlässigkeit, Datenschutz, Barrierefreiheit oder Reaktionsverhalten, ohne technische Lösung vorzugeben.
7. Formuliere überprüfbare Erfolgskriterien und kennzeichne offene Produktentscheidungen.

## Ergebnisdatei

Erstelle oder aktualisiere `docs/product-requirements.md` mit dieser Struktur:

```markdown
# Produktanforderungen

## Status und Freigabe
## Produktvision
## Problem und Zielgruppe
## Hauptanwendungsfall
## Benutzerbedürfnisse
## Umfang der ersten Version
## Bewusste Nicht-Ziele
## Mögliche spätere Funktionen
## Qualitätsanforderungen
## Erfolgskriterien
## Offene Produktentscheidungen
## Rückverfolgbarkeit
```

Der Umfang der ersten Version wird als kompakte Tabelle mit mindestens diesen Spalten dokumentiert:

| ID | Kernfunktion | Zugeordnetes Benutzerbedürfnis | Priorität |
|---|---|---|---|

Unter `Rückverfolgbarkeit` wird für jede Kernfunktion auf die relevante Aussage der Ideenvalidierung und auf mindestens ein Erfolgskriterium verwiesen. Unter `Status und Freigabe` stehen zunächst `Entwurf` und `Freigabe ausstehend`.

## Qualitätsprüfung

Prüfe vor der Übergabe:

- Jede Kernfunktion unterstützt ein dokumentiertes Benutzerbedürfnis.
- Der Hauptanwendungsfall ist mit dem vorgesehenen Umfang vollständig möglich.
- Funktionen der ersten Version, spätere Optionen und Nicht-Ziele sind eindeutig getrennt.
- Erfolgskriterien sind beobachtbar oder messbar und enthalten keine erfundenen Zielwerte.
- Anforderungen widersprechen der freigegebenen Ideenvalidierung nicht.
- Produktanforderungen enthalten keine vorgezogene technische oder detaillierte UI-Lösung.
- Offene Entscheidungen sind so konkret formuliert, dass der Entwickler sie beantworten kann.

Dokumentiere diese Prüfung in `STATUS.md` und setze den Status auf `Bereit zur persönlichen Abnahme`.

## Freigabe und Übergang

Nach der Freigabe durch den Entwickler:

1. Halte Freigabestatus und wichtige Entscheidungen in der Ergebnisdatei fest.
2. Führe den GitHub-Abschluss der Phase durch.
3. Trage als nächste Phase `Funktions- und UI-Plan` ein.
4. Nenne `docs/product-requirements.md` als erforderliche freigegebene Eingabe.

Wechsle erst nach erfolgreichem GitHub-Abschluss zur nächsten Phase.
