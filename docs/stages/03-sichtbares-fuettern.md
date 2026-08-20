# Etappe 03: Sichtbares Füttern

## Status und Freigabe

- Status: Geplant
- Freigabe: ausstehend

## Ziel und sichtbares Ergebnis

Die dauerhaft sichtbare Schaltfläche **Füttern** kann per Zeiger und Tastatur aktiviert werden. Sichtbares Futter sinkt; mindestens ein Fisch schwimmt hin und die Futtermenge wird sichtbar weniger.

## Enthaltene Anforderungen und Akzeptanzkriterien

- F-04
- AC-F04-01 und AC-F04-02

## Bewusst ausgeschlossen

Mehrere gleichzeitige Fütterungen, Pflege- oder Inventarmechaniken, Audio sowie dauerhafte Speicherung.

## Voraussetzungen und Abhängigkeiten

Abgeschlossene Etappen 01 und 02 mit stabiler Szene, Fischzuständen und Eingabebehandlung.

## Konkrete Aufgaben

- Beschrifteten nativen Button mit sichtbarem Fokus, sinnvoller Position und programmatischem Namen fertigstellen.
- Futterpartikel und exklusiven Fütterungszustand implementieren; den Button bis zum Ende der sichtbaren Reaktion deaktivieren.
- Mindestens einen geeigneten Fisch auf Futter zielen und beim Erreichen Partikel sichtbar reduzieren lassen.
- Vorrang der Fütterung vor Neugier und die Rückkehr eines geflohenen Fisches zum Futterziel wie geplant behandeln.

## Automatisierte Prüfungen

Statische Prüfung auf nativen Button, sichtbare Textbeschriftung, fehlende externen Ressourcen und die Sperre gegen paralleles Futter. Soweit ohne neue Abhängigkeit verfügbar: HTML-/JavaScript-Syntaxprüfung.

## Manuelle Prüfungen

Button mit Maus/Touch aktivieren und per Tabulator fokussieren sowie per Tastatur auslösen. Futter, Zielbewegung und sichtbare Verringerung beobachten; erneutes Füttern während der Reaktion, Szenengesten während Fütterung und erneutes Füttern nach Abschluss prüfen.

## Risiken und Hinweise

Der Button darf Canvas-Gesten nicht verdecken; Futter und Fischbewegung müssen sich deutlich von Neugier unterscheiden.

## Erforderliche Dokumentationsänderungen

Etappenstatus, Zugänglichkeits- und Prüfnachweise sowie `STATUS.md` aktualisieren.

## Abschlussbedingungen

Beide Kriterien sind auf Touch und Desktop nachgewiesen, Fokus und Bezeichnung sind sichtbar und sinnvoll, konkurrierendes Futter ist verhindert, die unabhängige Prüfung ist bestanden und der Entwickler hat persönlich abgenommen; erst danach erfolgt der GitHub-Abschluss.

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
