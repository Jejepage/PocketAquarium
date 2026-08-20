# Etappe 02: Szenengesten

## Status und Freigabe

- Status: Geplant
- Freigabe: ausstehend

## Ziel und sichtbares Ergebnis

Kurze Aktivierung erzeugt sichtbare Neugier, Ziehen sichtbares Ausweichen und doppelte Aktivierung fügt bis zum Limit von sechs einen sichtbaren zufälligen Fisch hinzu.

## Enthaltene Anforderungen und Akzeptanzkriterien

- F-03
- AC-F03-01, AC-F03-02, AC-F03-03 und AC-F03-04

## Bewusst ausgeschlossen

Fütterung und alle nicht in V1 enthaltenen Funktionen; keine neue Tastaturpflicht für Canvas-Gesten.

## Voraussetzungen und Abhängigkeiten

Abgeschlossene Etappe 01 mit stabiler Fischsimulation.

## Konkrete Aufgaben

- Pointer Events, Koordinatenumrechnung, Capture sowie Bereinigung bei Abbruch implementieren.
- Konservative Schwellen für kurze, doppelte und ziehende Aktivierung festlegen.
- Ziel- und Verhaltenswechsel für Neugier und Ausweichen ergänzen.
- Zufälligen Fisch nur unterhalb des Limits erzeugen und das Erreichen des Limits verständlich folgenlos behandeln.

## Automatisierte Prüfungen

Statische Prüfung auf einheitliche Pointer-Event-Behandlung und Begrenzung auf sechs Fische; lokal verfügbare Syntaxprüfung. Gestenerkennung wird wegen physischer Eingaben zusätzlich manuell nachgewiesen.

## Manuelle Prüfungen

Auf Touch und mit Maus/Trackpad jeweils kurze Aktivierung, Ziehen und doppelte Aktivierung ausführen; neue Fische bis sechs erzeugen, dann erneut doppelt aktivieren. `pointercancel`, eine abgebrochene Geste und rasche Wiederholungen prüfen.

## Risiken und Hinweise

Doppeltaktivierung darf nicht zugleich eine verwirrende anhaltende Neugier erzeugen. Schwellenwerte sind als getestete Implementierungsdetails zu dokumentieren.

## Erforderliche Dokumentationsänderungen

Etappenstatus, Schwellenwertbegründung, Prüfnachweise und `STATUS.md` aktualisieren.

## Abschlussbedingungen

Alle vier Kriterien sind mit Touch sowie Maus/Trackpad nachgewiesen, die Szene bleibt nach Abbruch bedienbar, die unabhängige Prüfung ist bestanden und der Entwickler hat persönlich abgenommen; erst danach erfolgt der GitHub-Abschluss.

## Umsetzungsergebnis

Noch nicht bearbeitet.

## Abweichungen und neue Erkenntnisse

Noch nicht bearbeitet.

## Prüfnachweise

Noch nicht bearbeitet.

## Persönliche Abnahme

Noch nicht bearbeitet.

## GitHub-Abschluss

Noch nicht bearbeitet.
