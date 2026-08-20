# Etappe 04: Robuste Übergabe

## Status und Freigabe

- Status: Geplant
- Freigabe: ausstehend

## Ziel und sichtbares Ergebnis

Die vollständige Aquariumerfahrung bleibt bei normalen und abgebrochenen Eingaben, Größenwechseln und längerer Beobachtung verständlich und bedienbar. Eine unabhängige Prüfung liefert einen nachvollziehbaren Gesamtnachweis.

## Enthaltene Anforderungen und Akzeptanzkriterien

- Regressionsprüfung für F-01 bis F-05 und AC-F01-01 bis AC-F05-02
- Qualitätsanforderungen Q-01 bis Q-07 und Erfolgskriterien E-01 bis E-06

## Bewusst ausgeschlossen

Neue Produktfunktionen, Browserunterstützung außerhalb aktueller stabiler Evergreen-Versionen und die GitHub-Pages-Aktivierung; diese erfolgt nach dieser Etappe ausschließlich in der Release-Phase.

## Voraussetzungen und Abhängigkeiten

Abgeschlossene Etappen 01 bis 03 und deren unabhängige Prüfberichte.

## Konkrete Aufgaben

- Fallback bei fehlendem Canvas oder Pointer Events sowie sichere Bereinigung bei Fokusverlust, `pointercancel` und Größenwechsel vervollständigen.
- Bewegungs- und Effektdichte auf kleinen und großen Ansichten kontrollieren; nötige Fehlerkorrekturen innerhalb des freigegebenen Umfangs vornehmen.
- Statische Datenschutz-, Sicherheits- und Abhängigkeitsprüfung durchführen.
- Vollständigen browserbasierten Smoke-Test mit Touch-Viewport und Desktop dokumentieren und die Umsetzung an die unabhängige Prüfphase übergeben.

## Automatisierte Prüfungen

`git diff --check`; statische Suche nach externen URLs, Speicherzugriffen, Geheimnissen und unerwünschten Abhängigkeiten; vorhandene Syntaxprüfung. Vollautomatisierte visuelle oder hardwareübergreifende Tests werden nicht vorausgesetzt, weil keine Testtoolchain installiert werden soll.

## Manuelle Prüfungen

Alle fünf Abläufe A-01 bis A-05 auf Desktop und kleinem Touch-Viewport prüfen, inklusive Tab-/Enter-Buttonbedienung, Zoomlesbarkeit, Fütterungswiederholung, Fischlimit, abgebrochener Geste, Größenwechsel und längerer Beobachtung. Vor Release zusätzlich die zugesagten aktuellen stabilen Browser Safari, Chrome, Edge und Firefox prüfen.

## Risiken und Hinweise

Browserübergreifende visuelle Unterschiede dürfen keine Akzeptanzkriterien beeinträchtigen. Die unabhängige Prüfung bleibt vom Implementierungsagenten getrennt.

## Erforderliche Dokumentationsänderungen

Vollständige Prüfnachweise, bekannte Einschränkungen, Übergabe an `Prüfung – Etappe 04` und `STATUS.md` aktualisieren.

## Abschlussbedingungen

Alle Kriterien, Qualitäts- und Erfolgskriterien sind ohne Umfangserweiterung nachgewiesen; keine Datenschutz-, Sicherheits- oder Bedienbarkeitsprobleme bleiben offen; die unabhängige Prüfung ist bestanden und der Entwickler hat persönlich abgenommen; erst danach erfolgt der GitHub-Abschluss.

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
