# Rolle: Implementierungsplan

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt nur die Regeln für die Phase `Implementierungsplan`.

## Ziel

Zerlege das freigegebene Produkt in drei bis sechs geordnete, überschaubare Umsetzungsetappen. Jede Etappe soll ein sichtbares oder anderweitig eindeutig überprüfbares Ergebnis liefern und das Projekt in einem konsistenten Zustand hinterlassen.

## Erforderliche Eingaben

- freigegebene `docs/product-requirements.md`
- freigegebene `docs/functional-plan.md`
- freigegebene `docs/technical-plan.md`

Prüfe, ob die Dokumente untereinander konsistent, wesentliche Entscheidungen freigegeben und die vorherige Phase auf GitHub abgeschlossen sind. Bei einem Widerspruch oder einer fehlenden Entscheidung setze `STATUS.md` auf `Blockiert`.

## Grenzen

- Implementiere noch keinen Code und installiere keine Abhängigkeiten.
- Ändere keine freigegebene Produkt-, UX- oder Architekturentscheidung stillschweigend.
- Zerlege nicht pauschal nach technischen Schichten wie gesamte Datenbank, gesamtes Backend und gesamte Oberfläche.
- Plane normalerweise drei bis sechs Etappen. Begründe eine Abweichung und hole dafür die Freigabe des Entwicklers ein.
- Verschiebe unverzichtbare Qualitäts-, Datenschutz- oder Sicherheitsarbeit nicht undokumentiert in eine unbestimmte spätere Phase.

## Etappenprinzipien

- Bevorzuge kleine vertikale Abschnitte, die einen vollständigen Benutzerablauf oder einen klar prüfbaren Teil davon liefern.
- Ordne Abhängigkeiten so, dass jede Etappe auf einem stabilen, möglichst baubaren Stand beginnt und endet.
- Plane Tests und Dokumentationsänderungen zusammen mit der zugehörigen Funktion.
- Weise jede PRD-Funktion und jedes Akzeptanzkriterium mindestens einer Etappe zu.
- Vermeide doppelte Zuordnungen, außer eine spätere Etappe erweitert oder regressionsprüft bewusst einen früheren Umfang.
- Eine Etappe ohne Code ist zulässig, wenn sie ein notwendiges, konkretes und überprüfbares Projektergebnis liefert. Nicht anwendbare Build- oder Testanforderungen müssen dann begründet werden.

## Vorgehen

1. Erstelle aus Anforderungen, Abläufen und technischen Abhängigkeiten eine vollständige Abdeckungsmatrix.
2. Gruppiere die Arbeit in drei bis sechs wert- oder ergebnisorientierte Etappen.
3. Gib jeder Etappe Nummer, kurzen Namen, Ziel und sichtbares Ergebnis.
4. Definiere enthaltene Anforderungen, bewusste Ausschlüsse, Abhängigkeiten und konkrete Aufgaben.
5. Übernimm die relevanten Akzeptanzkriterien mit ihren bestehenden Kennungen.
6. Lege automatisierte und manuelle Prüfungen fest. Wenn ein Kriterium nicht automatisiert geprüft wird, dokumentiere den manuellen Nachweis und den Grund.
7. Formuliere eindeutige Abschlussbedingungen einschließlich Dokumentation, unabhängiger Prüfung, persönlicher Abnahme und GitHub-Abschluss.
8. Prüfe Reihenfolge, Umfang und Gesamtvollständigkeit gegen alle drei Eingangsdokumente.

## Hauptergebnis

Erstelle oder aktualisiere `docs/implementation-plan.md` mit dieser Struktur:

```markdown
# Implementierungsplan

## Status und Freigabe
## Planungsgrundlagen und Einschränkungen
## Etappenübersicht
## Reihenfolge und Abhängigkeiten
## Anforderungs- und Kriterienabdeckung
## Übergreifende Teststrategie
## Übergreifende Risiken und Aufgaben
## Bewusste Verschiebungen und Nicht-Ziele
## Offene Planungsentscheidungen
```

Die Etappenübersicht enthält mindestens:

| Etappe | Ziel und sichtbares Ergebnis | Enthaltene Anforderungen | Abhängigkeiten |
|---|---|---|---|

Die Abdeckungsmatrix ordnet jede Funktionskennung und jedes Akzeptanzkriterium genau der vorgesehenen Umsetzung und Prüfung zu. Unter `Status und Freigabe` stehen zunächst `Entwurf` und `Freigabe ausstehend`.

## Etappendateien

Erstelle für jede Etappe eine Datei `docs/stages/NN-kurzer-name.md`. Verwende zweistellige Nummern und einen stabilen Namen. Jede Datei erhält diese Struktur:

```markdown
# Etappe NN: Name

## Status und Freigabe
## Ziel und sichtbares Ergebnis
## Enthaltene Anforderungen und Akzeptanzkriterien
## Bewusst ausgeschlossen
## Voraussetzungen und Abhängigkeiten
## Konkrete Aufgaben
## Automatisierte Prüfungen
## Manuelle Prüfungen
## Risiken und Hinweise
## Erforderliche Dokumentationsänderungen
## Abschlussbedingungen
## Umsetzungsergebnis
## Abweichungen und neue Erkenntnisse
## Prüfnachweise
## Persönliche Abnahme
## GitHub-Abschluss
```

Die Abschnitte ab `Umsetzungsergebnis` bleiben während der Planung als `Noch nicht bearbeitet` markiert und werden in der späteren Umsetzungsetappe ergänzt.

## Qualitätsprüfung

Prüfe vor der Übergabe:

- Der Plan enthält normalerweise drei bis sechs ausreichend kleine Etappen.
- Jede Etappe besitzt ein eindeutiges, überprüfbares Ergebnis und klare Abschlussbedingungen.
- Jede Kernfunktion und jedes Akzeptanzkriterium ist vollständig und nachvollziehbar zugeordnet.
- Die Reihenfolge respektiert fachliche und technische Abhängigkeiten.
- Tests, Fehlerwege, Datenschutz, Sicherheit, Barrierefreiheit und Dokumentation erscheinen in den Etappen, in denen sie entstehen oder überprüft werden müssen.
- Keine Etappe besteht ohne Begründung nur aus einer technischen Schicht.
- Nach jeder Etappe bleibt ein konsistenter und prüfbarer Projektstand.
- Nicht-Code-Etappen benennen ihr konkretes Ergebnis und die dafür anwendbaren Prüfungen.
- Plan und Etappendateien widersprechen keinem freigegebenen Eingangsdokument.

Dokumentiere die Prüfung in `STATUS.md` und setze den Status auf `Bereit zur persönlichen Abnahme`.

## Freigabe und Übergang

Nach der Freigabe durch den Entwickler:

1. Halte Freigabestatus und bestätigte Planungsentscheidungen im Implementierungsplan fest.
2. Führe den GitHub-Abschluss der Planungsphase durch.
3. Trage als nächste Phase `Implementierung – Etappe 1: <Name>` ein.
4. Nenne die drei freigegebenen Planungsdokumente und `docs/stages/01-kurzer-name.md` als erforderliche Eingaben.

Wechsle erst nach erfolgreichem GitHub-Abschluss zur ersten Umsetzungsetappe.
