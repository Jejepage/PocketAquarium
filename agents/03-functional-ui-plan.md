# Rolle: Funktions- und UI-Plan

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt nur die Regeln für die Phase `Funktions- und UI-Plan`.

## Ziel

Übersetze das freigegebene PRD in vollständiges, beobachtbares Verhalten der App: Ansichten, Navigation, Benutzerabläufe, Zustände und prüfbare Akzeptanzkriterien.

## Erforderliche Eingabe

- freigegebene `docs/product-requirements.md`

Prüfe, ob alle Kernfunktionen stabile Kennungen besitzen, die Produktentscheidungen abgeschlossen oder ausdrücklich offen sind und die vorherige Phase auf GitHub abgeschlossen ist. Andernfalls setze `STATUS.md` auf `Blockiert` und benenne die fehlende Klärung.

## Grenzen

- Plane noch keine technische Architektur, konkrete Persistenztechnik oder Bibliothek.
- Füge keine Funktion hinzu, die nicht durch das PRD begründet ist.
- Erstelle nur so viele Ansichten und Navigationsschritte wie für die Kernabläufe nötig.
- Triff keine plattformspezifische Detailentscheidung, bevor die Zielplattform feststeht.
- Verwende Text-Wireframes nur, wenn sie einen Ablauf oder eine Ansicht verständlicher machen.

## Vorgehen

1. Erstelle für jede Kernfunktion einen vollständigen Benutzerablauf vom Ausgangspunkt bis zum sichtbaren Ergebnis.
2. Leite daraus eine minimale Liste von Ansichten, Seiten, Dialogen oder Fenstern und ihre Navigation ab.
3. Beschreibe pro Ansicht Zweck, dargestellte Daten, mögliche Aktionen und erwartete Reaktion der App.
4. Berücksichtige relevante Lade-, Leer-, Fehler-, Erfolgs-, Berechtigungs- und gegebenenfalls Offline-Zustände.
5. Beschreibe, wann Berechtigungen angefragt werden und wie die App bei Ablehnung verständlich weiterarbeitet.
6. Plane grundlegende Barrierefreiheit: verständliche Beschriftungen, logische Fokus- und Bedienreihenfolge, skalierbare Inhalte, ausreichende visuelle Unterscheidbarkeit sowie alternative Bedienwege, soweit für Plattform und Funktion relevant.
7. Formuliere für jede Kernfunktion beobachtbare Akzeptanzkriterien. Verwende Kennungen wie `AC-F01-01`, damit jedes Kriterium auf eine PRD-Funktion zurückgeführt werden kann.
8. Dokumentiere offene UX-Entscheidungen, statt sie unbemerkt als Annahme festzulegen.

## Ergebnisdatei

Erstelle oder aktualisiere `docs/functional-plan.md` mit dieser Struktur:

```markdown
# Funktions- und UI-Plan

## Status und Freigabe
## Geltungsbereich und Grundlagen
## Informations- und Navigationsstruktur
## Wichtigste Benutzerabläufe
## Ansichten und Verhalten
## Zustände und Fehlersituationen
## Berechtigungen
## Bedienbarkeit und Barrierefreiheit
## Akzeptanzkriterien
## Rückverfolgbarkeit zum PRD
## Offene UX-Entscheidungen
## Optionale Text-Wireframes
```

Beschreibe Ansichten und Akzeptanzkriterien in kompakten Tabellen, wenn dies die Zuordnung klarer macht. Unter `Status und Freigabe` stehen zunächst `Entwurf` und `Freigabe ausstehend`.

## Qualitätsprüfung

Prüfe vor der Übergabe:

- Jede PRD-Kernfunktion erscheint in mindestens einem Benutzerablauf und mindestens einem Akzeptanzkriterium.
- Jeder Hauptablauf besitzt einen klaren Start, ein sichtbares Ergebnis und relevante Fehlerwege.
- Navigation und Ansichten enthalten keine unbegründeten Zusatzfunktionen.
- Lade-, Leer-, Fehler-, Erfolgs- und Berechtigungszustände sind berücksichtigt, sofern anwendbar.
- Akzeptanzkriterien beschreiben beobachtbares Verhalten und keine interne Implementierung.
- Barrierefreiheit und Bedienbarkeit sind für die bekannte Zielplattform angemessen berücksichtigt.
- Offene UX-Entscheidungen und Annahmen sind ausdrücklich markiert.
- Das Dokument trifft keine vorgezogenen Architekturentscheidungen.

Dokumentiere diese Prüfung in `STATUS.md` und setze den Status auf `Bereit zur persönlichen Abnahme`.

## Freigabe und Übergang

Nach der Freigabe durch den Entwickler:

1. Halte Freigabestatus und bestätigte UX-Entscheidungen in der Ergebnisdatei fest.
2. Führe den GitHub-Abschluss der Phase durch.
3. Trage als nächste Phase `Technischer Plan` ein.
4. Nenne `docs/product-requirements.md` und `docs/functional-plan.md` als erforderliche freigegebene Eingaben.

Wechsle erst nach erfolgreichem GitHub-Abschluss zur nächsten Phase.
